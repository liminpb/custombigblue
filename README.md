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
1. Login to the server SSH.
2. Login to docker image as bash
          docker exec -it <greenlightcontainer id> bash
3. edit "./config/locales/en.yml". 
4. Make following changes. 

5. Change line 

bigbluebutton: Bigbluebutton >> bigbluebutton: Your app name

greenlight: Greenlight   >> greenlight: Your Greenligh Name. 

Under landing: section change everything with Bigbluebutton with your app name. 

You can replace every Bigbluebotton with your appname and Greenlight with Your appname. But make sure that you are not changing any variable. 

(bigbluebutton:   do not change the variable name before : )

6. Stop start your docker container. 
==


2. Branding image.

==
Loigin to app as administrator. 
Go to Orgonization from Top Right handside Admin button.
Select site setting. 
Update you branding image in the Apperence section. Click on Change image. 

==

3. favicon.

==
1. Login to docker as bash.
2. change favion in following directorty with your favicon 
/usr/src/app/public/assets
/usr/src/app/public.
3. Stop start your docker container. 
==

4. Help URL.

==
1. Login to docker as bash.
2. edit ./app/views/shared/_header.html.erb  
3. remove the help_url section in the file. 
   
   <% if Rails.configuration.help_url.present? %>                                                                                                                            <a class="dropdown-item" href="<%= Rails.configuration.help_url %>" target="_blank" rel="noopener">                                                                       <i class="dropdown-icon far fa-question-circle"></i> <%= t("header.dropdown.help") %>                                                                                 </a>                                                                                                                                                                  <% end %>  
4. Stop start your docker container. 
==

5. PDF file in chat room. 

==
1. Login to ssh.
2. cd /var/www/bigbluebutton-default
3. Replace the default.pdf with your PDF.  
4. Restart bb service "sudo bbb-conf --restart"
==

6. Metadata while sharing URL.

===
1. login to docker using bash.
2. edit followiing ./config/locales/en.yml

 landing:                                                                                                                                                                  about: "%{href} is a simple front-end for your BigBlueButton open-source web conferencing server. You can create your own rooms to host sessions, or join others usi
 
 change %{href}  >>  YourAPP name. 

3. Stop start your docker container. 
===

7. Header and Footer. 

==
1. Login to docker as bash.
2. Edit following files and replace Bigbluebotton with your app name. 
./app/views/shared/_footer.html.erb
./app/views/main/index.html.erb
3. Stop start your docker container. 
==

8. Change Logo in chat room section.

==
1. Login to server SSH.
2. cd  /var/bigbluebutton/playback/2.0/
3. Change logo.png with your logo.
4. Restart bb service "sudo bbb-conf --restart"
==
