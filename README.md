# Install-Workpress
#  Download the latest version of WordPress
'''
wget http://wordpress.org/latest.tar.gz

tar -xzvf latest.tar.gz
'''
# Create a database and users
'''
mysql -u root -p

mysql> CREATE DATABASE wordpress;
Query OK, 1 row affected (0.00 sec)


mysql> CREATE USER user@localhost;
Query OK, 0 rows affected (0.00 sec)

mysql> SET PASSWORD FOR user@localhost= PASSWORD("password");
Query OK, 0 rows affected (0.00 sec)

mysql> GRANT ALL PRIVILEGES ON wordpress.* TO user@localhost IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

mysql> exit
'''
# Set WordPress
cp ~/wordpress/wp-config-sample.php ~/wordpress/wp-config.php

vi ~/wordpress/wp-config.php
# Enter all the information here: database name, database user name and password for the database:
define('DB_NAME', 'wordpress');
define('DB_USER', 'user');
define('DB_PASSWORD', 'password');
define('DB_HOST', 'localhost');
# Transfer Wordpres files to /var/www/html
cp -r ~/wordpress/* /var/www/html
service httpd restart
