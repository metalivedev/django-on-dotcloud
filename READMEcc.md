# Porting notes

## Installation

Create the app with the custom buildpack and push:

   $ cctrlapp djondc create custom --buildpackhttps://github.com/metalivedev/buildpack-python-cloudcontrol#dotcloud
   Git configuration found! Using "Git" as repository type.
   $ cctrlapp djondc/cloudcontrol push
   :
   -----> Adding default Procfile: web: /srv/www/bin/dcapproot.sh; supervisord -c config/supervisord.conf
   -----> Building image
   -----> Custom buildpack provided
   -----> Uploading image (32.3 MB)
       
   To ssh://djondc@cloudcontrolled.com/repository.git

Add on Postgre and Redis:

   $ cctrlapp djondc/cloudcontrol addon.add postgresqld.micro
   $ cctrlapp djondc/cloudcontrol addon.add openredis.micro

If you see "Gone" that means you haven't pushed the deployment version
yet. You don't have to cctrlapp deploy, but you do have to push.

