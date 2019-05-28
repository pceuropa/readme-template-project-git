# Readme template for project on Git

DIRECTORY STRUCTURE
-------------------

      assets/             contains assets definition
      commands/           contains console commands (controllers)
      config/             contains application configurations
      controllers/        contains Web controller classes
      mail/               contains view files for e-mails
      models/             contains model classes
      runtime/            contains files generated during runtime
      tests/              contains various tests for the basic application
      vendor/             contains dependent 3rd-party packages
      views/              contains view files for the Web application
      web/                contains the entry script and Web resources



REQUIREMENTS
------------
PHP 5.4.0+
Composer
Framework Yii2
Rabbit MQ

INSTALATION
------------

```
sudo apt-get install software-properties-common
composer update
```

#Edit the file 'app/config/db.php' with real data, for example:
```php
return [
    'class' => 'yii\db\Connection',
    'dsn' => 'mysql:host=localhost;dbname=telemetry',
    'username' => 'root',
    'password' => '1234',
    'charset' => 'utf8',
];

```

```
sudo chown :www-data -R .
sudo chmod 770 web -R

sudo cp nginx/* /etc/nginx
#edit /etc/nginx/default
sudo service nginx restart

#create table user
php yii migrate/up --migrationPath=@app 

#create Rules system
php yii migrate/up --migrationPath=@yii/rbac/migrations

#create super user
./yii user/create

#create rules and role and assign rule admin to user id 1
./yii user/create-roles

#caching
php yii migrate/up --migrationPath=@yii/caching/migrations
```


**NOTES:**
- App won't create the database for you, this has to be done manually before you can access it. In manual of
  telemetry-backend you can see how create the database.
- Check and edit the other files in the `config/` directory to customize your application as required.


TESTING
-------
Tests can be executed by running
```
./test
```
