## HUGO

See the link below for the basic usage of Hugo: [Basic usage](https://gohugohug.io/overview/usage/)

#### Build

Build hugo locally `hugo -t theme_folder_name`

#### Run

Run hugo locally for development purpose: `hugo server -t theme_folder_name`

#### Deploy to Github Pages
+ Delete the current public folder `rm -rf public`.
+ Only at the first deploy, add the submodule: `git submodule add -b master https://github.com/andr3a88/andr3a88.github.io.git public`.
+ Give permission `chmod +x deploy.sh`
+ Run `./deploy` to deploy on `public` submodule. Remember to push the changes on _website_ repository.

### Themes 

+ Hugo GOA: [https://github.com/shenoybr/hugo-goa](https://github.com/shenoybr/hugo-goa)
