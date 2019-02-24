README
======================


# Installing locally

Please follow this steps in order to run codeigniter-vue2 locally

### 1 - Add Host to /etc/hosts

```
$ sudo echo "127.0.0.1 site-local.com.br www.ci-vue.com" >> /etc/hosts
```

### 2 - Create Apache's Virtual Host

```
<VirtualHost *:80>
	ServerName ci-vue.com
	ServerAlias www.ci-vue.com
	DocumentRoot "/path/to/genericdash/httpdocs"

	SetEnv CI_ENV development

	<Directory "/path/to/genericdash/httpdocs">
		AllowOverride All
		Allow from All

		Require all granted
	</Directory>

	ErrorLog "/var/log/apache2/error_log"
	CustomLog "/var/log/apache2/access_log" common
</VirtualHost>
```

Don't forget to run:
```
sudo a2ensite ci-vue.com.conf
```

### 3 - Enabling mod_rewrite

```
sudo a2enmod rewrite
```

### 4 - Restart Apache

```
sudo service apache2 reload
```

### 5 - Create database

```
mysql> CREATE DATABASE ``;
```

### 6 - Include the CI_ENV environment selection

First you need to find your profile file. Usually is the .bashrc, but
if you are using the zsh bash, its the .zshrc, in your home folder. Then add this
```
export CI_ENV=development
```

### 7 - Run the migrations

```
$ php httpdocs/index.php migrate
```

### 8 - It's all good!

Point your browser to:

- [http://www.ci-vue.com](http://www.ci-vue.com)
