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
