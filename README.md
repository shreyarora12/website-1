# Website for Fedora Developer Portal

This repository contains Jekyll templates, HTML and CSS files for the Fedora Developer Portal.

If you are here to submit issue or PR regarding the content of the portal, please do so in the `content` repository:
https://github.com/developer-portal/content.

## Local development instance

### Using a Docker container

Docker container provides a simple way how to run the development instance of Developer Portal. Following command will start the Jekyll server in a container (with very similar output):

```
$ sudo docker run -it --rm developerportal/devel
Configuration file: /website/_config.yml
            Source: /website
       Destination: /website/_site
      Generating... 
                    done.
 Auto-regeneration: enabled for '/website'
Configuration file: /website/_config.yml
    Server address: http://172.17.1.16:8080/
  Server running... press ctrl-c to stop.

```

The above command will serve the latest content available in Github repository. If you want to do some changes in a `website` repository and view them, you need to add argument `-v /path/to/your/repo:/website`:

```
$ sudo docker run -it --rm -v $PWD:/website developerportal/devel
```

In case you want to modify the `content` repository, you need to add argument `-v /path/to/content/repo:/website/content`:

```
$ sudo docker run -it --rm -v $PWD/content:/website/content developerportal/devel
```
 


### Using local installation

Before fetching the sources from GitHub make sure you have the public keys uploaded to your GitHub account. Here is how to do it:  https://help.github.com/articles/error-permission-denied-publickey/.

Then run:

```bash
$ git clone git@github.com:developer-portal/website.git && cd website
$ git submodule init
$ git submodule update
$ jekyll serve --force_polling
```

`jekyll serve --force_polling` will start the development server at `http://127.0.0.1:4000/` and regenerate any modified files for you. If you don't have Jekyll installed, here is the installation guide: http://jekyllrb.com/docs/installation/.

If you want to **install Jekyll on Fedora** with Ruby Gems, you can use our content to learn how: https://github.com/developer-portal/content/blob/master/tech/languages/ruby/gems-installation.md

To update the content/ directory fetched by `git submodule update` just switch to that directory, make sure you are on the master branch and pull the latest stuff:

```bash
$ cd content
$ git checkout master
$ git pull
```

If you just want to download the sources without uploading your keys get the sources as:

```bash
$ git clone https://github.com/developer-portal/content.git
```
