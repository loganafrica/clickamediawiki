Mediawiki installed on LEMP.

Installation Considerations:

Web server
In order to serve wiki pages to browsers, MediaWiki requires some web server software. Often you will not have a choice of which software to use – it will be the one provided by your hosting provider.
MediaWiki is broadly compatible with all major web servers that can invoke a compatible version of PHP. Most installations use the Apache HTTPD web server. Nginx (configuration example) is a good choice as well.

PHP
PHP is the programming language in which MediaWiki is written, and is required in order to run the software.

For the latest stable version of MediaWiki, at least PHP 7.4.3 is required. See the page on Compatibility for further information.
MediaWiki is not compatible with PHP 7.4.0 - 7.4.2 due to an upstream bug. Use PHP 7.4.3+ instead. See task T246594 for more information.
If using PHP 8, it is recommended to use MediaWiki 1.38.4 or higher. PHP 8 is not in use by Wikimedia wikis, and thus gets less testing, but other groups do use MediaWiki with PHP 8 without issue. If you encounter any bugs when using MediaWiki with PHP 8, please report them. See task T248925 for more information.
The following extensions are required:
calendar - required since MW 1.33
dom - required since MW 1.34
fileinfo - required since MW 1.30
intl - required since MW 1.36
json - required since MW 1.22
mbstring - required since MW 1.27, recommended in earlier versions
openssl - required since MW 1.27, see $wgSessionInsecureSecrets if unavailable
xml - required since MW 1.27, recommended in earlier versions
xmlreader - required since MW 1.36
The following extensions are recommended in addition to the required ones:
apcu
curl
MediaWiki only requires PHP extensions that are enabled in PHP by default. If your hosting provider provides a basic LAMP environment without these, you may need to install or enable these manually.
In Debian/Ubuntu, the following command installs all recommended PHP extensions listed above:
sudo apt-get install php php-intl php-mbstring php-xml php-apcu php-curl
At hosting providers with a control panel such as cPanel, you can often use "Select PHP Version" (PHP Selector) to enable these extensions. (For example, after seeing "You are missing a required extension to PHP that MediaWiki requires to run. Please install: intl")
On most Debian/Ubuntu-based distros the php-mysql package is required if you want MediaWiki to use MySQL.
Some features of MediaWiki may require PHP functions that execute external processes, like image thumbnailing, that some cheap hosts usually disable. Please take this into consideration if you plan to install MediaWiki on a shared host.
MediaWiki extensions may require additional PHP features, e.g. VisualEditor requires libcurl support (php-curl on Debian/Ubuntu-based distros).
If you need to compile PHP from source, then see PHP configuration for compilation options that affect MediaWiki.

Database server
MediaWiki stores all the text and data (content pages, user details, system messages, etc.) in a database, which it is capable of sharing with other web-based applications (phpBB, etc.). You will need one of the following database servers to run the latest version of MediaWiki:

MariaDB 10.3.0+ or MySQL 5.7.0+
PostgreSQL 10.0+
SQLite 3.8.0+
Using MariaDB or MySQL is recommended as Wikimedia uses MariaDB. Any other database servers are less tested and you may likely run into some bugs.

MediaWiki no longer supports using Oracle or Microsoft SQL Server as of version 1.34.

Hardware requirements
The recommended minimum requirements are 256MB of RAM for a single-computer website and 85MB of storage, although this will not suffice for a busy public site or a site with uploading enabled. Some users have reported running MediaWiki on computers with as little as 48MB of RAM.

Optional dependencies
ImageMagick or GD is required for Image thumbnailing.
Shell access is required to run Maintenance scripts; upgrading MediaWiki may be more difficult without it.
Sending email notifications via the server itself requires a message transfer agent (MTA).
GNU diff3 can be used to automatically resolve conflicts.
memcached can be used for object caching.
