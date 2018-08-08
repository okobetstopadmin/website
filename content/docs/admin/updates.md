+++
title = "Updating BookStack"
description = "How to update BookStack to the lastest version"
date = "2017-01-01"
type = "admin-doc"
+++

Topadmin BookStack is updated regularly and is still in beta although we do try to keep the platform and upgrade path as stable as possible. The latest release can be found on [GitHub here](https://github.com/BookStackApp/BookStack/releases) and detailed information on releases is posted on the [BookStack blog here](https://www.bookstackapp.com/blog/tag/releases/).

**Before updating you should back up the database and any file uploads to prevent potential data loss**. <br>
Backup and restore documentation can be found [here](/docs/admin/backup-restore).

 Updating is currently done via Git version control. To update BookStack you can run the following command in the root directory of the application:

```bash
git pull origin release && composer install && php artisan migrate
```

This command will update the repository that was created in the installation, install the PHP dependencies using `composer` then run then update the database with any required changes.

In addition, we recommend clearing the cache after an update -

```bash
php artisan cache:clear
php artisan view:clear
```

Check the below list for the version you are updating to for any additional instructions.


## Version Specific Instructions

#### Updating to v0.19 or higher

Version v0.19 needs the following requirement change:

* Minimum required version of PHP has changed from 5.6.4 to 7.0.0.

#### Updating to v0.18 or higher

Version v0.18 introduced a commenting system. After updating you should check the permissions for all roles if you'd like to enable comments for your users.

#### Updating to v0.13 or higher

The v0.13 release contained some new features and updates which change the requirements of BookStack.

* Minimum required version of PHP has changed from 5.5.9 to 5.6.4.
  Upgrade your PHP version if below 5.6.4.
* PHP-Tidy extension is now required.
  - On Ubuntu 16.04 this can be installed via `sudo apt install php7.0-tidy`.
  - On Ubuntu 14.04 (Using the defauly PHP option) this can be installed via `sudo apt-get install php5-tidy`.
* Page attachments will be stored in the `storage/uploads` folder (Unless you use Amazon S3). This folder will be created on update. Ensure your webserver has write permissions for this folder.
