# Setting up the development environment

Prerequisites:
1. [Docker](https://www.docker.com/products/docker-desktop)
2. [Git](https://git-scm.com/downloads)
    - Or use your favorite package manager (`brew`, whatever your linux distro uses, etc.)
3. [Github Account](https://github.com/join)
4. Send an email to `board@lists.davismakerspace.org` that contains:
    - A request to be added to the Davis Makerspace Github organization (if you want to contribute changes)
    - A request for access to the website database
    - Your Github username
    - Your desired Wordpress username (if approved we will send you a password)

Create a top level directory to hold all your work. We suggest `dms-website` but you can use anything you want.

- Inside the top level directory, clone the development environment:

```
$ git clone https://github.com/DavisMakerspace/WPDevEnvironment.git
```

* Inside the top level directory, create a `themes` directory

* [Fork the dmsWPtheme](https://help.github.com/articles/fork-a-repo/)

* Inside the 'themes' directory clone **your fork** of the dmsWPtheme repository.

```
$ git clone <repo>
```

Your directory structure should look something like the following now:

```
./dms-website
    WPDevEnvironment/
    themes/
        dmsWPtheme/
```

# Getting everything running

To start Wordpress run the following command from inside the development environment repository (`WPDevEnvironment` directory):

```
$ docker-compose up
```

The first time you run this command it may take a while to complete as it will need to download the container images. Once you stop seeing text scrolling through your terminal window go ahead and try the next step. If you can't access the link in the next step be patient and try again in a bit.

To access Wordpress once the environment is running:
- Open browser
- Navigate to [http://localhost:8080](http://localhost:8080)
- Finish the installation by choosing a site name (doesn't matter what you choose), username, and password and record all info.

To add the database:
- Log into the site by navigating to: [http://localhost:8080/wp-admin](http://localhost:8080/wp-admin) in your browser. Enter the credentials you created.
- Click 'Plugins' in the left menu of the dashboard
- Click 'Add New' and type 'All-in-One WP Migration' into the search bar.
- Install and activate the plugin.
- In your WP dashboard under 'All-in-One WP Migration', select 'Import', and upload the database which was previously shared with you and accept.
- Log into [http://localhost:8080/wp-admin](http://localhost:8080/wp-admin) again using the credentials that were created for you on the already [existing WP site](https://wp.davismakerspace.org/). These are the credentials given to you after you opened an issue for an account.

Congratulations! You have set up the dev environment.

# Contributing your changes to the theme

In order to make changes to the site:
- Navigate to `themes/dmsWPTheme`.
- Make changes to the files.
- Add, and commit the changes
- Push the changes to your fork
- From you fork make a [pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/) to the dmsWPtheme repo.

## Tips

To start WP over from scratch (will remove all DB content) run the following from the development environment directory (`WPDevEnvironment`):

```
$ docker-compose down -v
$ rm -rf volumes/
```

If you need help understanding how to use git or Github there are many resources [available](https://help.github.com/articles/git-and-github-learning-resources/).
