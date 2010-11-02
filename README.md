**Deploying WordPress with Capistrano using wp-cap**

Here is the steps:

1. Clone [wp-cap](http://github.com/adamhunter/wp-cap/) to a directory, e.g. my-wordpress `git clone git://github.com/adamhunter/wp-cap.git my-wordpress`
2. Copy your WordPress files to my-wordpress/public so you will have 

    my-wordpress/
    ├── config
    └── public
        ├── wp-admin
        ├── wp-content
        └── wp-includes

3. You want to point your WordPress domain to my-wordpress/public
4. Move my-wordpress/public/wp-config-sample.php to my-wordpress/config/wp-config-sample.php

    my-wordpress/
    ├── Capfile
    ├── config
    │   ├── deploy.rb
    │   └── wp-config-sample.php
    ├── public
    │   ├── index.php
    │   ├── license.txt
    │   ├── readme.html
    │   ├── wp-activate.php
    │   ├── ...

5. Now make sure your WordPress installation is good to go
6. Push your changes in my-wordpress to your own Git repository
7. Edit my-wordpress/config/deploy.rb to conform your production environment. You will need to set:

* application: this is the name of your application and the folder it will reside in on your server
* domain: this is the domain of your app
* user: this is the user that will be used to SSH and copying your files to your server
* git_domain and git_user should be self explanatory
* db_name, db_user, db_pass, db_host and db_prfx are all pretty self explanatory too if you have ever read through wp-config-sample.php.  If you haven't, go do that right now.

8. Run `cap deploy:setup`
9. If everything is good, run `cap deploy`
