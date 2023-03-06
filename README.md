# Nginx-project on Ubuntu

## Cloning Git repo

Install the git on your system by below command

```bash
apt-get isntall git
```

Now clone the Nginx-project repo:

```bash
git clone https://github.com/sanket363/Nginx-project.git
```

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

## Docker Installation

Install Docker using apt-get:

```bash
sudo apt-get install docker.io
```
Add your current user to the docker group:

```bash
sudo usermod -aG docker $USER
```
Reboot the system to apply the changes:

```bash
sudo reboot
```

## Building and Running Docker Container

Navigate to the directory that contains your Dockerfile and run the following command to build the container:

```bash
sudo docker build -t my-notes-app:latest .
```
To run the container and map port 8000 on the container to port 8000 on the host, run the following command:

```bash
sudo docker run -p 8000:8000 my-notes-app:latest
```

## Configuring NGINX

NGINX's configuration files are located in the /etc/nginx/ directory. The main configuration file is nginx.conf. Before making any changes to this file, make a backup copy:

```bash
sudo cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.bak
```
To apply any changes you make to the configuration files, you'll need to restart NGINX:

```bash
sudo systemctl restart nginx
```
To add a proxy pass configuration for your Docker container, navigate to the sites-enabled path on Ubuntu:

```bash
cd /etc/nginx/sites-enabled/
```

Use the following command to open the default file in Vim:

```bash
sudo vim default
```
Find the ```location /``` block and inside the curly braces, add the following line to create a proxy pass to your Docker container:

```bash
proxy_pass http://127.0.0.1:8000;
```

Add another ```location``` block for proxy the API requests to the container:
```bash
location /api {
  proxy_pass http://127.0.0.1:8000/api;
}
```

After saving above changes in default file now navigate to the /var/www/html/ location and do below commands:
```bash
mkdir static
```

```bash
cp -r /home/<your-user>/Nginx-project/mynotes/build/static/* /var/www/html/static/
```

Once done restart the nginx service

```bash
systemctl restart nginx
```

Now navingate to your browser and go to the url
```
http://<public-ip>/
```

Boom 🔥🔥🔥 you can see your notes app

## Conclusion
You've successfully installed and configured NGINX on your Ubuntu server. For more information on how to configure NGINX, see the official [documentation](https://nginx.org/en/docs/).
