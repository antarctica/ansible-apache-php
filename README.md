# Apache PHP (`apache-php`)

**Part of the BAS Ansible Role Collection (BARC)**

Installs the PHP module for Apache

## Overview

* Installs PHP Apache module
* Explicitly enables the `mcrypt` module (others are auto-enabled) for the Apache SAPI
* Configures the `php.ini` file for the Apache SAPI.

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

* `apache`
* `php`

### Variables

#### PHP SAPI configuration (CLI, apache, etc. `.ini` configuration)

##### Overview

This role essentially adds an additional SAPI.

See this section in the `php` role for an overview of how PHP SAPI `.ini` files are managed.

##### All interfaces

See this section in the `php` role for details of what these do.

##### Apache SAPI `apache2/php.ini`

See [here](http://php.net/manual/en/ini.php) for documentation.

* `php_apache_ini_default_options`
    * Default values for the Apache PHP SAPI.
    * **Do NOT override this variable**, use `php_apache_ini_user_options` instead.
    * Structured as an array of items where each item consists of a section name string and array of options and values
        * `section`  
            * Name of section in INI file (e.g. "Error handling and logging")
        * `options` [array]
            * `option`
                * Name of option in INI file (e.g. "display_errors") 
            * `value`
                * Value for option in INI file (e.g. "On") 
    * Default: (see variable)
* `php_cli_apache_user_options`
    * Use to change values set in `php_cli_apache_default_options` or where you want to change an option for the PHP Apache interface.
    * Structured as an array of items where each item consists of a section name string and array of options and values
        * `section`  
            * Name of section in INI file (e.g. "Error handling and logging")
        * `options` [array]
            * `option`
                * Name of option in INI file (e.g. "display_errors") 
            * `value`
                * Value for option in INI file (e.g. "On")
    * Default: "[]  (empty array)" 

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) workflow is used to manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* (where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2015 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.