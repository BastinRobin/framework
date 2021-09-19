## Robinhood µservice Framework 
Robinhood a.k.a (rhood) is a hybrid microservice framework which has been build to simplify creation and deploying of microservices with ease. Currently `rhood` supports `Node` for service generation but will not be same in couple of months. We are planning to create language support for `Python`, `Go`, `PHP` services as first stable release. 

## Why Robinhood?

- Defacto support for service deployment inside docker containers.
- Faster response > Code craft.
- Auto generated swagger documentation for services.
- Auto generate tests for each services.
- Scalable design patterns for larger applications.
- Easy integeration with 3rd party services or marketplaces.
- Service status monitoring.
- Preconfigured Nginx Reverse Proxy
- CLI based service creation.


## Framework Structure

        rhood-core
        |--- run.js
        |--- assets/
        |--- scr/
            |--- service/ # Basic skeleton
                |--- service.js
                |--- package.json
                |--- src/
                    |--- app.js
                    |--- config/
                        |--- index.js
                    |--- models/
                        |--- sample_model.js
                    |--- Dockerfile
                    |--- node_modules/


## Installation

    npx install robinhood

## Usage
    > rhood init (inside folder)
    > rhood create service_name --type=js
    > rhood list 
    > rhood attach service_name > service_exists
    > rhood test
    > rhood serve

## Working principles
1. `mkdir ~/project_name`
2. `cd ~/project_name`
3. Execute `> rhood init` which initializes a configuration file with Application name, descriptions, metadata.
4. After application initialization complete now we are good to create our first service.
5. Execture `> rhood create service_name(users)`
6. Prompt with following: `> Language {*Node, PHP, Python}: Node`
7. Prompt with version: `> Version {beta, dev, v1, v2, etc}: beta`
8. Prompt with base endpoint: `> Select Endpoint: /api/beta/users`.
9. Prompt with ModelName: `> User(recommended)`
10. How many fields: `> 5`
    - Field 1 Name: `>id`
    - Field type: `int`
    - Field 2 Name: `first_name`
    - Field type: `varchar`
    - Field 3 Name: `last_name`
    - Field type: `varchar`
    - Field 4 Name: `email`
    - Field type: `varchar`
    - Field 5 Name: `created_at`
    - Field type: `Timestamp(now)`
    - Want to add more ? `> No`
    - Any constraint ? `> id`
    - Constrain type? `PK`
    - Any constraint ? N
    - Any Relationship ? `> id`
      - Pick table: `> profile`
      - Type: `user_id`

11. Now a directory is created inside current directory with the name `users` which consists of `service` skeleton and scr files such as `app.js, models, config` etc.

        |--- project_name
            |--- docker-compose.yml 
            |--- default.conf
            |--- settings.json
            |--- status.html
            |--- users/ # user µ-service
                |--- service.js
                |--- package.json
                |--- src/
                    |--- app.js
                    |--- config/
                        |--- index.js
                    |--- models/
                        |--- sample_model.js
                    |--- Dockerfile
                    |--- node_modules/

            |--- profile/ # profile µ-service
                |--- service.js
                |--- package.json
                |--- src/
                    |--- app.js
                    |--- config/
                        |--- index.js
                    |--- models/
                        |--- sample_model.js
                    |--- Dockerfile
                    |--- node_modules/