# [Bedrock Fork](https://roots.io/bedrock/)
Bedrock is a modern WordPress stack that helps you get started with the best development tools and project structure. Much of the philosophy behind Bedrock is inspired by the [Twelve-Factor App](http://12factor.net/) methodology.

For documentation on Bedrock please visit https://roots.io/bedrock/docs/installing-bedrock/

## Changes in Fork

* Removed unneeded files and folders.
* Updated composer.json with default plugins.

## Requirements

* PHP >= 5.6
* Composer - [Install](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)
* WP-CLI (Optional) - [Install](http://wp-cli.org/#installing)

## Installation

1. Clone the git repo into a new folder for WordPress. In the command line example below we clone the repository into a folder named public.

  `git clone https://github.com/joakimstrandell/bedrock public`

2. Copy `.env.example` to `.env` and update environment variables:

  * `DB_NAME` - Database name
  * `DB_USER` - Database user
  * `DB_PASSWORD` - Database password
  * `DB_HOST` - Database host
  * `WP_ENV` - Set to environment (`development`, `staging`, `production`)
  * `WP_HOME` - Full URL to WordPress home (http://example.com)
  * `WP_SITEURL` - Full URL to WordPress including subdirectory (http://example.com/wp)
  * `AUTH_KEY`, `SECURE_AUTH_KEY`, `LOGGED_IN_KEY`, `NONCE_KEY`, `AUTH_SALT`, `SECURE_AUTH_SALT`, `LOGGED_IN_SALT`, `NONCE_SALT`

  If you want to automatically generate the security keys (assuming you have wp-cli installed locally) you can use the very handy [wp-cli-dotenv-command][wp-cli-dotenv]:

      wp package install aaemnnosttv/wp-cli-dotenv-command

      wp dotenv salts regenerate

  Or, you can cut and paste from the [Roots WordPress Salt Generator][roots-wp-salt].

3. Set your site vhost document root to `/path/to/site/web/`.

4. Access WP admin at `http://example.com/wp/wp-admin`.
