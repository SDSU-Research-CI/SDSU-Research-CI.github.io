# SDSU-Research-CI.github.io

This repo contains the Research & Cyberinfrastructure documentation site: https://sdsu-research-ci.github.io/. The repo contains a dockerfile that uses a [pre-built Jekyll container](https://github.com/SDSU-Research-CI/jekyll/pkgs/container/jekyll) to allow editing and testing locally before publishing to GitHub pages.

This repo is set up to edit in Visual Studio Code.

The firt time the container is run on your comptuer, run the following:
 
```
# bundle install
# bundle update
```

When you're ready to test the site, run:

```
# bundle exec jekyll server --livereload
```

Point your browser to http://127.0.0.1:4000/ and you should be able to view the site. When you're ready to publish, use git to add/commit and then push.