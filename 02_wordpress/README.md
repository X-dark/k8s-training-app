# Wordpress lab

## Spawn a standalone Wordpress instance

* Create a Namespace.
* Deploy the `wordpress:5` image, using a `deployment` of one replica and exposing the port `80`.
* Try to connect to it using port forwarding from the hosting node.
* Confirm the Wordpress setup screen is available and that you need a database to complete the setup.

## Create a service to expose Wordpress

* Expose the Wordpress server, with a service to facilite access to it.

## Create a MariaDB database

* Deploy the `mariadb:10` image: 
  * Using a `deployment` of one replica
  * Exposing an environment variable called `MYSQL_ROOT_PASSWORD` containing the password of your choice
  * Exposing an environment variable called `MYSQL_DATABASE` with the value `wordpress` (to automatically create an empty database at MariaDB startup)
  * Exposing the port `3306`.
* Create a `service` to expose the MariaDB server.
* Resume the Wordpress setup to use the newly created database.
* Delete the mariadb container to have it recreated.
* Go back to Wordpress and note that all previous work is now lost.

## Put Wordpress database settings into environment variables

* Edit the wordpress deployment and add the following environment variables with appropriate values:
  * WORDPRESS_DB_HOST
  * WORDPRESS_DB_NAME
  * WORDPRESS_DB_USER
  * WORDPRESS_DB_PASSWORD
* Confirm the database settings are now automatically configured.

## Persist the MariaDB volume

* Create a `PersistentVolumeClaim` to store MariaDB data.
* Modify the mariadb deployment to mount the new PersistentVolume into `/var/lib/mysql`
* Repeat the Wordpress setup
* Delete the mariadb container and confirm the Wordpress configuration is restored from the database.
