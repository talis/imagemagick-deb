# imagemagick-deb

## Requirements

* Docker
* Docker Compose (v 1.9 or greater)

## Usage

pick your distro (currently only trusty) and then ```docker-compose run imagemagick```, this will place a debian package in the out directory

## Newer imagemagick?

New imagemagick release? Simply ```docker-compose build && docker-compose run imagemagick```
