# test-shopware6
Used by automated tests to test shopware6 installation

This repo was created with a `composer create-project` using the techniques at https://developer.shopware.com/docs/guides/installation/template.html and https://ddev.readthedocs.io/en/latest/users/quickstart/#shopware

`ddev config --name=testpkgshopware6 --project-type=shopware6 --docroot=public`

Demo data was installed with the Admin Settings->System->First Run Wizard.

Database db tarball (not db.sql.gz) was created with
```
ddev export-db --gzip=false --file=.tarballs/db.sql && tar -czf .tarballs/shopware6_db.sql.tar.gz -C .tarballs db.sql
```

Files tarball was created with
```
cd public/media && tar -czf ../../.tarballs/shopware6_files.tgz .
```