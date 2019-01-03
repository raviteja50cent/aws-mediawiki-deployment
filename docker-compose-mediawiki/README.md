# Docker Compose - MEDIAWIKI(PHP,APACHE) - MYSQL

**What was acheived:**

This folder has `docker-compose.yml` file that will create two docker containers of mediawiki and mysql with ports exposed from container to host.

Once containers are created, I can access the mediawiki application page on the browser using the `localhost:exposed-port`.

**What was not acheived:**

As soon as the mediawiki webapp is running on container, I will have to run the `docker-compose restart` to copy the `LocalSettings.php` file to install wiki.