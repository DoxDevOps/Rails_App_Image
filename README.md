Setting up PoC Platform
_____________________________________________________________________________________________________________________

By						      Zione Mwakanema


Prerequisites

1. Basic command line knowledge
2. Text editor

Resources

https://docs.docker.com/get-started/

Getting started

1. Ensure Docker is installed (docker --version)

2. Ensure docker-compose is installed (docker-compose -v)

Other information

1. General info that is not necessarily commands are specified by ***

Steps to install platform

1. mkdir poc_backend
2. cd poc_backend
3. *** From https://github.com/HISMalawi/BHT-EMR-API, get the Gemfile into poc_backend dir
4. touch Gemfile.lock
5. chmod a+w Gemfile.lock
6. *** get Dockerfile from dist folder to poc_backend
7. *** get the docker-compose.yml from the dist folder to poc_backend
8. docker-compose run app rails new . --force --database=mysql --skip-bundle
