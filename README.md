# README

## Versions
- Ruby Version: ruby-2.5.1
- Rails Version: Rails 5.1.6
- PostgreSQL Version: 9.5

## Setup Instructions

* Install ruby using RVM, use ruby-2.5.1
* Install Dependencies: `bundle install --without production`
* Configure your DB in config/database.yml, copy config/database.yml.example
* Create database: `rails db:create`
* Run Migrations: `rails db:migrate`
* install imagemagick
* Start Redis server process.
* To start sidekiq: `bundle exec sidekiq -e development -q default -q mailers -d -L tmp/sidekiq.log` (In development)

## Docker Instructions

* Install docker and docker-compose
* Run: `docker-compose up`

If you need to rebuild, run this before `docker-compose up`
```
docker system prune
docker-compose build --no-cache
```

## Developer Instructions
Developers can quickly get started by setting up the dev environment using the instructions above. The database is seeded with the following admin account. 
```
User: Admin
Email: admin@circuitverse.org
Password: password
```

## Production Specific Instructions

```
bundle install --without development test
RAILS_ENV=production bundle exec rake assets:precompile
bundle exec sidekiq -e production -q default -q mailers -d -L tmp/sidekiq.log` (In production)
```

fake
