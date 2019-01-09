# Prepare local environment

1. Install **docker, ansible, make**.
  * For Ubuntu: ```sudo bash bash/install-ubuntu.sh```.
  * For Linux Mint: ```sudo bash bash/install-mint.sh```.
2. Run ```sudo usermod -a -G docker $USER```.
You need **reboot** system, after running the command.

# Usage guide

  * You can run the project using ```make local-up``` command.
  * You can check docker container status using ```make docker-status``` command.
  * You can connect to workspace using ```make local-bash``` command.
  * You can run migrations using ```make local-october-up``` command.
> **app/vendor** folder is in .gitignore, so after cloning project you need to run ```local-composer-install``` command.

### First start

  * Clone repo with project.
  * Run ```make local-first-start``` command.
  * Connect to workspace. Run ```make local-bash``` command.
  * Run ```nmp i``` and ```npm run watch``` commands.

### Usual developer day guide

  * Run ```make local-up``` command.
  * Connect to workspace. Run ```make local-bash``` command.
  * Run ```npm run watch``` commands.
  * You start to do the task.
  
 >  If you get **database error**, after updating the project, then you can update your database (```make import-mysql-db```) or apply migrations (```make local-october-up```).
 
 >  If you get **non-database error**, after updating the project, then you can try run ```make local-composer-install``` command.

### Useful links

  * Beanstalkd console - http://localhost:2080/
  * PHPMyAdmin - http://localhost:8080/
  * Maildev - http://localhost:1080/
  * Kibana - http://localhost:5601/
  * Grafana - http://localhost:3000/
  * Portainer - http://localhost:9010/
  * Netdata - http://localhost:19999/
  * Metabase - http://localhost:3030/
  * PHPRedisAdmin - http://localhost:9987/
  * Docker web UI - http://localhost:8754/

# Available commands (local environment)

### local-init-env

Creates local environment files from templates.
```bash
make local-init-env
```

### local-up

Creates local environment files from templates. Starts docker machines.
```bash
make local-up
```

### local-restart

Creates local environment files from templates. Restarts docker machines.
```bash
make local-restart
```

### local-stop

Stops docker machines.
```bash
make local-stop
```

### local-rebuild

Rebuild and restart docker machines.
```bash
make local-rebuild
```

### local-bash

Connect to workspace with laradock user
```bash
make local-bash
```

### local-composer-install

Connect to workspace with laradock user and run composer install
```bash
make local-composer-install
```

### local-october-up

Connect to workspace with laradock user and apply migrations
```bash
make local-october-up
```

### local-npm-prod

Connect to workspace with laradock user and run ```npm run prod```
```bash
make local-npm-prod
```

### local-sphinx-rotate-all

Connect to Sphinx search container and run ```indexer --rotate --all```
```bash
make local-sphinx-rotate-all
```

# Database

### import-mysql-db

  * Download db.zip file from bitbucket.
  * Get dump db.sql file from temp/db.zip archive.
  * Import mysql dump file.
```bash
make import-mysql-db [src=bitbucket]
```

### export-mysql-db

  * Export mysql database in db.sql file.
  * Create temp/db.zip archive with db.sql file.
  * Upload db.zip archive to bitbucket.
```bash
make export-mysql-db [src=bitbucket]
```

# Content files

### import-content

  * Download content.zip file from bitbucket.
  * Get content files from temp/content.zip archive.
  * Copy content folders: meta, content.
```bash
make import-content [src=bitbucket]
```

### export-content

  * Copy content folders: meta, content.
  * Create temp/content.zip archive with content files.
  * Upload content.zip archive to bitbucket.
```bash
make export-content [src=bitbucket]
```

# Image files

### import-images

  * Download images.zip file from bitbucket.
  * Get images files from temp/images.zip archive.
  * Copy images folders: upload, media.
```bash
make import-images [src=bitbucket]
```

### export-images

  * Copy images folders: upload, media.
  * Create temp/images.zip archive with images files.
  * Upload images.zip archive to bitbucket.
```bash
make export-images [src=bitbucket]
```

# Full import/export

### import-full

Starts import mysql database, content files, images.
```bash
make import-full
```

### export-full

Starts export mysql database, content files, images.
```bash
make export-full
```

# Available commands (staging environment)

### staging-create

Creates droplet machine.
```bash
make staging-create [prefix=master]
```

### staging-provisioning

Does server default setup.
```bash
make staging-provisioning [prefix=master]
```

### staging-up

Connect to staging server. Creates staging environment files from templates. Starts docker machines.
```bash
make staging-up [prefix=master]
```

### staging-pull

Connect to staging server and update project
```bash
make staging-pull [prefix=master] [version=master]
```

### staging-restart

Creates staging environment files from templates. Restarts docker machines.
```bash
make staging-restart [prefix=master]
```

### staging-stop

Stops docker machines on staging server.
```bash
make staging-stop [prefix=master]
```

