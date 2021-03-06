# EarthVectors Website

## Setup

* Clone the repo with `git clone`
* `rvm install "ruby-2.6.3"`
* `bundle`
* `gem install bundler`
* Install Postgres.app
* `rake db:create`
* Copy `application.yml` from 1Password into `config` folder
* Start up with `rails server`

## Deploying to Heroku Review

* Download the Heroku CLI
* Login into Heroku via the CLI `heroku login`
* Set up your remote: `heroku git:remote -a earthvectors-review`.
* Since the Heroku remote by default is `heroku`, we need to change the name to make
it clear that it is review.  `git remote rename heroku heroku-review`
* We need nodejs buildpack for the assets to properly precompile. And yes the order of which the buildpacks
are loaded matter:
```
heroku buildpacks:remove heroku/ruby --app earthvectors-review
heroku buildpacks:add heroku/nodejs --app earthvectors-review
heroku buildpacks:add heroku/ruby --app earthvectors-review
```
* Local branches can be pushed up by `git push heroku-review your_branch_name:master`.
* Master can be pushed by `git push heroku-review master`

## Deploying to Heroku Production
* Set up your remote: `heroku git:remote -a earthvectors`. This sets your remote name as `heroku`.
* We need nodejs buildpack for the assets to properly precompile. And yes the order of which the buildpacks
are loaded matter:
```
heroku buildpacks:remove heroku/ruby --app earthvectors
heroku buildpacks:add heroku/nodejs --app earthvectors
heroku buildpacks:add heroku/ruby --app earthvectors
```
* To deploy your committed changes on master run `git push heroku master`
