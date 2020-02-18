# test-nginx-vapor
Example of putting NGiNx in front of Vapor on Heroku

#### Heroku setup

1. Create an app
2. Add official ngnix buildback, I used:  
   [Heroku Buildpack: NGINX](https://elements.heroku.com/buildpacks/heroku/heroku-buildpack-nginx)  
   `heroku-community/nginx` (or https://github.com/heroku/heroku-buildpack-nginx.git)
3. Add official Vapor buildpack - I used:  
   [Heroku buildpack: swift](https://elements.heroku.com/buildpacks/vapor-community/heroku-buildpack)  
   `vapor/vapor`
4. Grab the app's git URL.  (in `Settings`, something like `https://git.heroku.com/YOUR-APP-NAME-HERE.git`)
5. Fork this repo, clone it locally
6. Add your app's git URL as an origin for you local repo
7. Push the repo to the Heroku origin.
   This will deploy the app.

#### How it works

When code is pushed to the app's git repo, Heroku will run a post_receive hook that triggers each of the buildpacks added to the app, in the order that they are listed in your `Settings` pane.  This also happes to be the same order that they were added in the above steps: `ngnix` then `vapor`.

Once both buildpacks have finished building, the `Procfile` is executed.

The `Procfile` in this repo has a single line, that runs two commands:
```
web: bin/start-nginx Run serve --env production --port 8080 --hostname 0.0.0.0
```

- `bin/start-nginx` starts ngnix
- `Run serve --env production --port 8080 --hostname 0.0.0.0` runs the vapor app.
