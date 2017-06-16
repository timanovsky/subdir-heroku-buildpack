Add as a first buildpack in the chain. Set `PROJECT_PATH` environment variable to point to project root. It will be promoted to slug's root, everything else will be erased. Following buildpack (e.g. nodejs) will finish slug compilation.

**Disclaimer:** I may change the code without notice, so always pin to specific github version. Provided as is.

# How to use:
1. `heroku buildpacks:clear` if necessary
2. `heroku buildpacks:set https://github.com/timanovsky/subdir-heroku-buildpack`
3. `heroku buildpacks:add heroku/nodejs` or whatever buildpack you need for your application
4. `heroku config:set PROJECT_PATH=projects/nodejs/frontend` pointing to what you want to be a project root.
5. Deploy your project to Heroku.

# How it works
The buildpack takes subdirectory you configured, erases everything else, and copies that subdirectory to project root. Then normal Heroku slug compilation proceeds.
