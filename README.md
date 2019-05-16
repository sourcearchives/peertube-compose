# Peertube setup with Ansible and Docker-Compose

This repo lets you easily setup a Peertube server based on docker-compose.

There is also a migration script to migrate from the
[default Peertube setup](https://github.com/Chocobozzz/PeerTube/blob/develop/support/doc/production.md)
to this setup. Use it at your own risk, and make sure to test and backup
before doing this migration.

You can contact me on the Fediverse about this project:
[https://radical.town/@felix](https://radical.town/@felix).

## Features

- automatic Let's Encrypt certificate handling via Traefik
- file caching with nginx (to limit backend access and Peertube CPU usage)
- email sending works out of the box

## Setup

Clone the repo onto your local machine.

Copy `inventory.example` to `inventory`, and configure the hosts you want to work with.

Install Python and Ansible on your local machine:

    apt install python
    pip2 install ansible

Run the playbook:

    ansible-playbook --become peertube.yml

The first time you run it, Ansible will output the root password.

Note: If you use this for an existing Peertube instance, make sure the file
`passwords/*your-server*/postgres` exists and contains the correct password. Otherwise
Ansible will change the password in Peertube, and it won't be able to connect to the database.
