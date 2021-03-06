# Docker

**--- For the moment this approach only works for IP cameras, we don't have a cross-platform method to inject a USB camera or Raspberry Pi camera ---**

A Docker image (x86) is available on [**the Docker Hub**](https://hub.docker.com/u/kerberos/). Before you can run this image you will have to get [**Docker**](https://docker.com) installed. After the installation you can use **docker-compose** to get Kerberos.io up and running. More detailed information can be [**found here**](https://blog.cedric.ws/kerberosio-available-on-docker).

## Docker Compose

Create a **docker-compose.yml** file and following configuration:

    machinery:
        image: kerberos/machinery
        ports:
        - "8889"
    web:
        image: kerberos/web
        environment:
        - KERBEROSIO_SECURE_SSL=false
        ports:
        - "80"
        volumes_from:
        - machinery
        links:
        - machinery

Run following command; this will download the Kerberos.io docker images and configure them properly.

    docker-compose up
