# Linux Server Configuration

## IP and Port
> The IP address and SSH port so your server can be accessed by the reviewer. 

* IP:   13.127.124.159
* Port: 2200

## URL
> The complete URL to your hosted web application. 

* http://ec2-13-127-124-159.ap-south-1.compute.amazonaws.com

## Software and resources
> A summary of software you installed and configuration changes made.

* $ mv ~/Downloads/udacity_key.rsa ~/.ssh/;  
  $ chmod 600 ~/.ssh/udacity_key.rsa;  
  $ ssh -i ~/.ssh/udacity_key.rsa root@52.32.166.80  
  Reference Link: [Udacity](https://www.udacity.com/account#!/development_environment)
* $ sudo apt-get update  

* $ sudo adduser grader  

* $ sudo visudo - and then copy "grader  ALL=(ALL:ALL) ALL" under root entry  
  Reference Link: [Digitalocean](https://www.digitalocean.com/community/tutorials/how-to-add-delete-and-grant-sudo-privileges-to-users-on-a-debian-vps)  

* $ sudo vim /etc/ssh/sshd_config; - change port 22 to 2200 and update PermitRootLogin to 'no'  
  $ sudo service ssh restart  

* $ cd /home/grader;  
  $ sudo mkdir .ssh; cd .ssh  
  $ sudo cp /root/.ssh/authorized_keys ./  
  $ sudo chmod 755 authorized_keys  

* $ sudo ufw status;  
  $ sudo ufw default deny incoming;  
  $ sudo ufw default allow outgoing;  
  $ sudo ufw allow 2200/tcp;  
  $ sudo ufw allow 123/udp;  
  $ sudo ufw allow 80/tcp;    
  $ sudo ufw enable  

* sudo dpkg-reconfigure tzdata  
  Reference Link: [ask ubuntu](http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt)

* $ sudo apt-get install apache2;  
  $ sudo apt-get install python-dev python-pip;  
  $ sudo apt-get install libpq-dev; 
  $ sudo apt-get install libapache2-mod-wsgi    
  $ sudo pip install httplib2  
  $ sudo pip install requests  
  $ sudo pip install --upgrade oauth2client  
  $ sudo pip install sqlalchemy  
  $ sudo pip install python-psycopg2  
  $ sudo pip install Flask-SQLAlchemy  
  $ sudo pip install psycopg2  
   
* $ sudo apt-get install git   

* $ mkdir /var/www/flask_app/;
  $ git clone https://github.com/anish8129/Item-Catalogue.git ItemCatalogue  
  $ vim /var/www/flask_app/ItemCatalogue.wsgi - then add content to ItemCatalogue.wsgi  
  $ vim /etc/apache2/sites-available/ItemCatalogue.conf - then add content  
  $ vim /etc/apache2/sites-enabled/000-default.conf - and add WSGIScriptAlias / /var/www/flask_app/ItemCatalogue.wsgi  
  Rerefence Link [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-configure-the-apache-web-server-on-an-ubuntu-or-debian-vps)

* $ sudo apt-get install postgresql postgresql-contrib

* $ sudo -u postgres psql - in postgres terminal, create user and database
  * CREATE USER catalog WITH PASSWORD 'catalog'
  * ALTER USER catalog CREATEDB 
  * CREATE DATABASE catalog WITH OWNER catalog 

* $ nano database.py; - change engine to postgresql://catalog:catalog@localhost/catalog  
  $ sudo python database.py

* $ nano routes.py; - change engine to postgresql://catalog:catalog@localhost/catalog  
* $ sudo service apache2 restart 
* add ip or url to google/facebook developer console  
## Third-party Reasources
* [Digitalocean](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
* [Youtube](https://www.youtube.com)
* [Udacity](https://www.udacity.com)
* [Ask Ubuntu](https://askubuntu.com/)
