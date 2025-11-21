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

## Update the repo

### Update the framework

Most updates require you to manually update configuration files like `app/Config/App.php` or `app/Config/Filters.php`, the easiest way to update this test project is to start over.
1. Delete all the files from the framework: **make sure you're in the project directory**
```bash
# will delete everything except for README.md, .gitignore and the .git (the only two file that is not from the framework)
find . -maxdepth 1 ! -name 'README.md' ! -name '.gitignore' ! -name '.git' ! -name '.' -exec rm -rf {} +
```
2. Create a new project:
```bash
composer create-project codeigniter4/appstarter project-root
```
3. Copy the contents of the directory in which you created the app to the root dir:
```bash
rsync -av --exclude='README.md' --exclude='.gitignore' --exclude='.git' project-root/ ./
```
4. Delete the directory in which you created the app:
```bash
rm -rf project-root/
```

### update tarballs

#### Database tarball (`db.sql.tar.gz`)
The database tarball contains the output of running migrations on a fresh CodeIgniter 4 install (creates an empty migrations table).

To create/update:
```bash
# Run migrations to create the database structure
php spark migrate

# Export the database (adjust credentials as needed)
mysqldump -u root -p db > db.sql

# Create the tarball
tar -czf db.sql.tar.gz db.sql

# Clean up
rm db.sql
```

#### Files tarball (`files.tar.gz`)
The files tarball contains the readme.md and welcome page assets used in ddev/ddev tests.

To create/update:
```bash
tar -czf files.tar.gz files
```

**Note:** These tarballs are used by the automated tests in the main ddev/ddev repository.