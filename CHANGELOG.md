# Apache PHP (`apache-php`) - Changelog

## 0.2.7 - March 2015

* Removing duplicate config option defined in upstream role

## 0.2.6 - March 2015

* Correcting variable conversion

## 0.2.5 - December 2014

* Preparing role for public release

## 0.2.4 - October 2014

* Updating dependencies
* Preparing for public release

## 0.2.3 - October 2014

* Adjusting role for inclusion in BARC

## 0.2.2 - September 2014

* Disabling X-Powered-By header

## 0.2.1 - September 2014

* Fixing `mcrypt` module loading

## 0.2.0 - August 2014

* Adopting new method of setting PHP ini config options using the ansible ini module
* This allows any config option to be set without first converting to an ansible variable
* Templating is now longer used as the ini file is modified directly
* Global config options (defined in main PHP role) that apply to all implementations (CLI, apache, etc.) and per-implementation option variables are used to reuse defaults efficiently
* Specific variables are provided to override any default (either global or implementation specific) options where needed without having to also replicate other default variables not being overridden

## 0.1.0 - June 2014

* Initial version
