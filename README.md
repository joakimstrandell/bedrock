# [Bedrock Fork](https://roots.io/bedrock/)
Bedrock is a modern WordPress stack that helps you get started with the best development tools and project structure. Much of the philosophy behind Bedrock is inspired by the [Twelve-Factor App](http://12factor.net/) methodology.

For documentation on Bedrock please visit the official [Bedrock site](https://roots.io/bedrock/docs/installing-bedrock/).

## Forked Changes

* Removed unneeded files and folders.
* Updated composer.json with default plugins.
* Added premium plugins that can't be installed via composer.

## Requirements

* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
* WP-CLI (Optional) - [Install](http://wp-cli.org/#installing)

## Installation

1. Clone the git repo to your sites folder.

	```
	git clone https://github.com/joakimstrandell/bedrock
	```

2. Install PHP dependencies from the project root.

	```
	composer install
	```

3. Copy `.env.example` to `.env` and update environment variables:

	* **DB_NAME** - Database name
	* **DB_USER** - Database user
	* `DB_PASSWORD` - Database password
	* `DB_HOST` - Database host
	* `WP_ENV` - Set to environment (`development`, `staging`, `production`)
	* `WP_HOME` - Full URL to WordPress home (http://example.com)
	* `WP_SITEURL` - Full URL to WordPress including subdirectory (http://example.com/wp)
	* `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT`

	You can automatically generate the security keys (assuming you have wp-cli installed locally):
	
		wp package install aaemnnosttv/wp-cli-dotenv-command
		wp dotenv salts regenerate

	Or, you can cut and paste from the [Roots WordPress Salt Generator](https://roots.io/salts.html).

4. Set your site vhost document root to `/path/to/site/web/`.

5. Access WP admin at `http://example.com/wp/wp-admin`.

## Plugins and Core
New plugins should always be installed and tested on your development machine first. To install plugins available in the public [WordPress Packagist](https://wpackagist.org/) you should use Composer. **Always avoid installing plugins via WP Admin or any other graphical user interface!**

	composer require wpackagist-plugin/plugin-name

Premium plugins are added to the repository manually, note that you need to add the plugin folder to `.gitignore` so that the plugin is tracket by git and added to the repository.

When a new plugin have been **installed**, **updated** and **tested** on your **development machine**, commit all changes and push to the projects shared respository. After that you can pull changes to Staging and run `composer install`. If tested OK on Staging you can pull changes to Live and run `composer install`.

### Updating without Composer
If you update plugins and core via the WP Admin (or any other user interface like Inifite WP), you must update the composer.json file on your development machine and push changes to the projects shared respository. After that you should also pull those changes to Staging and Live.