### staging-rebuild

Rebuild and restart docker machines on staging server.
```bash
make staging-rebuild [prefix=master]
```

### staging-import-mysql-db

  * Connect to staging droplet.
  * Download db.zip file from bitbucket.
  * Get dump db.sql file from temp/db.zip archive.
  * Import mysql dump file.
```bash
make staging-import-mysql-db [prefix=master] [src=bitbucket]
```

### staging-export-mysql-db

  * Connect to staging droplet.
  * Export mysql database in db.sql file.
  * Create temp/db.zip archive with db.sql file.
  * Upload db.zip archive to bitbucket.
```bash
make staging-export-mysql-db [prefix=master] [src=bitbucket]
```

### staging-import-content

  * Connect to staging droplet.
  * Download content.zip file from bitbucket.
  * Get content files from temp/content.zip archive.
  * Copy content folders: meta, content.
```bash
make staging-import-content [prefix=master] [src=bitbucket]
```

### staging-export-content

  * Connect to staging droplet.
  * Copy content folders: meta, content.
  * Create temp/content.zip archive with content files.
  * Upload content.zip archive to bitbucket.
```bash
make staging-export-content [prefix=master] [src=bitbucket]
```

### staging-import-images

  * Connect to staging droplet.
  * Download images.zip file from bitbucket.
  * Get images files from temp/images.zip archive.
  * Copy images folders: upload, media.
```bash
make staging-import-images [prefix=master] [src=bitbucket]
```

### staging-export-images

  * Connect to staging droplet.
  * Copy images folders: upload, media.
  * Create temp/images.zip archive with images files.
  * Upload images.zip archive to bitbucket.
```bash
make staging-export-images [prefix=master] [src=bitbucket]
```

### staging-import-full

Starts import mysql database, content files, images.
```bash
make staging-import-full
```

### staging-export-full

Starts export mysql database, content files, images.
```bash
make staging-export-full
```

### staging-sphinx-rotate-all

Connect to Sphinx search container and run ```indexer --rotate --all```
```bash
make staging-sphinx-rotate-all
```

# Available commands (production environment)

### production-up

Creates production environment files from templates. Starts docker machines.
```bash
make production-up [prefix=master]
```

### production-pull

Connect to production server and update project.
```bash
make production-pull [version=master]
```

### production-restart

Creates production environment files from templates. Restarts docker machines.
```bash
make production-restart [prefix=master]
```

### production-stop

Stops docker machines on production server.
```bash
make production-stop [prefix=master]
```

### production-rebuild

Rebuild and restart docker machines on production server.
```bash
make production-rebuild [prefix=master]
```

### production-import-mysql-db

  * Connect to production server.
  * Download db.zip file from bitbucket.
  * Get dump db.sql file from temp/db.zip archive.
  * Import mysql dump file.
```bash
make production-import-mysql-db [prefix=master] [src=bitbucket]
```

### production-export-mysql-db

  * Connect to production server.
  * Export mysql database in db.sql file.
  * Create temp/db.zip archive with db.sql file.
  * Upload db.zip archive to bitbucket.
```bash
make production-export-mysql-db [prefix=master] [src=bitbucket]
```

### production-import-content

  * Connect to production server.
  * Download content.zip file from bitbucket.
  * Get content files from temp/content.zip archive.
  * Copy content folders: meta, content.
```bash
make production-import-content [prefix=master] [src=bitbucket]
```

### production-export-content

  * Connect to production server.
  * Copy content folders: meta, content.
  * Create temp/content.zip archive with content files.
  * Upload content.zip archive to bitbucket.
```bash
make production-export-content [prefix=master] [src=bitbucket]
```

### production-import-images

  * Connect to production server.
  * Download images.zip file from bitbucket.
  * Get images files from temp/images.zip archive.
  * Copy images folders: upload, media.
```bash
make production-import-images [prefix=master] [src=bitbucket]
```

### production-export-images

  * Connect to production server.
  * Copy images folders: upload, media.
  * Create temp/images.zip archive with images files.
  * Upload images.zip archive to bitbucket.
```bash
make production-export-images [prefix=master] [src=bitbucket]
```

### production-import-full

Starts import mysql database, content files, images.
```bash
make production-import-full
```

### production-export-full

Starts export mysql database, content files, images.
```bash
make production-export-full
```

### production-sphinx-rotate-all

Connect to Sphinx search container and run ```indexer --rotate --all```
```bash
make production-sphinx-rotate-all
```

# Project initialisation

Steps of quick start of new project:
1. You need change *.yml file with vars in folder **ansible/vars**.
2. You need check and change template files in folder **ansible/templates**.
3. You need change workspace host name in **ansible/local-hosts.yml** and **ansible/playbooks/mysql/import-db.yml** (For example: **laradockoctober_workspace_1**).
4. Run ```make project-install``` command.