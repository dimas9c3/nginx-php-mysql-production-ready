## nginx-production-ready

This is example of how to configure nginx mysql php using docker

## Features

- nginx
- php 7.4 fpm
- Mysql
- auto renewal let'sencypt ssl

## Installation Guide

- cp .env.example .env
- docker-compose up -d
- if you want to configure ssl check bin/nginx/Dockerfile instruction and configure nginx conf at /config/nginx/
