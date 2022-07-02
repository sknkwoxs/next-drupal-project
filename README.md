# next-drupal-project

FROM [drupal/recommended-project](https://github.com/drupal/recommended-project)

## install drupal project

```bash
# Just use this as template to create new repo and clone it.
# Check dependencies.
$ php -v && sqlite3 -version && composer -V
# $ mysql -V | psql -V

$ composer install
# Load env vars and check install options.
$ . scripts/env.sh && env | grep DRUSH
# Install site.
$ composer site-install
# Run web server.
$ composer start
# Uninstall site.
$ composer site-uninstall
```

## into the next-drupal

<https://next-drupal.org/learn/quick-start/install-drupal>

```bash
$ export $(grep -v '^#' .env | xargs) && composer start
$ composer require drupal/next
# add patches to composer.json
$ composer update -o
$ drush -y en next_jsonapi
# if got errors, uninstall pathauto, reinstall next_jsonapi
# $ drush -y pmu pathauto && drush -y en next_jsonapi && drush cr or ctrl+c && composer start
$ npx create-next-app -e https://github.com/chapter-three/next-drupal-basic-starter -y
$ composer require drush/devel && drush -y en devel_generate && drush genc 10 5
```
