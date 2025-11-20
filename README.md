# test-codeigniter4
Used by automated tests to test CodeIgniter 4 installation

This repo was created with a `composer create-project` using the official CodeIgniter 4 installation method:
```
composer create-project codeigniter4/appstarter test-codeigniter4
```

For more information, see the [CodeIgniter 4 Installation Guide](https://codeigniter.com/user_guide/installation/installing_composer.html#id10).

## DDEV Configuration

```
ddev config --name=testpkgcodeigniter4 --project-type=codeigniter --docroot=public
```