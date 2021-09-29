# docker-hackmyresume-web
[![Docker pull](https://img.shields.io/docker/pulls/nouchka/hackmyresume-web)](https://hub.docker.com/r/nouchka/hackmyresume-web/)
[![Docker stars](https://img.shields.io/docker/stars/nouchka/hackmyresume-web)](https://hub.docker.com/r/nouchka/hackmyresume-web/)
[![Build Status](https://gitlab.com/japromis/docker-hackmyresume-web/badges/master/pipeline.svg)](https://gitlab.com/japromis/docker-hackmyresume-web/pipelines)
[![Docker size](https://img.shields.io/docker/image-size/nouchka/hackmyresume-web/latest)](https://hub.docker.com/r/nouchka/hackmyresume-web/)

Docker image to build personal website with resume (Ex. https://japromis.katagena.com/)

# Versions

Version follows npm package version

* 1.0 (latest) (npm package version >=1.3.0 <2)

# Image

This image extends [docker-hackmyresume](https://github.com/nouchka/docker-hackmyresume) providing a nginx server.

The entrypoint of the image:
* download the json file
* generate html file using parent image
* launch nginx

# Use

Use from command line (port 8005):

	docker run -p 8005:80 \
		-e 'OUTPUT_TEMPLATE=kendall' \
		-e 'PHONE=+33602030405' \
		-e 'EMAIL=docker@katagena.com' \
		-e 'ADDRESS=25 Rue Delphin Loche' \
		-e 'RESUME_JSON_URL=https://raw.githubusercontent.com/nouchka/japromis.katagena.com/master/resume.json' \
		nouchka/hackmyresume-web
or use with docker compose (port 8005):

	docker-compose up -d
Environment variables:

	# specify basic template or https://jsonresume.org/themes/ template (ex. kendall in docker-compose.yml, default: modern)
	OUTPUT_TEMPLATE=kendall
	# will replace ###PHONE### by this value
	PHONE=+33602030405
	# will replace ###EMAIL### by this value
	EMAIL=docker@katagena.com
	# will replace ###ADDRESS### by this value
	ADDRESS=25 Rue Delphin Loche
	# specify url to json file
	RESUME_JSON_URL=https://raw.githubusercontent.com/nouchka/japromis.katagena.com/master/resume.json

# Todo

* Migrate docker-compose file format to version 2
* Add parameters to define directory
* CI check contains of index.html

# Donate

Bitcoin Address: 15NVMBpZJTvkefwfsMAFA3YhyiJ5D2zd3R
