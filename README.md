# Ansible Role: Passenger

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-passenger.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-passenger)

Installs Passenger (with Nginx) on RedHat/CentOS (soon) or Debian/Ubuntu linux servers.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    passenger_server_name: www.example.com

The server name (used in the Nginx virtual host configuration).

    passenger_app_root: /opt/example/public

The `passenger_root` for your application (e.g. the `public` folder in a rails app).

    passenger_app_env: production

The app environment passenger will load.

    passenger_root: /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini
    passenger_ruby: /usr/bin/ruby

Values for passenger configuration directives inside `nginx.conf`. These defaults should generally work correctly, but if you build `ruby` on its own (as an example), the path to ruby may be different.

    nginx_worker_processes: "{{ ansible_processor_vcpus | default(ansible_processor_count) }}"
    nginx_worker_connections: "768"
    nginx_keepalive_timeout: "65"
    nginx_remove_default_vhost: true

Nginx directives.

## Dependencies

None.

## Example Playbook

    - hosts: server
      roles:
        - { role: geerlingguy.passenger }

## License

MIT / BSD

## Author Information

This role was created in 2015 by [Jeff Geerling](http://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
