# Symfony Docker

A [Docker](https://www.docker.com/)-based installer and runtime for the [Symfony](https://symfony.com) web framework,
with [FrankenPHP](https://frankenphp.dev) and [Caddy](https://caddyserver.com/) inside!

## Getting Started

### Developpment
1. If not already done, [install Docker Compose](https://docs.docker.com/compose/install/) (v2.10+)
2. Run `docker compose build --pull --no-cache` to build fresh image.
3. Run `docker compose up --wait` to set up and start project.
4. Run `docker compose down --remove-orphans` to stop the Docker containers.

#### Fix permissions on Linux (if needed)
```sh
docker compose run --rm php chown -R $(id -u):$(id -g) .
```

#### Install additionnal packages
```sh
docker compose exec php composer require --dev symfony/profiler-pack
```

### Production

#### Build Fresh Images for Production Use
```sh
docker compose -f compose.yaml -f compose.prod.yaml build --pull --no-cache
```
#### Start container in production mode
```sh
docker compose -f compose.yaml -f compose.prod.yaml up --wait
```

## Docs

1. [Options available](docs/options.md)
2. [Using Symfony Docker with an existing project](docs/existing-project.md)
3. [Support for extra services](docs/extra-services.md)
4. [Deploying in production](docs/production.md)
5. [Debugging with Xdebug](docs/xdebug.md)
6. [TLS Certificates](docs/tls.md)
7. [Using MySQL instead of PostgreSQL](docs/mysql.md)
8. [Using Alpine Linux instead of Debian](docs/alpine.md)
9. [Using a Makefile](docs/makefile.md)
10. [Updating the template](docs/updating.md)
11. [Troubleshooting](docs/troubleshooting.md)
12. [Using AI Coding Agents](docs/agents.md)
