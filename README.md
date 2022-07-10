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
# set admin theme
$ drush -y then gin && drush -y thun olivero
$ drush -y cset system.theme admin gin && drush -y cset system.theme default gin
$ drush -y en gin_login gin_toolbar
$ drush -y cex
# https://next-drupal.org/learn/preview-mode/bearer
# /admin/people/roles -- 1. Create Role
$ drush role:create next_js_site 'Next.js Site'
# /admin/people/permissions -- 2. Assign Permissions
$ drush role:perm:add next_js_site 'bypass node access,issue subrequests,access user profiles'
# /admin/people/create -- 3. Create User
$ drush ucrt sknk-dev --mail=sknk-dev@users.noreply.github.com --password=letmein
$ drush urol "next_js_site" sknk-dev
$ drush -y cex
# /admin/config/people/simple_oauth -- 4. Generate keys
$ mkdir keys && chmod 777 keys
# /admin/config/services/consumer/add -- 5. Create Consumer
# consumer_nextjs_site:
# - uuid
# - secret
```

Starter does not build because of Type error #245
https://github.com/chapter-three/next-drupal/issues/245

https://gist.github.com/shadcn/23d2cff86eb68836774f877a3ecc88a3
