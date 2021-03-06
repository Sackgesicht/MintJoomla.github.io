---
layout: doc
title:  "Migration from Emerald 9 or Mighty Membership"
date:   2013-07-01 12:30:30
tags: setup
---

Emerald 9 has completely new DB structure. Thus simple update of extension will work. You have to migrate. Amd Emerald out of the box has migration plugin for Emerald 8 and Mighty membership.

## Step 1

<div class="alert alert-error">This is most crucial step. Please make backup of your Joomla DB before you proceed.</div>

Delete Emerald 8 or Mighty Membership extension. But be sure, `_jcs_plans` and `_jcs_user_subscr` tables are not deleted. For that FTP your site to `administrator/components/com_[emerald|jcs]/sql/uninstall.utf8.php` and delete from there.

    DROP TABLE IF EXISTS `#__jcs_plans`;
    DROP TABLE IF EXISTS `#__jcs_user_subscr`;

This way, when you uninstall Emerald or Mighty Membership, those tables will not be deleted.

Now you can safely uninstall Emerald or Mighty Membership.

## Step 2

Update your Joomla to version 3. Either you update from Joomla 1.5 or Joomla 2.5 the process is the same. Read [Joomla wiki](http://docs.joomla.org/How_do_I_upgrade_from_Joomla!_1.5_to_3.x%3F) for more details. You have to though update process to safely transfer all your users and keep their user IDs that are bounded to subscriptions.

## Step 3

When you updated to Joomla 3 series and it is up and running, and you can access backend and frontend, you may go and install **Emerald 9**. Install and set it up.

For more details on that read Emerald [quick start](/en/emerald/emerald-quick-start/).

## Step 4

Now open Emerald dashboard/control panel and you will find Import section there.

![](/assets/img/screenshots/em-imp-cp.png)

Open import and you will see _Emerald 8_ importer. This one works as good for Mighty membership since DB structure is the same for both.

![](/assets/img/screenshots/em-imp-emr.png)

How click import button.

![](/assets/img/screenshots/em-imp-last.png)

There is one parameter. If you do not want to import subscriptions that already ended you can turn it on. But we recommend to import all subscription for analytics purpose.

## Step 5

First edit group that was created by importer. At least one group have to be created for Emerald to function. Name it as you want.

Now you have to edit all your plans and configure it. Since DB is completely different, plans was created but empty. We cannot migrate plans options as it is stored in very special way.

Edit all plans and set price, period, restriction rules and configure gateways.

That is it. You have just finished hassle free migration.

