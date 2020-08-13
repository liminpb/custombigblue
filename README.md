# Install Greenlight

Greenlight is a simple front-end for BigBlueButton written in Ruby on Rails. It lets users create accounts, have permanent rooms, and manage their recordings. It also lets you, as the administrator, manage the user accounts (such as approve or deny users).

You can install Greenlight by adding the -g option.

wget -qO- https://ubuntu.bigbluebutton.org/bbb-install.sh | bash -s -- -v xenial-22 -s <replace with your domain> -e <replace with mail account> -w -g

Once Greenlight is installed, it redirects the default home page to Greenlight. You can also configure GreenLight to use OAuth2 authentication.

To launch Greenlight, simply open the URL of your server, such as https://bbb.example.com/. You should see the Greenlight landing page.

To set up an administrator account for Greenlight (so you can approve/deny signups), enter the following commands

cd greenlight/
docker exec greenlight-v2 bundle exec rake admin:create

This command will create an admin account and set a default password. After running this command, login using the given username/password and change the default password. Next, select 'Administrator' and choose 'Organization'.


You can then select 'Site Settings' on the left-hand side and change the Registration Method to 'Approve/Decline'.


You can now contol who creates accounts on your BigBlueButton server. For more information see Greenlight administration.


# How to Rebrand your Bigbluebutton. 

After the installation using bbb-install.sh there will be a following things will be created in your server. 

1. BBservice on server. 
2. Java service witha Java web content.
3. Nginx service.
4. Docker container for Greenlight app.
5. Postgress Docker container for storing DB content user details etc. 

So we hvae to make following changes in the files to rebrand the same. 

1. Welcome message. 

==

==

2. Branding image.

==
==

3. favicon.

==
==

4. Helo URL.

==
==

5. PDF file in chat room. 

==
==

6. Metadata while sharing URL.

===
===

