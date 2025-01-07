# LIVPARK - APP API

## Requirement:

- OS: Linux (Ubuntu, CentOS, ArchLinux,...), MacOS.
- Software: Docker with Docker compose.

## Installation:
1. Clone source code to your machine.
2. Running the command below to install dependencies:
    ```
    docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php83-composer:latest \
    composer install --ignore-platform-reqs
    ```
3. Copy .env from .env.example.
   If you want to change env vars, edit the .env file. Compare it with docker-compose.yml to make sure all env vars was match.
4. Start services by running the following command:
```
./vendor/bin/sail up -d --build
```
5. After services were built, generate the key for the app by command:
```
./vendor/bin/sail artisan key:generate
```
6. Migration the database by command:
```
./vendor/bin/sail artisan migrate
```
7. Build ReactJS with InertiaJS:
```
./vendor/bin/sail exec -it laravel.test npm install
./vendor/bin/sail exec -it laravel.test npm run dev
```
