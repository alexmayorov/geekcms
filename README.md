# GeekCMS

[![License](https://img.shields.io/packagist/l/doctrine/orm.svg)](https://scrutinizer-ci.com/g/miuapps/geekcms/build-status/LICENSE)
[![Version](https://img.shields.io/badge/version-0.1-lightgrey.svg)]()
[![Build Status](https://scrutinizer-ci.com/g/miuapps/geekcms/badges/build.png?b=master)](https://scrutinizer-ci.com/g/miuapps/geekcms/build-status/master)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/miuapps/geekcms/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/miuapps/geekcms/?branch=master)

GeekCMS is a very simple, blazing fast CMS. See http://geekcms.miuapps.com/ for more info.

[![I Love Open Source](http://www.iloveopensource.io/images/logo-lightbg.png)](http://www.iloveopensource.io/)

Minimal requirements
---

 - Requires PHP 7+ or HHVM Hacklang
 - Requires Twig 1.22+
 - Markdown like parser (erusev/parsedown-extra)

Download
---
You can install the latest version either by downloading it from <http://geekcms.miuapps.com/> or use Git:

```shell
git clone https://github.com/miuapps/geekcms.git
```

Install
---
Download [composer](<https://getcomposer.org/>) and run it with install option.

    $ curl -sS https://getcomposer.org/installer | php
    $ php composer.phar install

Run
---

The easiest way to GeekCMS is using [the built-in web server on PHP](<http://php.net/manual/en/features.commandline.webserver.php>).

    $ php -S 0.0.0.0:8080

GeekCMS will be accessible from <http://localhost:8080>.

Nginx
---


    # Example of configuration

    server {
        listen :80;
        server_name yoursite.com;
    
        set $sname yoursite.com;
        set $root "/www/sites/$sname/public";
    
        root $root;
        index index.php index.html index.htm;
    
        location = / {
            include php.conf;
        }

        location / {
            if (!-e $request_filename) {
                rewrite ^(.*)$ /index.php last;
            }
        }
    
        location ~ \.php$ {
            include php.conf;
        }
    }



Apache
---

    # Prevent file browsing
    Options -Indexes
    
    <IfModule mod_rewrite.c>
        RewriteEngine On
        #May be required to access sub-directories
        #RewriteBase /
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteRule . index.php [L]
    </IfModule>



Getting Help
---
You can read the wiki if you are looking for examples and read the inline-docs for more development information.

If you find a bug please report it on the issues page, but remember to include as much detail as possible, and what someone can do to re-create the issue.

Issues with plugins should be reported on the offending plugins homepage, same goes for themes.

Contributing
---
Help make geekcms.miuapps.com better by checking out the GitHub repository and submitting pull requests.

If you create a plugin please add it to the Wiki.

Plugins + Wiki
---
GeekCMS can be extended with a wide variety of plugins in order to add extra functionality, speed, or features.

Visit the [GeekCMS Wiki](https://github.com/geekcms.miuapps.com/GeekCMS/wiki) for docs, plugins, themes, etc...
