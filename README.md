#### Build

`hugo -t theme_folder_name`

#### Run

`hugo server -t theme_folder_name`

#### Deploy
+ Delete the current public folder `rm -rf public`.
+ Only at the first deploy, add the submodule: `git submodule add -b master git@github.com:andr3a88/andr3a88.github.io.git public`.
+ Run `./deploy` to deploy on `public` submodule. Remember to push the changes on _website_ repository.


git submodule add -b master https://github.com/andr3a88/andr3a88.github.io.git public