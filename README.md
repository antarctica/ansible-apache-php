# Apache PHP (`apache-php`)

**Part of the BAS Ansible Role Collection (BARC)**

Installs the PHP module for Apache

## Overview

* Installs Apache-PHP module package
* Explicitly enables the `mcrypt` module (others are auto-enabled) for the apache environment
* Configures the `php.ini` file for the Apache interface.

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

* `apache`
* `php`

### Variables

#### PHP interface `.ini` configuration (CLI, apache, etc.)

##### Overview

See this section in the `php` role for an overview of how PHP `.ini` files are managed.

This role essentially adds an additional interface.

Note: In addition to the variables listed below two variables from the main PHP role are used by tasks in this role, these are:

##### All interfaces

See this section in the `php` role for details of what these do.

##### Apache interface `apache2/php.ini`

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

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](https://github.com/fzaninotto/Faker#formatters) workflow is used to manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* (where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2015 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.