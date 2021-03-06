# Ansible Role: Composer

[![Build Status](https://travis-ci.org/yfix/ansible-role-composer.svg?branch=master)](https://travis-ci.org/yfix/ansible-role-composer)

Installs Composer, the PHP Dependency Manager, on any Linux or UNIX system.

## Requirements

`php` (version 5.4+) should be installed and working.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    composer_path: /usr/local/bin/composer

The path where composer will be installed and available to your system. Should be in your user's `$PATH` so you can run commands simply with `composer` instead of the full path.

    composer_keep_updated: false

Set this to `true` to update Composer to the latest release every time the playbook is run.

    composer_home_path: '~/.composer'

The COMPOSER_HOME path; this is the directory where global packages will be installed.

    composer_global_packages: {}

A list of packages to install globally (using `composer global require`). If you want to install any packages globally, add a list item with a dictionary with the `name` of the package and a `release`, e.g. `- { name: phpunit/phpunit, release: "4.7.*" }`. The 'release' is optional, and defaults to `@stable`.

    composer_add_to_path: true

If `true`, and if there are any configured `composer_global_packages`, the `vendor/bin` directory inside `composer_home_path` will be added to the system's default `$PATH` (for all users).

## Dependencies

None (but make sure you've installed PHP; the `yfix.php` role is recommended).

## Example Playbook

    - hosts: servers
      roles:
        - { role: yfix.composer }

After the playbook runs, `composer` will be placed in `/usr/local/bin/composer` (this location is configurable), and will be accessible via normal system accounts.
