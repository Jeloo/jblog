---
layout: post
title:  "How to get Mongo ODM working with PHP7"
date:   2016-10-10 01:54:36 +0300
categories: php php7 mongodb
---

Sometime I needed to use Mongo DB on new symfony 3 project. I decided to use PHP7
that is pretty stable yet. I tried to install [Symfony ODM bundle][doctrine-mongodb-bundle-docs], but
get a message telling that i have not installed mongo extension. I was surprised as i had installed it
within pecl. But it turned out that php 7 mongo extension is different. It's called **mongodb**. 
PHP 5 version's called **mongo**
I found [issue][mongodb-odm-issue] that describes issue like mine.
To my disappointment, i realized that currently Mongo ODM is useless for PHP 7.

__Attempted to load class "MongoId" from the global namespace.
  Did you forget a "use" statement?__

For example, on the [code][mongodb-odm-github-code] old ext-mongo classes are used everywhere.

Fortunately, I found the [doctrine blog post][mongodb-odm-release-note]. It tells that Doctrine ODM
is still not working with new extension natively yet, but [mongo extension adapter][mongodb-php-adapter]
solves this problem, defining old extension's classes.

[doctrine-mongodb-bundle-docs]: http://symfony.com/doc/current/bundles/DoctrineMongoDBBundle/index.html
[mongodb-odm-github-code]: https://github.com/doctrine/mongodb-odm/blob/master/lib/Doctrine/ODM/MongoDB/Id/AutoGenerator.php
[mongodb-odm-issue]: https://github.com/doctrine/mongodb-odm/issues/1234
[mongodb-odm-release-note]: http://www.doctrine-project.org/2016/02/16/doctrine-mongodb-odm-release-1.0.5.html
[mongodb-php-adapter]: https://github.com/alcaeus/mongo-php-adapter
