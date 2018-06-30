# LinuxServer_configuration
##This project is about the configuration of the LinuxServers.
#### Packages I have used for this project
      python
      apache2 software
      Flask etc;
#### Server details
      Server Ip Address:13.232.131.70
      UrlSite: http://13.232.131.70.xip.io
#### How to connect grader
     Download the file that is having our private key when we created our instance in the lightsail amazon.com
     Save the private key provided in your machine and run the command as follows:
     -- ssh -i path/to/privatekey -p 2200 grader@ipaddress
#### grader password
        unix
#### For update the latest versions:
       sudo apt-get update
       sudo apt-get upgrade
       sudo apt-get dist-upgrade
#### grader key 
     -----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEA5O4ifMUHIeHhfMtSdwag5U2/OXPowwpTNpBpwR9aioQreX2S
id28UcJYVvjF4CNKS32eNRxb8DHb6Ky/17U0u9FRqJwWP8PDbcXOp5ysZNWIqx7t
KuQMparJj/TCuVzgMddH8KuBBjStCJBT1r0/glFn8wIyWkmPQUMN51oSugIqck3q
o5uz3ZqWagINx1iEM35wBc/GptbOuEYTfe+k5YegGbsNFQogLssJb9sT7yZNROQT
ULrywUaGdf9Wi+BMYOub7HxCtqikFkVSEUmdV0n4UFJ/w0DfWPKw3V9ZKM+ZmvB0
M3pfLsf3d9G/3rBm3cT8Qe+l/dUNGV7Y/DOqewIDAQABAoIBAQCdlhMlYhdjynKG
jgtpJaXx0o/0g4ZRZDUd1VEHAIc53Ht0uOz7fCha+3YGAF9tx70ntAQIuUnMUPX4
95ljajgvpYoZj8B9Ckvnr4dut5mwG5FlgfduU+ckzyjKsIiuQnGNvYym7df2JqKJ
x5f+tO0XzuPIUtXIcuRq3zad79H+OZvJllmVyWHPiEec8NR9y82UOp/DQnvWDdyM
I1Nqkr6TayTgtbKVofzvWPgmfUwphzpchtrv9ZZeL1aDnpCuqvIdBcG+AJA7arpK
GpYV9HyJh3fr09Le5DVCMbdQDs6jPwXa85X6PVO7Hk9LetEQpZvcTz5io4pOc2Q1
Gpl6YNgpAoGBAP2eXdOHpMPFtMUSO6bJCs1ZIBdeKBmQYri6f9xPsWE7J1CQYUWg
VsWrqDw7nocrXymCoGH9tK44UPiGXn/fFY8pZgyjwpPF9C02vpUEYocJtuQ/1638
+i8apwwu0H0i6/cgQrztHTcXORAs+L2vBGFE5cYZjv6sV3JH0lTZMgy3AoGBAOcU
bHXaLEsJHWILf+pIsNTAo3mNK4gQNRgQA2bsBO6+XptLNctowgZjtdh+dVC0ksTh
WU93Wb1jms6sLdcdw8iD6KVap8uqVvKtfmVLcf/e/5vlg0mnI5E3wikyg/LolOSP
fw83OlfGA29/Ctn6kJrUS9CFGgEwCOEebKCG71RdAoGBAPFS98SHlWgTf+blao1R
T04GOFsD5PQuR0GvdGqWChqSxt4KBATUhLyikfp+YGIOCwbcnO+hEYOVYraYZOMX
ytPmeIweZs9l1OoQ5Ve2TGph+/1EIl4UEZswqTMWeJwZ1p3XvKk4lkwNdObHZAhZ
uLk1bc4KE96Q7sR3QtQpt04RAoGAARGAGt9iWwp0v1JMShoB70ngt5wmel+Qz0ar
rVsj/rKUn2Uun30hgIQPgCu9gR0EnLJqBksH+C8wtQnowFjb4d5yQel0YyWrdz3E
GtXJdiRizCa4f6utJ2u5kxUvtPzMS246aSiZNXSt6WMN+soExyJ6I0GqSB0fvWK1
n9xf2OUCgYEA5LaV101bsZa1ta4M97VVuAm+mH+4r3RS8CDtxelETRG6zfwGT/V9
g64HxExlxln5R2ISEH4PvyRT9qslQ0xtfIOfpi0M5vdkJxf4oG5CAwMeQGiv88a1
NH/smDk8W3u8cjPaR/W3Wzlo2PbtC1RK0EN5Nl4W36r6tJDFtBoxdTc=
-----END RSA PRIVATE KEY-----
       
       
#### To create grader user:
      we have to creater a new user called grader
         -- sudo adduser grader
#### To get another new user:
      In order to grant permissions to the grader we have to open a nano file  
         -- sudo nano /etc/sudoers
