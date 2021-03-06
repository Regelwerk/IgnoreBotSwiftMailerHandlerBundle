# RegelwerkIgnoreBotSwiftMailerHandler

Use this bundle to let the swift handler ignore all log entries from bot requests

**Highly unstable ATM!**

Installation
============

Step 1: Download the Bundle
---------------------------

Open a command console, enter your project directory and execute the
following command to download the latest stable version of this bundle:

```bash
$ php composer.phar require regelwerk/ignore-bot-swift-mailer-handler-bundle "master@dev"
```

This command requires you to have Composer installed globally, as explained
in the [installation chapter](https://getcomposer.org/doc/00-intro.md)
of the Composer documentation.

Step 2: Enable the Bundle
-------------------------

Then, enable the bundle by adding the following lines in the `app/AppKernel.php`
file of your project:

```php
<?php
// app/AppKernel.php

// ...
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            // ...

            new Vipx\BotDetectBundle\VipxBotDetectBundle(),
            new Regelwerk\IgnoreBotSwiftMailerHandlerBundle\RegelwerkIgnoreBotSwiftMailerHandler()
        );

        // ...
    }

    // ...
}
```

Step 3: Edit app/config/config.yml
----------------------------------

add the following line to the parameters section:

```
parameters:
  monolog.handler.swift_mailer.class: Regelwerk\IgnoreBotSwiftMailerHandlerBundle\Handler\IgnoreBotSwiftMailerHandler
```

And set the swift mail handler id:

```
regelwerk_ignore_bot:
    handler: main
```
This is the id under monolog:handlers: where the entry with type: swift_mailer is defined.

If you want to disable the bundle, just set

```
regelwerk_ignore_bot:
    enable: no
```
