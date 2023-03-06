# Nginx-project

## Installation of NGINX on Ubuntu

NGINX is a high-performance web server, load balancer, and reverse proxy that is widely used by web developers and system administrators. This guide will walk you through the steps to install NGINX on Ubuntu.

## Prerequisites
Before installing NGINX, make sure that you have a non-root user account with sudo privileges. If you don't have one, you can create a new user and grant sudo privileges by following this tutorial.

## Installation

Update your package index:

```bash
sudo apt-get update
```

Install NGINX using apt-get:
```bash
sudo apt-get install nginx
```
Once the installation is complete, start the NGINX service:
```bash
sudo systemctl start nginx
```
To verify that NGINX is running, check its status:
```bash
sudo systemctl status nginx
```
You should see output indicating that the service is active and running.

NGINX should start automatically after a reboot. To enable this, run:
```bash
sudo systemctl enable nginx
```
## Configuration

NGINX's configuration files are located in the /etc/nginx/ directory. The main configuration file is nginx.conf. Before making any changes to this file, make a backup copy:
```bash
sudo cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bak
```
To apply any changes you make to the configuration files, you'll need to restart NGINX:
```bash
sudo systemctl restart nginx
```
## Conclusion
You've successfully installed and configured NGINX on your Ubuntu server. For more information on how to configure NGINX, see the official [documentation](https://nginx.org/en/docs/).
