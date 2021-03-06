Yii 2 API Template
============================

This is a a REST API template built using Yii2. This template use Yii2-Micro approach so it will be lightweight and easy to deploy.

Installation
------------
[1. Preparing application](preparing-application.md)

[2. Creating new environments](new-environments.md)

GENERAL INDICATIONS
-------------------

### i18n - Translating App Messages

The i18n configuration is set up using the instructions found at [Yii2 i18n](https://www.yiiframework.com/doc/guide/2.0/en/tutorial-i18n).
The i18n configuration file is located at ```<ProjectRoot>/messages/config-messages.php```

To extract your app messages you can do so using the [message command](https://www.yiiframework.com/doc/guide/2.0/en/tutorial-i18n#using-the-message-command).

```./yii message messages/config-messages.php```

To scan the tree 'sourcePath' to generate files default for labels used in the code  execute the following command 
```./yii message/extract @app/messages/config-messages.php ```

To change target lenguage for example to spanish use 
```Yii::$app->language = 'es';```


### Applying migrations

The migrations can be found in ```@console/migrations``` .  The initial migration named ```m130524_201442_init.php``` contains the user table creation script, including the following aditions to 
yii2 base user table:
```
id              string(36) - v4 UUID
access_token    string(32) - user access token
refresh_token   string(32) - used to refresh the access token
created_at      int(13) - Time of creation
updated_at      int(13) - Time of creation
created_by      string(13) - id of the user that created the record
updated_by      string(13) - id of the last user that updated the record
```
To apply the migrations execute the command
```./yii migrate```

To revert the migrations execute the command 
```./yii migrate/down```

### Congiguration of tests
install codeception 
``composer require codeception/codeception --dev``

create folder named `tests` in your project after execute follow command
```./vendor/bin/codecept bootstrap```

to active test to api execute
``` ./vendor/bin/codecept generate:suite api ```

for create a new test of api execute 
``` ./vendor/bin/codecept generate:cest api CreateUser```

create unit test execute the follow command
``` ./vendor/bin/codecept generate:test unit Example```

create advanced tests execute 
```./vendor/bin/codecept generate:cest suitename CestName ```


for execute all tests execute
```./vendor/bin/codecept run ```

for execute only the unit test execute
``` ./vendor/bin/codecept run unit ```

run test of only file
``` ./vendor/bin/codecept run tests/api/UserCest.php```