# Linux Server Configuration
URL: http://3.224.57.144.xip.io/
IP: http://3.224.57.144
SSH Port: 2200

Udacity Project Rubric: https://review.udacity.com/#!/rubrics/2007/view

## Step-by-step Walkthrough
### Set Up Server
1. Started a new Ubuntu Linux server instance on [Amazon Lightsail](https://lightsail.aws.amazon.com/).
* Created an instance on Lightsail - I went with Ubuntu 16.04 LTS after choosing "OS Only" (not apps), and the free plan.

2. Follow the instructions provided to SSH into the server.
* Use the private key from the downloaded folder to login as the ```ubuntu``` user.

### Secure the Server
3. Updated all currently installed packages.
* Run the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

4. Changed the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it, and change ```PermitRootLogin``` and edit it to ```no```.

5. Configured the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

6. Set scripts to automatically manage package updates
```
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

### Give grader access
7. Created a new user account named ```grader```, and gave sudo access to it.

8. Created an SSH key pair for ```grader``` using the ```ssh-keygen``` tool.
 * You can ssh into the instance as grader by running the following command: ```ssh -i ~/ENTER_KEY_LOCATION.rsa -p 2200 grader@3.224.57.144```
 * Key will be in instructor notes with project submission!

### Prepare to deploy
9. Configured the local timezone to UTC.

10. Installed and configured Apache to serve a Python mod_wsgi application.

11. Installed ```git```.

### Deploy the Item Catalog project (Restaurant App).
12. Cloned and set up my Item Catalog project.
* Cloned with ```git clone https://github.com/brienomatty/udacity-item-catalog catalog```.
* Changed owner to ```grader```.

13. Installed virtual environment
* Configured and enabled a new virtual host

14. Installed Flask

15. Installed the project's dependencies

16. Installed and configured PostgreSQL

## Third-Party Resources
This project was huge, terrifying, and awesome. Special thanks to the following resources for paving the way:
* https://github.com/iliketomatoes/linux_server_configuration
* https://github.com/kcalata/Linux-Server-Configuration (I used a LOT of these steps to learn from when I stumbled)
* https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps (Fantastic article about deploying a flask app on Ubuntu)
* https://umar-yusuf.blogspot.com/2018/02/deploying-python-flask-web-app-on.html (Another great article)
* https://www.postgresql.org/docs/9.0/sql-createdatabase.html (PSQL documentation)
* https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-connecting-to-your-postgres-database
* https://lightsail.aws.amazon.com/ls/docs/en_us/articles/amazon-lightsail-databases
* https://github.com/juvers/Linux-Configuration
* https://knowledge.udacity.com/questions/ (Made significant use of the Udacity knowledge areas)

## Further Reading
* https://www.matthealy.com.au/blog/post/deploying-flask-to-amazon-web-services-ec2/ (I plan to try deploying this to EC2 next)
