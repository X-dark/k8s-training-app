# Nginx lab

## Spawn a standalone Nginx instance

* Create a Namespace.
* Deploy the `nginx:stable` image, using a `deployment` of one replica and exposing the port `80`.
* Try to connect to it using port forwarding from the hosting node.

## Create a service to expose Nginx

* Expose the Nginx server, with a service to facilite access to it.

## Expose a static webpage with Nginx

* Create a basic HTML file with the content of your choice
* Create a `configmap` with the html file
* Modify the nginx deployment to mount the configmap into `/usr/share/nginx/html`
* Confirm the webpage is now available
