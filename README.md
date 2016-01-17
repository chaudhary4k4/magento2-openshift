Magento 2 on OpenShift
====================

This git repository deploys a Magento 2 store on OpenShift.

An empty database is populated, and the application is configured automagically.

Running on OpenShift
----------------------------

Create an account at http://www.openshift.com/

Get a Magento API key pair 

Create a new OpenShift app with NGINX as web server (you can call your application whatever you want), write down your Git Remote SSH url.

    rhc create-app $myapp http://cartreflect-claytondev.rhcloud.com/github/boekkooi/openshift-cartridge-nginx API_KEY=123 API_SECRET=123

Install PHP 5.6 cartridge into the app
    
    rhc cartridge add -a $myapp http://cartreflect-claytondev.rhcloud.com/github/boekkooi/openshift-cartridge-php

Install mysql-5.5 cartridge into the app

    rhc cartridge add -a $myapp mysql-5.5

Clone this repository and push it to your app, we will take care of everything for you :)

    git clone https://github.com/javilumbrales/magento2-openshift
    cd magento2-openshift
    git remote add $myapp YOUR_GIT_REMOTE_SSH_URL
    git push $myapp master -f

That's it, you can now checkout your application at:

    http://$appname-$yournamespace.rhcloud.com

Default admin credentials: username _admin_ password _OpenShiftAdmin123_.

### Post-installation details

After the installation it is important to change the admin password and other Magento configurations properly. Log in to 

    http://$appname-$yournamespace.rhcloud.com/admin123

using the provided credentials and check all system settings, for example:

 * System > My Account
 * System > Configuration > General > Countries Options
 * System > Configuration > General > Locale Options
 * System > Configuration > Admin
 * System > Configuration > System
 
For a detailed guide check our post [How to install Magento 2 on OpenShift](http://thedeveloperworldisyours.com/magento/how-to-install-magento-2-on-openshift/ "How to install Magento 2 on OpenShift")
