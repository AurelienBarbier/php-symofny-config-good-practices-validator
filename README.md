# PHP Good practices validators & checkers set (for symfony projects)

## Tools lists

### Main tools (events)
* **GrumPHP :** Used as pre-commit hook. Config file is available [here](https://github.com/WildCodeSchool/php-symofny-config-good-practices-validator/blob/master/grumphp.yml). [Github](https://github.com/phpro/grumphp)
* **Travis :** Used as hook on github when branch deployed on remote branches. Config file is available [here](https://github.com/WildCodeSchool/php-symofny-config-good-practices-validator/blob/master/.travis.yml). [Github](https://github.com/travis-ci)

### Secondary tools (validators)
* **PHP Code sniffer :** Used to check if PSRs are respected. Config file is available [here](https://github.com/WildCodeSchool/php-symofny-config-good-practices-validator/blob/master/phpcs.xml). [Github](https://github.com/squizlabs/PHP_CodeSniffer)
* **PHPStan :** Used to check if code is syntaxicaly correct according to PHP version requested. Config file is available [here](https://github.com/WildCodeSchool/php-symofny-config-good-practices-validator/blob/master/phpstan.neon). [Github](https://github.com/phpstan/phpstan)


## Details

### GrumPHP

Is configured to block commit if :

 - PSR according to code_sniffer are not respected,
 - PHP Syntaxe is wrong according to PHPStan.
 
 You can launch test without trying to commit with running `php ./vendor/bin/grumphp run`
 
 ### Travis.CI
 
 Is configured to set a pull request as refused on each push on a branch from local to remote.
 
 It tests :
 
 - if some forbidden (criticals or too heavy) files are presents like :
     - ./vendor
     - ./node_modules
     - ./.idea
     - ./.env.local
  
 - PSR according to code_sniffer are not respected,
 - PHP Syntaxe is wrong according to PHPStan.
   
 - HTML [validator](https://github.com/svenkreiss/html5validator#integration-with-travisci)
     
### PHP Code_sniffer

PHPCS is configured to :

 - check PSR2
 - check bin, config, src and tests folders,
 - ignores migrations folder and symfony Kernel.php file.
 
### PHP Stan

Is configured to follow directives from [PHPStan Symfony Framework extensions and rules](https://github.com/phpstan/phpstan-symfony)

## More tests would be great

* **W3C Validator :** A tool to check if pages are ok with W3C standard. Does-it exists ?
* **SCSS Validator/checker :**  Need to compile scss with node.js to find if errors found on build.
