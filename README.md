# linux-commands
My Linux Commands 

* `history | awk '!($1="")'` --- When I dont need numbering with my history
* Folder permissions
```
sudo chown -R www-data .
sudo chgrp -R www-data .
sudo chmod -R g+rwxs .
```
### PHPmyadmin Security tips

#### Add htaccess

* `sudo apt-get install apache2-utils` --- install apache utils 
* `sudo vi /etc/phpmyadmin/apache.conf` -- and add following lines
```
<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php
        AllowOverride All
```
* `sudo vi /usr/share/phpmyadmin/.htaccess` --- now create the .htaccess file
```
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/.phpmyadmin.htpasswd
Require valid-user
```
* `sudo htpasswd -c /etc/apache2/.phpmyadmin.htpasswd username` --- add username and password after enter
* `sudo vi /etc/phpmyadmin/config.inc.php` --- change the alias to access the phpmyadmin
```
Alias /phpmyadmin7iuhyY /usr/share/phpmyadmin
```
* `sudo service apache2 restart`
