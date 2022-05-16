# Laravel Migrations Generator

Generate Laravel Migrations from an existing database, including indexes and foreign keys!

<<<<<<< Updated upstream
This package is cloned from https://github.com/Xethron/migrations-generator and updated to support Laravel 5.6 and above, with a lot of feature improvements.

## Supported Database

Currently, Generator support generate migrations from:

- [x] MySQL
- [x] PostgreSQL
- [x] SQL Server

## Version Compatibility

|Laravel|Version|
|---|---|
|8.x|5.x|
|7.x|5.x|
|6.x|5.x|
|5.8.x|5.x|
|5.7.x|5.x|
|5.6.x|5.x|
|5.5 and below|https://github.com/Xethron/migrations-generator|

## Install

The recommended way to install this is through composer:

```bash
composer require --dev "kitloong/laravel-migrations-generator"
```

### Laravel Setup

Laravel will automatically register service provider for you.

### Lumen Setup

Auto-discovery is not available in Lumen, you need some modification on `bootstrap/app.php`.

#### Enable facade

Uncomment the following line.

```
$app->withFacades();
```

#### Register provider

Add following line into the `Register Service Providers` section.

```
$app->register(\MigrationsGenerator\MigrationsGeneratorServiceProvider::class);
```

## Usage

To generate migrations from a database, you need to have your database setup in Laravel's config (`config/database.php`).

To create migrations for all the tables, run:

```bash
php artisan migrate:generate
```

You can specify the tables you wish to generate using:

```bash
php artisan migrate:generate --tables="table1,table2,table3,table4,table5"
```

You can also ignore tables with:

```bash
php artisan migrate:generate --ignore="table3,table4,table5"
```

Laravel Migrations Generator will first generate all the tables, columns and indexes, and afterwards setup all the foreign key constraints.

So make sure you include all the tables listed in the foreign keys so that they are present when the foreign keys are created.

You can also specify the connection name if you are not using your default connection with:

```bash
php artisan migrate:generate --connection="connection_name"
```

### Squash migrations

By default, Generator will generate multiple migration files for each table. 

You can squash all migrations into a single file with:

```bash
php artisan migrate:generate --squash
```

### Options

Run `php artisan help migrate:generate` for a list of options.

|Options|Description|
|---|---|
|-c, --connection[=CONNECTION]|The database connection to use|
|-t, --tables[=TABLES]|A list of Tables or Views you wish to Generate Migrations for separated by a comma: users,posts,comments|
|-i, --ignore[=IGNORE]|A list of Tables or Views you wish to ignore, separated by a comma: users,posts,comments|
|-p, --path[=PATH]|Where should the file be created?|
|-tp, --template-path[=TEMPLATE-PATH]|The location of the template for this generator|
|--date[=DATE]|Migrations will be created with specified date. Views and Foreign keys will be created with + 1 second. Date should be in format suitable for `Carbon::parse`|
|--table-filename[=TABLE-FILENAME]|Define table migration filename, default pattern: `[datetime_prefix]\_create_[table]_table.php`|
|--view-filename[=VIEW-FILENAME]|Define view migration filename, default pattern: `[datetime_prefix]\_create_[table]_view.php`|
|--fk-filename[=FK-FILENAME]|Define foreign key migration filename, default pattern: `[datetime_prefix]\_add_foreign_keys_to_[table]_table.php`|
|--default-index-names|Don\'t use db index names for migrations|
|--default-fk-names|Don\'t use db foreign key names for migrations|
|--use-db-collation|Follow db collations for migrations|
|--skip-views|Don\'t generate views|
|--squash|Generate all migrations into a single file|

## Thank You
=======
This package is cloned from https://github.com/kitloong/laravel-migrations-generator with only a minor addition to support a `--skip-indices` option which prevents columns from having any index related eloquent specifications and without any foreign key constraints between table columns. Our use-case required this addition to support a legacy/archived MSSQL database that was being converted to MySQL. To make the transition easier, we removed calls to any index related functions.
>>>>>>> Stashed changes

## Use

Simply run your `php artisan` command as specified at https://github.com/kitloong/laravel-migrations-generator and include the new `--skip-indices` option.

Example:

`php artisan migrate:generate --tables="DBA.Accounts" --skip-views --skip-indices`

## Additional Read me

The rest of the readme is provided as is from the original project - [kitloong/laravel-migrations-generator/README.md](./original%20README.md)