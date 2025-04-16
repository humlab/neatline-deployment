# Humlab deployment of Neatline

## WARNING
This really just install Omeka-s in it's current state, not Neatline.

## Installation

1. Copy .env-example to .env and fill it out
1. Copy ./mounts/neatline/database-example.ini to ./mounts/neatline/database.ini and fill it out. You need to enter the same password here as in the .env.
1. Run docker compose up -d.
1. Site is now available at http://localhost:8080, or whatever port you specified in docker-compose.yml.
