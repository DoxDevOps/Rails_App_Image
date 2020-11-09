Setting up Contenarized Rails App with MySQL database
_____________________________________________________________________________________________________________________

By						      Zione Mwakanema


Prerequisites

1. Basic command line knowledge
2. Text editor
3. Install Docker and docker-compose

Getting the image up

*** Assuming that you are in the dist dir, follow these steps to get your App up-and-running!

1. Generate the Rails skeleton using docker-compose run:
```bash
docker-compose run --no-deps web rails new . --force --database=mysql
```

2. If you are running Docker on Linux, the files created are owned by root. If this is the case, change the ownership of the new files. If you are running Docker on Mac or Windows, you should already have ownership of all files.
```bash
sudo chown -R $USER:$USER .
```


3. Now that you’ve got a new Gemfile, you need to build the image again. (This, and changes to the Gemfile or the Dockerfile, should be the only times you’ll need to rebuild.)
```bash
docker-compose build
```
4. By default, Rails expects a database to be running on localhost - so you need to point it at the db container instead. You also need to change the database and username to align with the defaults set by the MySQL image (see image environment var in docker-compose.yml). Replace the contents of config/database.yml with the following:

```bash
default: &default
  adapter: postgresql
  encoding: unicode
  host: db
  username: postgres
  password: password
  pool: 5

development:
  <<: *default
  database: myapp_development


test:
  <<: *default
  database: myapp_test
```

5. Get the image up with:
```bash 
docker-compose up -d
```

6. Finally, you need to create the database.
```bash
docker-compose run web rake db:create
```




