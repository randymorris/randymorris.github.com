This is the source of my personal website [http://rsontech.net/](http://rsontech.net).  The only interesting branch in this repo will be the *source* branch as GitHub expects the generated website to live in *master*.

Steps to publish:

* Make changes in the *source* branch
* Build and test the site locally
* Commit changes to *source* branch
* `git publish-website` which consists of the following steps
  - `git branch -D master`
  - `git checkout -b master`
  - `git filter-branch --subdirectory-filter _site/ -f`
  - `git checkout source`
  - `git push --all origin`


