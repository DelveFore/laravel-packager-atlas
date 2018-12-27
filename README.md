# Laravel Packager Atlas 
Foundational Laravel project example for building Laravel packages quickly using the Artisan tools [Packager](https://github.com/Jeroen-G/laravel-packager) and [Packager Hermes](https://github.com/DelveFore/laravel-packager-hermes)

This is helpful for companies and teams needing build modules and packages within their organization or for the open-source community

The design of this project is to create and publish packages. As such, add NOTHING to `app/` and hence why the directory is ignored by `git`

## Setup
### option 1 
Either use this template means it comes with some "best practices" like ignoring `app/` directory
```bash
$ composer create-project delvefore/laravel-packager-atlas
$ composer install
$ cp .env.example .env
```

## option 2 
...or start from scratch
```bash
$ laravel new my-packager-atlas
$ composer require jeroen-g/laravel-packager --dev
$ composer require delvefore/laravel-packager-hermes --dev
$ echo 'packages/' >> .gitignore
$ echo 'app/' >> .gitignore 
```

## Usage
### First Time Package
_For instructional purposes, the vendor name I'm using is MyVendor and the package is MyPackage. I'm referencing Github.com for instructional purposes too._

**1** Create the repository in your Github (e.g. `https://github.com/MyVendor/my-package`) 

**2** Then create package
```bash
$ php artisan packager:new MyVendor MyPackage --i
```

**3**
Change naming and other information in `composer.json`

**4**
If you're building an HTTP API or Web UI, make sure to update the appropriate `routes/` file.

**5** Publish the package
```bash
$ php artisan packager:publish MyVendor MyPackage https://github.com/MyVendor/my-package --i
```
Making it available in Git

**6** Remove the package and then `git` the package
The package is now in Github, so let's remove and then get the package from Github
```bash
$ php artisan packager:remove MyVendor MyPackage
$ php artisan packager:git https://github.com/MyVendor/my-package MyVendor MyPackage
```
During development of new features to the package, you can use `--branch=mybranch` at the end of the last command to checkout from the branch

**7**
Now you can make modifications in your package locally and then use git as normal
```bash
$ cd package/MyVendor/MyPackage
$ git commit 
```
 