#### To grant permissions:
       grader  ALL=(ALL:ALL) ALL
#### To create ssh keypair grader:
        The generated keys will be stored in .ssh folder
            -- ssh-keygen
            This generate the public key and private key to the .ssh folder
#### To get change to the new user:
     su - grader
#### create a new folder .ssh and new authorized_file:
        mkdir .ssh
#### Then copy the public keys with .pub extension and save the authorized file
        sudo nano .ssh/authorized_keys
#### To get permissions for to user:
       chmod 700 .ssh
#### To prevent other user to write on file:
      chmod 644 .ssh/authorized_keys

#### run the following commands:
        service ssh restart
    Then log in to grader with your privatekey generated
          ssh -i .ssh/id_rsa grader@ipaddress
    we have to change the port to 2200 with the following code:
        sudo nano /etc/ssh/sshd_config
    restart the ssh server:
          service ssh restart
    then we have to add this port 2200 in the lightsail networkings tab for firewall safety
    Login into grader using the below command:
          ssh -i .ssh/id_rsa -p 2200 grader@ipaddress
    Then run the following command to disable ssh root as login:
          sudo nano /etc/ssh/sshd_config
          make change of PermitRootLogin to 'no'
     Firewall safety commands:
            sudo ufw allow 2200/tcp
            sudo ufw allow 80/tcp
            sudo ufw allow 123/udp
            sudo ufw enable
    run "sudo ufw status"
#### Installing Apache2:
    sudo apt-get install apache2
    sudo apt-get install python-setuptools libapache2-mod-wsgi
    sudo a2enmod wsgi
    We have to create a flaskapp:
      sudo mkdir FlaskApp
      cd FlaskApp
    Install git:
        sudo apt-get install git
    get the app you have to deploy from your github account:
        sudo git clone  https://github.com/devisrikomati/NeverGiveUp.git
    Change the main file name to __init__.py:
        sudo mv mainproject.py __init__.py
    open init file and add the json file:
       sudo nano __init__.py
      PROJECT_ROOT = os.path.realpath(os.path.dirname(__file__))
      json_url = os.path.join(PROJECT_ROOT, 'client_secrets.json')
    then save it and exit:
         ctrl+o
         ctrl+x
     Create a wsgi file:
            sudo nano mv project.py FlaskApp.wsgi
      Add the following code into the wsgi file:
            #!/usr/bin/python
            import sys
            import logging
            logging.basicConfig(stream=sys.stderr)
            sys.path.insert(0,"/var/www/FlaskApp/")
            from FlaskApp import app as application
            application.secret_key = 'Add your secret key'
      create a cofiguration file:
            sudo nano /etc/apache2/sites-available/FlaskApp.conf
       Add the following code into the .conf file:
              <VirtualHost *:80>
              ServerName mywebsite.com ----(static ip)
              ServerAdmin admin@mywebsite.com
              WSGIScriptAlias / /var/www/FlaskApp/flaskapp.wsgi
              <Directory /var/www/FlaskApp/FlaskApp/>
                Order allow,deny
                Allow from all
              </Directory>
              Alias /static /var/www/FlaskApp/FlaskApp/static
              <Directory /var/www/FlaskApp/FlaskApp/static/>
                Order allow,deny
                Allow from all
              </Directory>
              ErrorLog ${APACHE_LOG_DIR}/error.log
              LogLevel warn
              CustomLog ${APACHE_LOG_DIR}/access.log combined
                </VirtualHost>
       In order to run the app we have to install the following softwares :
                pip install sqlalchemy
                pip install flask
                pip install oauth2client
                pip install pyscopg2
                pip install requests
#### Install postgresql:
    sudo apt-get install postgresql
#### login to postgres:
     sudo su - postgres
     psql
#### create a new user in postgres:
    CREATE USER catalog WITH PASSWORD 'password';
#### give the user permissions to create a new database:
     ALTER USER item_catalog CREATEDB;
#### To create a new database with user :
    CREATE DATABASE catalog WITH user catalog;
#### connect to db:
    \c catalog
#### give permissions to public:
    REVOKE ALL ON SCHEMA public FROM public;
#### grant permissions on schema for catalog:
     GRANT ALL ON SCHEMA public TO catalog;
    Example for deploying a flaskapplication can be known from digitalOcean
    Now login to your developer console and select your project and edit Oauth details:
    Javascript origin 
    http://ip.xip.io
    redirect URI
    http://ip.xip.io\login
    http://ip.xip.io\gconnect
    http://ip.xip.io\callback
    xip.io is a free DNS which will be the same as using IP address
## Final Step:
    sudo service apache2 restart
    open browser and type http://ip.xip.io(chage ip address) . open my project 
## refrences:
    -- https://www.digitalocean.com
    -- https://stackoverflow.com/   
    -- Udacity Full stack nanodegree course of my classroom videos. 
   
