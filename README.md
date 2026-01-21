# Symfony Docker

A [Docker](https://www.docker.com/)-based installer and runtime for the [Symfony](https://symfony.com) web framework,
with [FrankenPHP](https://frankenphp.dev) and [Caddy](https://caddyserver.com/) inside!

## Getting Started

### Developpment
1. If not already done, [install Docker Compose](https://docs.docker.com/compose/install/) (v2.10+)
2. Run `docker compose build --pull --no-cache` to build fresh images
3. Run `docker compose up --wait` to set up and start a fresh Symfony project
4. Open `https://localhost` in your favorite web browser and [accept the auto-generated TLS certificate](https://stackoverflow.com/a/15076602/1352334)
5. Run `docker compose down --remove-orphans` to stop the Docker containers.

#### Fix permissions on Linux
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
#### Start container
```sh
SERVER_NAME=your-domain-name.example.com \
APP_SECRET=ChangeMe \
CADDY_MERCURE_JWT_SECRET=ChangeThisMercureHubJWTSecretKey \
docker compose -f compose.yaml -f compose.prod.yaml up --wait
```

## Docs

1. [Options available](docs/options.md)
2. [Support for extra services](docs/extra-services.md)
3. [Deploying in production](docs/production.md)
4. [Debugging with Xdebug](docs/xdebug.md)
5. [TLS Certificates](docs/tls.md)
6. [Using MySQL instead of PostgreSQL](docs/mysql.md)
7. [Using a Makefile](docs/makefile.md)
8. [Updating the template](docs/updating.md)
9. [Troubleshooting](docs/troubleshooting.md)
