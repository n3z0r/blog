---
date: '2026-02-23T17:43:16Z'
draft: true
title: 'Open Project VM Installation'
---

# Open Project local env setup

## Create new vm
Install Ubuntu 22.04 server 2cpu/4GB ram/40GB space
Take Snapshot-0

## Installation
Find app release package https://packager.io/gh/opf/openproject/builds/12998/install/ubuntu-22.04
We are on 15.1.0

### Install the app
wget -qO- https://dl.packager.io/srv/opf/openproject/key | sudo apt-key add - [This changes to the next line because apt-key is deprecated]
wget -qO- https://dl.packager.io/srv/opf/openproject/key | sudo tee /etc/apt/trusted.gpg.d/
sudo wget -O /etc/apt/sources.list.d/openproject.list \
  https://dl.packager.io/srv/opf/openproject/release/15.1/installer/ubuntu/22.04.repo
sudo apt-get update
sudo apt-get install openproject

Take Snapshot-1

### Configure the app

sudo openproject reconfigure
Selected edition: default
postgress: install
Server: Install apache2
hostname: 192.168.1.60
prefix:op
TLS: no
API KEY: copy this value somewhere safe
svn: skip
git: skip
memcached: install
admin email: [EMAIL_ADDRESS]
language: English

Take snapshot-2

### Login and set password
Username: admin
Password: set your own password
