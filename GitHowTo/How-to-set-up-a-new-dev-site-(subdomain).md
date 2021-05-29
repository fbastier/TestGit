_Note: this process can only be used by someone with access to the server_

### I. Set up DNS on the hosting side (Pete).

### II. Set up the code
1. ssh into server1
1. cd /var/www/Sites
1. (assuming there is an up-to-date version of the VE repo in my home folder, and that my user is part of the sudoers) sudo git clone ~/Yii/.git xxxx.vocaleyes.org
1. su - root
1. cd /var/www/Sites/xxxx.vocaleyes.org
1. Copy db, debug and params from database to protected/config: cp database/db.php protected/config (…etc)
1. nano protected/config/db.php
1. Change host localhost to localab2 > Save (Ctrl + X, Y, Enter)
1. chmod 777 protected/runtime
1. mkdir assets
1. chmod 777 assets
1. cd ..
1. chown -R developer:developer xxxx.vocaleyes.org
1. su - developer
1. cp dev.vocaleyes.org/.git/config xxxx.vocaleyes.org/.git/config
1. cd xxxx.vocaleyes.org
1. git checkout -b xxxx
1. git pull origin xxxx:xxxx

### III. Set up apache redirection
1. cd /etc/apache2/sites-available
1. cp dev.vocaleyes.org.conf xxxx.vocaleyes.org.conf
1. nano xxxx.vocaleyes.org.conf
1. Replace every occurrence of dev with xxxx
1. Ctrl + w
1. Ctrl + r
1. Type dev > Enter
1. Type xxxx > Enter
1. a
1. Ctrl + x
1. Y > Enter
1. cd ../sites-enabled
1. ln -s /etc/apache2/sites-available/xxxx.vocaleyes.org.conf /etc/apache2/sites-enabled/xxxx.vocaleyes.org.conf
1. service apache2 restart

### IV. Edit crontab
1. nano /export/users/developer/update-script.sh
1. Add the following lines at the logical place

cd /var/www/Sites/xxxx.vocaleyes.org/
git fetch -a && \
git checkout xxxx && \
git pull origin xxxx && \