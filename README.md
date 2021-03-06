# Zf3Php7Recaptcha - A ZF3 Module for Google ReCaptchaV2 

Zf3Php7Recaptcha is forked by [zf2-recaptcha](https://github.com/malganis93/BrlReCaptcha) features.


## Installation 
### with composer
Just add the following line to your requirements:
```json
"nocvp/zf3-php7-recaptcha-v2": "dev-master"
```
and run
```bash
php composer.phar update
```

Since there are problems with the SSL-Cert if you use Adapter\Socket, please install php-curl! 

Then activate the module in your application.config.php :

    ```php
    return array(
        'modules' => array(
            // ...
            'Zf3Php7Recaptcha',
        ),
        // ...
    );
    ```


## Get your private-key 
To use this service, you have to register at [Google ReCaptcha](https://www.google.com/recaptcha) using your Google-Account.

## Usage 
### with Zend\From
This module works similar as [ZendFrameworkService\ReCaptcha](https://github.com/zendframework/ZendService_ReCaptcha). 

Just add the following lines to your form creation:
```
$element = new \Zend\Captcha\Captcha('g-recaptcha-response');
$element->setCaptcha(new Zf3Php7Recaptcha\ReCaptcha(array('private_key' => 'YOUR_SECRET FROM GOOGLE', 'public_key' => 'YOUR_PUBLIC_KEY', 'theme' => 'dark')));
$form->add($element);

```
Important: The element has to be named g-recaptcha-response due to the reason that the JS from google creates this virtual input.

Remember to add this element to your validationChain as well.

Note: The theme parameter is not required. By default the light theme is used. 

It acts the same way as any other built-in captcha solution.
 
### with ServiceManager 
If you like to implement the view on your own, just use the Service\ReCaptchaService. It handles the whole communication between your code and the ReCaptcha API. 

```
$recaptcha = $serviceLocator->get('Zf3Php7Recaptcha\Service\ReCaptcha');

```

### other 

just look into the sources! It's pretty easy to understand.


## TODO  
* PHPUnit Tests are missing -> Will do this in the next couple of days
* some error handling is qnd
* better documentation 

## Questions? 
If you have any problems or questions regarding my code, please create an issue.
Since i'm using this module for my own projects i'm interested in keeping this up to date!
