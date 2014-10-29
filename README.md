# Apache PHP (`apache-php`)

**Part of the BAS Ansible Role Collection (BARC)**

Installs the PHP module for Apache

## Overview

* Installs Apache-PHP module package
* Explicitly enables the `mcrypt` module (others are auto-enabled) for the apache environment
* Configures the `php.ini` file for the Apache interface.

## Author

[British Antarctic Survey](http://www.antarctica.ac.uk) - Web & Applications Team

Contact: [basweb@bas.ac.uk](mailto:basweb@bas.ac.uk).

## Availability

This role is designed for internal use but if useful can be shared publicly.

## License

[Open Government Licence V2](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/)

## Requirements

### BAS Ansible Role Collection (BARC)

* `apache`
* `php`

## Variables

### PHP interface `.ini` configuration (CLI, apache, etc.)

#### Overview

See this section in the `php` role for an overview of how PHP `.ini` files are managed.

This role essentially adds an additional interface.

Note: In addition to the variables listed below two variables from the main PHP role are used by tasks in this role, these are:

#### All interfaces

See this section in the `php` role for details of what these do.

#### Apache interface `apache2/php.ini`

See [here](http://php.net/manual/en/ini.php) for documentation.

* `php_apache_ini_default_options`
    * Default values for the Apache PHP implementation.
    * **Do not override this variable**, use `php_apache_ini_user_options` instead.
    * Structured as an array of items where each item consists of a section name string and array of options and values
        * `section`  
            * Name of section in ini file (e.g. "Error handling and logging")
        * `options` [array]
            * `option`
                * Name of option in ini file (e.g. "display_errors") 
            * `value`
                * Value for option in ini file (e.g. "On") 
    * Default: (see variable)
* `php_cli_apache_user_options`
    * Use to change values set in `php_cli_apache_default_options` or where you want to change an option for the PHP Apache interface.
    * Structured as an array of items where each item consists of a section name string and array of options and values
        * `section`  
            * Name of section in ini file (e.g. "Error handling and logging")
        * `options` [array]
            * `option`
                * Name of option in ini file (e.g. "display_errors") 
            * `value`
                * Value for option in ini file (e.g. "On")
    * Default: "[]  (empty array)" 

## Changelog

### 0.2.4 - October 2014

* Updating dependencies

### 0.2.3 - October 2014

* Adjusting role for inclusion in BARC

### 0.2.2 - September 2014

* Disabling X-Powered-By header

### 0.2.1 - September 2014

* Fixing `mcrypt` module loading

### 0.2.0 - August 2014

* Adopting new method of setting PHP ini config options using the ansible ini module
* This allows any config option to be set without first converting to an ansible variable
* Templating is now longer used as the ini file is modified directly
* Global config options (defined in main PHP role) that apply to all implementations (CLI, apache, etc.) and per-implementation option variables are used to reuse defaults efficiently
* Specific variables are provided to override any default (either global or implementation specific) options where needed without having to also replicate other default variables not being overridden

### 0.1.0 - June 2014

* Initial version
