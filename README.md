# Linux-Server-Configuration

## IP address
The user grader can log in to the Ubuntu server at 13.58.221.240 on port 2200 via SSH.
## Web Application
The web application can be accessed at http://ec2-13-58-221-240.us-east-2.compute.amazonaws.com/ in any browser of choice.
## Configuration Changes
The following configuration changes were made to the server
1. Root Login was disabled in /etc/ssh/sshd_config
2. created grader user with the following command
```
sudo adduser grader
```
3. Added grader user to the sudo group with the following command
```
sudo usermod -aG sudo grader
```
4. Created a private-public key pair on the local machine using ssh-keygen. Copy pasted the contents of the graderKey.pub file in a new file located at /home/grader/.ssh/authorized_keys.
5. ssh port number was changed from 22 to 2200 in /etc/ssh/sshd_config
6. Firewall was enabled with following rules:
```
sudo ufw allow ssh
```
```
sudo ufw allow 2200/tcp
```
```
sudo ufw allow 80/tcp
```
```
sudo ufw allow ntp
```
```
sudo ufw deny 22/tcp
```
```
sudo ufw enable
```
7. ssh remote login was enforced by setting PasswordAuthentication to no in /etc/ssh/sshd_config 
8. update and upgrade all available packages list using 
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

9. Change read write permissions to /var/www/catalog/catalog.db to allow write queries.
## Packages Installed
- finger
- apache2
- python3
- git
- libapache2-mod-wsgi-py3
- python3-flask
- python3-pip
- python3-sqlalchemy
- python3-oauth2client
- python3-httplib2
- python3-urllib3
- sqlite3
python3.5-venv
## Resources used
The Udacity course on [Configuring Linux Web Servers](https://classroom.udacity.com/courses/ud299-nd) was used as the main reference in configuring the firewall settings, adding a new user and setting up ssh login with a private-public key pair. 
Other references used are as follows:
- [Setting up AWS EC2 instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html)
- blog posts on Deploying a Flask Application on ubuntu 
-- [Blog 1](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
-- [Blog 2](https://devops.profitbricks.com/tutorials/deploy-a-flask-application-on-ubuntu-1404/)
- [Flask Documentation on mod_wsgi](http://flask.pocoo.org/docs/1.0/deploying/mod_wsgi/)
