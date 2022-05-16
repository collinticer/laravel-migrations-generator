# Laravel Migrations Generator

Generate Laravel Migrations from an existing database, including indexes and foreign keys!

This package is cloned from https://github.com/kitloong/laravel-migrations-generator with only a minor addition to support a `--skip-indices` option which prevents columns from having any index related eloquent specifications and without any foreign key constraints between table columns. Our use-case required this addition to support a legacy/archived MSSQL database that was being converted to MySQL. To make the transition easier, we removed calls to any index related functions.

## Use

Simply run your `php artisan` command as specified at https://github.com/kitloong/laravel-migrations-generator and include the new `--skip-indices` option.

Example:

`php artisan migrate:generate --tables="DBA.Accounts" --skip-views --skip-indices`

## Additional Read me

The rest of the readme is provided as is from the original project - [kitloong/laravel-migrations-generator/README.md](./original%20README.md)