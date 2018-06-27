# Linux-Server-Configuration

# # IP address
The user grader can log in to the Ubuntu server at http://ec2-13-58-221-240.us-east-2.compute.amazonaws.com on port 2200 via SSH.
# # Web Application
The web application can be accessed at http://ec2-13-58-221-240.us-east-2.compute.amazonaws.com/ in any browser of choice.
# # Software Installed
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
# # Packages Installed
- finger
- apache2
- python3
- git
- libapache2-mod-wsgi-py3
- python3-flask
- python3-pip
- mysql-server
- mysql-client
- python3-sqlalchemy
- python3-oauth2client
- python3-httplib2
- python3-urllib3
- sqlite3
python3.5-venv
# # Resources used
Stack Exchange and Ubuntu
