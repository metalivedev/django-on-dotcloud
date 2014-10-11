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

Made the necessary changes to system paths and credentials.
The credentials port was easy. 
Not sure about the Redis conversion and `CACHES` section: it wasn't
actually in the original dotCloud example, so I'm not sure why it was
removed..

Also, `MEDIA_ROOT` in settings.py expects to be persistent, and we
used to point people to the ~/data directory, which doesn't work on
cloudControl. So, that's a big difference. Is there some database
backend?

?? Should dcapproot.sh also run the postinstall script if it exists?
Probably.
