# License
MIT License


# Requirements:

For example if your server distro is Ubuntu 20.04, you need to install the following items first

* NGINX (1.18.0, stock Ubuntu repo build using ```sudo apt install nginx```)
* MySQL (Ver 8.0.23, stock Ubuntu repo build ```sudo apt install mysql```)
* PHP (7.4.3, stock Ubuntu repo build ```sudo apt install php-fpm php-mysql```)
* npm v6.9.0 (use nvm: ```nvm install 6.9.0```)
  * 20210503 notes: use v.8.9.0 if there is problem on your system
* Composer 1.10.17

Detail steps for installing specific version (e.g. 1.10.17) of Composer:

```
curl -O "https://getcomposer.org/download/1.10.17/composer.phar"
chmod a+x composer.phar
sudo mv composer.phar /usr/local/bin/composer
```

Install the following packages for Laravel/Composer:

```sudo apt install zip unzip php7.4-zip```

```sudo apt install php7.4-common php7.4-bcmath openssl php7.4-json php7.4-mbstring php7.4-xml php7.4-gd php7.4-curl```

(Tip for Mac computer: you can install [Homebrew](https://brew.sh/) first and use it to install the required package. PLease note that the path are not the same as Ubuntu 20.04)


# Installation Steps


## Basic Steps

To begin with, please clone this repository to your local machine from the git


```git clone https://github.com/ldsstem/ldsk12_beta.git```

Go into the directory of the project source code

```cd ldsk12_beta```

Run the composer install command to install all the laravel dependency.

```composer install```

Please edit your own ```.env``` file and config the database setting (Change DB_DATABASE, DB_USERNAME, DB_PASSWORD to your MySQL settings)

```sudo cp .env.example .env```

Then run these 2 PHP artisan commands into to init and apply the laravel environment config:

```php artisan cache:clear```

```php artisan key:generate``` (this will update you .env file)

Run the migration to update your database:

```php artisan migrate```

Laravel Passport: create the encryption keys and clients:

```php artisan passport:install```

Install all the front end dependencies:

```npm install```

Run the npm build to apply the latest front code changes.

```npm run prod``` or ```npm run dev``` for dev build


## LDS on the server
LDS can be served on the NGINX Server.

Copy it to your WWW folder for production build, or put it anywhere and set it in NGINX server block configuration.
``` cp ldsk12_beta -rf /var/www ```

Set the NGINX server block for the LDS site, for example:

```sudo nano /etc/nginx/sites-available/lds```

Sample config:

```
server {
    listen 80;
    server_name lds.localhost www.lds.localhost;
    root /var/www/ldsk12_beta/public;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
        # for PHP-FPM listening on TCP port (e.g. on Mac), use the below line instead
        # fastcgi_pass 127.0.0.1:9000
        try_files $uri /index.php =404;
        fastcgi_index index.php;
        fastcgi_buffers 16 16k;
        fastcgi_buffer_size 32k;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        #fixes timeouts
        fastcgi_read_timeout 600;
        include fastcgi_params;
     }

    location ~ /\.ht {
        deny all;
    }
}
```

Remember to link it to enabled sites:

```sudo ln -s /etc/nginx/sites-available/lds /etc/nginx/sites-enabled/```

Optionally, disable the default NGINX site:

```sudo unlink /etc/nginx/sites-enabled/default```

Set the proper files owner for public and storage folder, for example:

```sudo chown -R www-data:www-data /var/www/ldsk12_beta/public```

```sudo chown -R www-data:www-data /var/www/ldsk12_beta/storage```

(You may also need to use ```chmod``` if you encounter permission issue)

At this point you may want to restart NGINX to apply any changes that is not loaded

```service nginx restart```



## Local Development

Besides, if you would like to develop in your own local enivironment

Go into the directory of the project source code

``` cd ldsk12_beta ```

In local development, you might run 

``` npm watch ```

to exam every changes in your front end

Serve LDS in your local machine via Laravel

``` php artisan serve ```


# Handle version changes
For each deployment to the production server, the version variable ```app_ver``` should be increased in the file ```config/app.php```. This also affected some Blade templates under ```resources/views/```, particularly make the loading of ```app.js``` depends on the version by this line:

```script.src = "/js/app.js?v=" + version;```

Please adjust it in your dev envirnoment if necessary when you find that JS does't update, but you may need to do a force/hard reload or clear cached files on your browser.

The following commands should be run for version upgrade with PHP/DB/JS changes (run all of them should have no negative effect):

```composer install```

```php artisan cache:clear```

```php artisan migrate```

```npm install```

```npm run prod```

Some features (e.g. Evidence on v2.3.5) might require web server to create folder and save file (uploaded by user on web) in the ```public\asset``` folder or its sub-folders, therefore you should run ```chown``` and/or ```chmod``` accordingly if you encounter problem like "500 internal server error" because of permission denied.

If there is still problem, by default Laravel would store logs at ```storage/logs/laravel.log``` and have detail stack trace.