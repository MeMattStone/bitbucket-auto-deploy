# BitBucket Auto-Deploy for ServerPilot

Deploy your repositories automatically from BitBucket to ServerPilot apps. This script can be easily modified to suit most LAMP environments, not just ServerPilot.

## Getting Started

These instructions will help you get this script deployed on a live system and the relevant webhook setup in BitBucket.

### Prerequisites

What you need to install the script and how to set it up

```
ServerPilot Server with an app setup and it's SFTP credentials
BitBucket account with a repository to deploy from
```

### Compatibilty

This script has been fully tested with ServerPilot using the following versions of PHP:

5.6, 7.0, 7.1, 7.2, 7.3

### Installing

By default this script will deploy to your app root directory (e.g. /srv/users/<sp_username>/apps/<sp_appname>), this is ideal for applications such as Laravel where the application files sit above the public folder that the web server has set as its document root. There is an option in the script to deploy directly to the public folder or you could even change this to a deeper path such as a WordPress theme directory (e.g. /srv/users/<sp_username>/apps/<sp_appname>/public/wp-content/themes).

Once you've decided where you repository contents will be deployed to open a terminal window, cd to that location and run the following command to create the hidden repo directory where our deployments will be cached:

```
mkdir -p .repo
```
The only file you need from this repository is bitbucket-deploy.php, download it directly from source, copy it to your public directory within your app (it needs to be in this location in order for BitBucket webhooks to connect to it) and then using your favourite terminal editor modify the following lines to suit your deployment:

```
/* ServerPilot app details */
$sp_user_name = 'serverpilot';
$sp_app_name = 'example';

/* Branch you want to deploy from */
$branch_to_deploy = 'master';

/* Deploy to public directory only? (by default we deploy to the app directory) */
$deploy_to_public = false;

/* Run composer after deploy to update packages? */
$run_composer = true;

/* Run custom commands after deploy? */
$run_custom_commands = false;

/* Add your custom shell commands to run here and change run_custom_commands to true */
$custom_commands = '';
```

That should be all you need to edit but on custom setups you may need to modify some of the paths to suit your needs.

## License

This project is licensed under the GPLv3 License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Adding soon...
