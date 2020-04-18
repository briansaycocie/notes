# WordPress

## Update database URLs
```bash
wp search-replace --all-tables --precise --url=mysite.com mysite.com mysite.dev
```

## Create wp-config.php file
```bash
wp config create --dbname=wordpress --dbuser=wordpress_user --dbpass=wordpress_password --dbprefix=wp_
```

## Setup wp-config.php
```php
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', false );
define( 'SCRIPT_DEBUG', true );
define( 'JETPACK_DEV_DEBUG', true );
define( 'ALLOW_UNFILTERED_UPLOADS', true );
```

## Setup wp-config.php in production
```php
define( 'DISALLOW_FILE_EDIT', true );
```

## Setup multi-site network
```php
define( 'WP_ALLOW_MULTISITE', true );
define( 'MULTISITE', true );
define( 'SUBDOMAIN_INSTALL', false );
define( 'DOMAIN_CURRENT_SITE', 'mysite.dev' );
define( 'PATH_CURRENT_SITE', '/' );
define( 'SITE_ID_CURRENT_SITE', 1 );
define( 'BLOG_ID_CURRENT_SITE', 1 );
```

## Clear transient from MySQL database
```bash
vagrant ssh (or ssh into server)
mysql -u root -p
USE database_name;
DELETE FROM `wp_options` WHERE `option_name` LIKE ('%\_transient\_%');
flush privileges;
```

## Import XML into local site
```bash
wp import domain.wordpress.2020-01-01.xml --authors=skip --url=mysite.dev
```

## Maintenance mode
```
File: .maintenance
Input: <?php $upgrading = time(); ?>
```