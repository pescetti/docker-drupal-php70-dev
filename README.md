Dockerised Drupal 8 development environment using PHP 7.0 on Ubuntu 14.04 with HTTP/2. This image is the development companion to the [docker-drupal-php70](https://github.com/andrewholgate/docker-drupal-php70) project.

# Included Tools

## Debugging Tools

- [XDebug](http://www.xdebug.org/) - PHP debugging and profiling.

## Front-end Tools

- [Wraith](https://github.com/BBC-News/wraith) - for visual regression testing.
- [PhantomJS](http://phantomjs.org/) - for smoke tests.

## PHP Documentation Tools

- [DoxyGen](http://www.doxygen.org) - generate documentation from annotated PHP code. It is used to generate XML which is then interpreted by Sphinx.
- [Sphinx](http://sphinx-doc.org/) - generate beautiful [Read The Docs](http://docs.readthedocs.org/en/latest/) format using [Breathe](https://breathe.readthedocs.org/) as a bridge to DoxyGen XML output.

# Other
- [NodeJS](https://nodejs.org/) - Javascript runtime.
- Java Runtime Environment (JRE) - project dev tools like [sitespeed.io](http://www.sitespeed.io/) need this.

# Installation

## Create Presistant Database data-only container

```bash
# Build database image based off MySQL 5.6
sudo docker run -d --name mysql-drupal-php70-dev mysql:5.6 --entrypoint /bin/echo MySQL data-only container for Drupal Dev MySQL
```

## Build Project using Docker Compose

```bash
# Customise docker-compose.yml configurations for environment.
cp docker-compose.yml.dist docker-compose.yml
vim docker-compose.yml

# Build docker containers using Docker Composer.
sudo docker-compose build
sudo docker-compose up -d
```

## Host Access

From the host server, add the web container IP address to the hosts file.

```bash
# Add IP address to hosts file.
./hosts.sh
```

## Logging into Web Front-end

```bash
# Using the container name of the web frontend.
sudo docker exec -it dockerdrupalphp70dev_drupalphp70devweb_1 su - ubuntu
```

# TODO

- [XHProf](http://pecl.php.net/package/xhprof) - function-level hierarchical profiler.
