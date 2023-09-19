---
title: "Managing apps"
lead: "Explains how to create and manage apps in Slingr."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "slingr-dev-portal"
toc: true
weight: 3 
---


{{< callout type="info" contend="" >}}
There is also a Slingr Free plan where instances are shared. Those are not meant for production.
{{< /callout >}}

Apps can be managed in the [Slingr Developer Portal](https://developer-portal.slingrs.io).
From there you will be able to manage apps, endpoints, organizations, handle developers permissions,
setup billing, see invoices, etc.

## Create a new app

To create a new app just click the `Create app from scratch` button in the `Home` section of Slingr.
/images/vendor/platform-ref/managing-apps/
![Create new app from Home](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/home_create_new_app.png)
![Create new app from Apps](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/apps_create_new_app.png)-->

<!--{% include note.html content="You can also create new apps from **Apps** section by clicking the **Create App** button" %}-->
{{< notes type="note">}}
You can also create new apps from <b>Apps </b>section by clicking the <b>create App</b> button
{{< /notes >}}

Then, you will be able to complete the following options:

- `Label`: this is a human-friendly name of your app. It can contain spaces and special characters.
  The label will be used in your app in different places, like the header or the title of the
  browser.
- `Name`: this is the internal name of your app. It's required and cannot contain spaces or special characters
  and it must be unique. It will be used as the subdomain of your app: `<app-name>.slingrs.io`.
<!--  {% include important.html content=" You won't be able to change the **name** of your app later." %} -->
{{< notes type="note">}}
You won't be able to change the <b>name</b> of your app later.
{{< /notes >}}
- `App owner`: You can choose to be the owner for the app or select an organization that you belong to.
- `Plan`: this is the plan your app will run on. You can choose between three different plans depending on your needs:
  - `Slingr Free`: this plan is free and it is useful to understand the platform and learn how to
    use it, however it is not suited for complex or production apps.
  - `Slingr Dev`: this is an isolated environment with a fixed price that allows developers have
    personal apps for a reasonable price. It has some limitations.
  - `Slingr Pro`: this is a usage-based plan meant for applications in production environments that needs dedicated resources and outstanding performance. There are no limitations with the **Slingr Pro** plan.

  You can see the full comparison in [Pricing and Billing](https://www.slingr.io/pricing).

- `Template`: you can choose to start from scratch, with an empty app, or you can choose one of the
  available templates. Here you will find global templates created by other people or you can
  also create your own templates. See [App templates](#app-templates) for more information.

  ![Choose template](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/create_app_templates.png)

  When you select a template, you might decide to make it linked by setting the flag `Linked`, which
  is only available if you select `Slingr Pro` as the plan. If this flag is set, the new app will be 
  linked to the template. This means that the new app will only have a production environment and 
  when changes are synced in the template app, those changes will be applied to this new app as well.
  If you don't set this flag, only a development environment will be created using the app
  template, but it will be completely independent from the original app, which means new
  changes in the template won't affect the new app and the other way around.
    
By default, when a new app is created, only the development environment (except that you are set
the `Linked` flag) is created with the selected plan.

<!--{% include tip.html content=""%}-->
{{< notes type="tip">}}
You can add a production environment later or change the plan if you need.
{{< /notes >}}

 
Additionally your developer account will be set as the admin and owner, as well as a developer for
the new app.

## General app settings

Once an app is created, you should be able to see :

- `Label`: this is a human-friendly name of your app that was provided during creation time. You
  can change the app's label at any time.
- `Description`: this is an internal description of your app. This field is for internal use or,
  if the app is a template, it will be used as the description of the template.
- `App logos`: these are the logo, favicon and background of the app. It will be used in different places like the `Developer portal`, in your app header, in the browser's title, etc. We suggest you to use a transparent background, but you are free to choose any.

![App logos](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_details_logos.png)

For any of these changes, as soon as you make them, will be applied.

## App environment settings

Apps can have 3 different environments:

- `Development`: this is the main environment that developers will use to make their changes. It's the **default environment**.
- `Staging`: this environment can be used as a buffer between development and production. Additionally,
  when you are in production and you need to fix something, this environment it's ideal to apply
  hotfixes in `Production` without syncing all the changes in `Development`.
- `Production`: this is the production environment your users will access. This environment does
  not have the builder component because you should never change your app directly in production.
  
By default a new app will only have `Development` environment, but you can easily add new ones as
you need them.

Then each app environment has the following settings:

![App environment details](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_environment_details_1.png)

- `Status`: indicates in which status the environment is. If the value is different than `Deployed`
  it could be that some maintenance work is going on (for example the platform is being upgraded) or
  there is a problem and you should contact support.
- `Version`: this is the current version your app is running on. We periodically release new updates
  to the platform and we automatically update apps when that's possible. If your app is behind, you
  will be able to manually trigger an update when you found it more convenient.
- `Instances`: this is the number of runtime instances for this environment. The more instances you
  have, the more requests and work your environment can handle, so this is a good way to scale your
  app. Keep in mind that more instances also mean more usage, so be sure you understand how [Pricing
  and Billing]({{site.baseurl}}/platform-pricing-and-billing.html) work in your plan.
  It could be that not all instances are available at all times, for example when you just added them
  or there is some maintenance work. In that case it will be shown how many instances are deployed
  and running out of the desired number of instances.
  Apart from the number of instances, you can also configure the size of each instance. You will
  need bigger instances as your app gets more complex. Don't worry, we will notify you if your instances are running out of resources. Here you should consider upgrading the size of your instance.
  The size available are:
  - `Small (1GB)`: this is the default size for apps. It is meant for small apps.
  - `Medium (2GB)`: this is for medium apps.
  - `Large (4GB)`: this is for big apps, which when there are many entities, views, listeners,
    endpoints, etc.

![App environment details](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_environment_details_2.png)

- `Database`: just adding more instances might not work to scale your app as there is a point where
  the database will be the bottleneck. When your reach that point (usually we try to size database
  based on data size so you know when to switch), you should update the database of the app environment
  from here. Please take a look at [Pricing and Billing]({{site.baseurl}}/platform-pricing-and-billing.html) 
  to understand how this will impact your invoice.
- `Custom domain`: by default you app will be available at `<appname>.slingrs.io`, however
  you can use your own domain as well, for example `myapp.com`. In order to do that you need to
  own the domain and have a valid SSL certificate. Just click on `Set your domain` and you will
  be asked to enter the domain and SSL certificate information.

There are a few cases that need changes in settings that deserve more attention:

### Scaling up and down your app

The way to scale your app is by adding more instances. How many instances you need depends on your 
app and the load it has, so it is hard to say how many users or API requests an instances can handle.

What we recommend is to watch out the response time of your app and add more instances when you see
it goes above your maximum desired value or when you see that the waiting time of background jobs
is growing. You can check those things in the app monitor.
 
Also keep in mind that adding more instances might not help if the database is the bottleneck. In
this case you should upgrade your database to take advantage of the additional instances. You can
check the [slows queries]({{<ref "/dev-reference/monitoring/database-and-files.md">}}) 
report in the app monitor to see if the database is being the bottleneck.

The same way you can add instances, you can remove them. When you do that some instances will be
gracefully stopped and undeployed until the desired number of instances is met.

### Changing the database

<!--{% include warning.html content="" %}-->
{{< notes type="warning">}}
Depending on the source and the target database type, changing the database could cause a downtime of your app.
{{< /notes >}}

If you are upgrading from a shared database to another shared database in most cases it won't mean
any downtime and the data size limit will be updated immediately. If it happens that we need to do
some migrations, we will notify and you should confirm before proceeding.

If you are upgrading from a database in shared servers to one in dedicated servers, a migration will
be needed and your app will be down during that time.

If you are upgrading from a database in dedicated servers to another database in dedicated servers,
migration can be done without any downtime.

Keep in mind that you will only be able to downgrade your database if the data size fits in the
new database type.

## Manage developers and admins

When you create an app, you automatically become the admin owner and a developer for it. However
you can add permissions to other developers to work in your app or give them admin permissions.

### Developers

![App developers](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_settings_developers.png) -->
![App developers](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_settings_add_developer.png)

In the `Developers` section of the app details you can add more developers by entering
the email associated to their developer accounts. Once you add a developer you can choose which
environments they will have access to.

When you give access to one environment, the developer will be able to use all components in it,
like runtime, builder and monitor, and a user will be created in the environment for that developer,
so if you go to the screen to manage users in that environment you will see the developer as a
user. These users will belong to the `Developers` group and cannot be modified (you can only assign
new groups, but cannot change password, name, etc.). They will be automatically managed and synced. 
For example if the developer changes its password, it will be updated in all apps.

One important thing about developer users is that permissions defined in the app won't affect
developers as they always have permissions for everything. The exception is when you assign groups
to the developer in that app. If you do so, the developer user will use those groups' permissions
by default.
 
If you need to test permissions while developing your app you should create other regular users,
assign groups to your developer user in that app, or use the `Switch groups` option available in
the user menu of the app runtime.

### Admins

![App admins](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_settings_admins.png)-->
![App admins](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_settings_add_admin.png)

<!--{% include note.html content="" %}-->
{{< notes type="note">}}
Admins are not allowed to use the app. If you want to, the admin should also be a developer.
{{< /notes >}}

In the `Admins` section of the details of the app you can indicate which developer accounts will
have permissions of admins over the app. Admins can do the following things:

- Add/remove developers
- Change general settings of the app
- Change settings of app environment

Also, there is only one admin that is also the owner of the app (by default the creator of the app).
The owner can do the following things:

- Add/remove admins
- Transfer ownership to another admin
- Sleep or wake up app
- Delete app

Ownership can be transferred by adding a new admin and then, after selecting that admin, click on
the button `Transfer ownership to this admin`.

## Sleeping and wake up

If your apps are not going to be used for a period, you can **Sleep** them. This way you can avoid charges while still
keeping your app. Later, if you need it again, you can wake it up and keep using it as usual.

This can be done by clicking the buttons `Sleep app` and `Wake up`.

![Sleep app](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/sleep_app.png)
![Wake up app](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/wakeup_app.png)

<!--{% include note.html content="" %}-->
{{< notes type="note">}}
This can only be done by the app owner.
{{< /notes >}}

## Add production environment

![Add prod environment](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_add_production_env.png)

When an app is created by default it only has a `Development` environment. We recommend to keep only
the development environment until you see the need for a `Production` environment. When that happens
you can easily add it by clicking the `Add production environment` button.

When you add a production environment it will be created based on your current development
environment. However keep in mind that **data won't be copied**. You should export and import records
from `Development` to `Production` if you need so.

Also, if you want developers to access the production environment you will need to explicitly set
permissions, even if they already had permissions for the development environment.

## Add staging environment

![Add staging environment](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_add_staging_env.png)

Once you have a development and a production environment, you might see the need for an additional
environment to work as a buffer between development and production. This is the `Staging` environment
and you can add it by clicking the `Add staging environment` button.

This environment is very useful for doing QA and also to do hotfixes of issues that show up in
production.

## Unlink app

If you created the app from a template with the `Linked` flag, the app will only have a production
environment and you won't be able to make changes. Instead changes are done in the template app and
synced to the clones.

![Unlink app](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/unlink_app.png)

If at some point you need to make changes in the app, you will need to unlink the app first. You can
do that by clicking on the button `Unlink` in the details of the app. When the app is unlinked a
`Development` environment is added to the app.

<!--{% include important.html content="" %}-->
{{< notes type="important">}}
You won't be able to link it again to the template, the apps will become independent from each other.
{{< /notes >}}

### Development environment in linked apps

There are cases where you need to make some changes to a linked app, but you don't want to unlink
it because you still want to get updates from the master app.

![Add development environment](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/add_development_env.png)

In these cases what you can do is add a development environment by clicking in `Add development environment`.
When you do this, how changes are synced will be changed. Please check the section
[Pushing and Syncing changes]({{< ref "/dev-reference/metadata-management/pushing-and-syncing.md">}}) for more details.

## Delete app

If you don't need an app any longer, you can delete the app. This will remove all instances as well
as the database, which means all data will be lost.

![Delete app](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/delete_app.png)

<!--{% include warning.html content="" %}-->
{{< notes type="warning">}}
This operation cannot be undone, so be careful.
{{< /notes >}}

<!--{% include note.html content="" %}-->
{{< notes type="note">}}
This can only be done by the app owner.
{{< /notes >}}
## App templates

![Make app a template](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/app_make_a_template.png)

If you want to make an app a template, you can do it so by setting the flag `Make this app a template`.
When this option is enabled your app will show up in the list of templates when creating new apps (only inside your
account).

## Cloning apps

![Clone app](https://maximiranda.github.io/slingrDoc/images/vendor/platform-ref/managing-apps/clone_app.png)

You can create a clone of your app by clicking the `Clone app` button. This will create a new app using the
same plan as the current app with the selected environment. Keep in mind that data will also be copied (up
to 1,000 records per entity).

<!--{% include tip.html content="" %}-->
{{< notes type="tip">}}
Clone your apps is useful when you want to test some changes in your app but you don't want to change anything.
{{< /notes >}}

