#### config for python flask application with virtual env
```
<VirtualHost *:80>
		ServerName mywebsite.com
		ServerAdmin admin@mywebsite.com
		WSGIDaemonProcess catalogger python-path=/var/www/catalogger:/var/www/catalogger/catalogger/venv/lib/python3.6/site-packages
		WSGIProcessGroup catalogger
		WSGIScriptAlias / /var/www/catalogger/app.wsgi
		<Directory /var/www/catalogger/catalogger/>
			Order allow,deny
			Allow from all
		</Directory>
		Alias /static /var/www/catalogger/catalogger/static
		<Directory /var/www/catalogger/catalogger/static/>
			Order allow,deny
			Allow from all
		</Directory>
		ErrorLog ${APACHE_LOG_DIR}/error.log
		LogLevel warn
		CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
