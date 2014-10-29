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

## Branches

This project uses three permanent branches with the *Git Flow* branching model managing the interaction between branches.

* **Develop:** unstable, potentially non-working but most current version of roles. Bug fixes and features interact with this branch only.
* **Master:** stable, tested, working version of role with full documentation. Releases and hot fixes mainly interact with this branch. This branch should when consuming roles internally.
* **Public:** equivalent to the *master* branch, but available externally. Some configuration details may be altered or features removed to make available for public release.

## Testing

Manual testing is performed for all roles to ensure roles achieve their aims and this forms a prerequisite task for merging changes into the *master* and *public* branches.
Wherever possible testing is as complete as possible meaning tasks such as downloading dependencies are performed as part of each test.

## Issues

Please log issues to the [BAS Web and Applications Team](https://jira.ceh.ac.uk/browse/BASWEB) project in Jira, within the *Project - Ansible Roles* component.

If outside of NERC please get in touch to report any issues.

## Contributions

We have no formal contribution policy, if you spot any bugs or potential improvements please submit a pull request or get in touch.

These roles are used for internal projects which may dictate whether any contributions can be included.

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
* Preparing for public release

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
