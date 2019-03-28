# Upgrade Guide

- [Basic](#basic)

## Basic

- When you got a new version of Botble Core from Codecanyon. You just need to do below steps to upgrade it.
    * Extract `core.zip` and extract `platform.zip` then override folder `platform`.
    * Run `composer update` to update core.
    * Update assets: `php artisan vendor:publish --tag=public --force`
    * Update database
    ```bash
      php artisan migrate
    ```
    * To make sure all config and cache is clear, please run below commands:
    ```bash
     php artisan config:clear
     php artisan cache:clear
     php artisan route:clear
     php artisan view:clear
    ```
