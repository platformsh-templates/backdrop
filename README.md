> [!WARNING]
> **This repository is no longer maintained by our internal teams.**  
> The template is provided *as is* and will not receive updates, bug fixes, or new features.  
> You are welcome to contribute on it or fork the repository and modify it for your own use.
> To deploy this template on [Upsun](https://www.upsun.com), you can use the command [upsun project:convert](https://docs.upsun.com/administration/cli/reference.html#projectconvert)
> on this codebase to convert the existing `.platform.app.yaml` configuration file to the [Upsun Flex format](https://docs.upsun.com/create-apps/app-reference/single-runtime-image.html).

# Backdrop for Platform.sh

This template deploys a Backdrop CMS site, with the entire site committed to Git.  It comes configured for MariaDB, the most popular database used with Backdrop.  It supports a quick web installation to configure the site.

Backdrop is a PHP-based CMS, originally forked from Drupal 7.

## Features

* PHP 8.1
* MariaDB 10.4
* Drush included
* Automatic TLS certificates

## Post-install

1. Run through the Backdrop installer as normal by visiting `<project url>/install.php`.  You will not be asked for database credentials as those are already provided.

2. Once Backdrop is fully installed, We strongly recommend switching to Redis-based caching.

## Customizations

The following changes have been made relative to Backdrop as it is downloaded from backdropcms.org.  If using this project as a reference for your own existing project, replicate the changes below to your project.

* The `.platform.app.yaml`, `.platform/services.yaml`, and `.platform/routes.yaml` files have been added.  These provide Platform.sh-specific configuration and are present in all projects on Platform.sh.  You may customize them as you see fit.
* The `/web/settings.platformsh.php` file contains Platform.sh-specific code to map environment variables into Backdrop configuration. You can add to it as needed.
* The `/web/settings.php` file has been customized to include the Platform.sh settings file.  It also will check for a `settings.local.php` file only if it's not running on Platform.sh.
* A patch has been included to support setting configuration values from `settings.php`.  This patch is based on an [existing PR](https://github.com/backdrop/backdrop/pull/2964) that is expected to be merged into a future version of Backdrop.  Once that happens the patch will no longer be necessary.

## References

* [Backdrop](https://backdropcms.org/)
* [PHP on Platform.sh](https://docs.platform.sh/languages/php.html)
