# Yenius

[Live Site](https://yenius.herokuapp.com/)
[GitHub](https://github.com/marshall-strong/yenius)

# Resume Project Info

## Keywords

Ruby on Rails 6, PostgreSQL, JavaScript, React.js, Redux.js, SCSS, AWS, Heroku

## Description

a Kanye West-centric full-stack clone of Genius.com -- community sourced music lyrics, interpretations, and metadata

## Present Tense Bullets

- Single Page App supports a fast frontend by loading resources at launch and by only transmitting JSON data
- Bing News Search API retrieves the latest tabloid gossip on Kanye West’s impending divorce
- Redux store maintains a single source of truth on the frontend, allowing easy access to complex metadata
- BCrypt gem salts, hashes, and retrieves passwords, maintaining secure authentication from front to back
- Rails polymorphic associations prevent the need for schema changes when adding new types of metadata

## Past Tense Bullets

- Retrieved the latest tabloid gossip on Kanye West’s impending divorce with the Bing News Search API
- Managed complex metadata by using Redux to create a normalized state with a single source of truth
- Leveraged Rails polymorphic associations to avoid schema changes when adding new types of metadata
- Ensured secure user authentication by using the BCrypt gem to salt, hash, and retrieve passwords

## Other Bullets

- Single Page App supports a fast frontend by loading resources at launch and by only transmitting JSON data
- Create React App’s Redux+JS template abstracts away Webpack configuration, uses Redux Toolkit and React-Redux to reduce both boilerplate code and developer headaches

# Backend

The backend is an API-only Ruby on Rails app, and uses a postgreSQL database.

## Rails 6

We are essentially using rails as an API only (I didn't create the app in API only mode, but I did delete most of the non-API stuff).

## PostgreSQL

## Routes, Controllers

## Active Record models

## Polymorphic associations

_Rails polymorphic associations prevent the need for schema changes when adding new types of metadata_

_Leveraged Rails polymorphic associations to avoid schema changes when adding new types of metadata_

## Counter Cache

## BCrypt gem

_BCrypt gem salts, hashes, and retrieves passwords, maintaining secure authentication from front to back_

_Ensured secure user authentication by using the BCrypt gem to salt, hash, and retrieve passwords_

## Seed Generation

# Frontend

_Single Page App supports a fast frontend by loading resources at launch and by only transmitting JSON data_

The frontend is a React/Redux app, located in the `client/` direcory. It was created using [cra-template-redux](https://github.com/reduxjs/cra-template-redux), the official Redux+JS template for [Create React App](https://github.com/facebook/create-react-app).

## React.js

## React Hooks API

## React Router

Single Page App supports a fast frontend by loading resources at launch and by only transmitting JSON data

## Redux.js

_Redux store maintains a single source of truth on the frontend, allowing easy access to complex metadata_

_Managed complex metadata by using Redux to create a normalized state with a single source of truth_

## Create React App redux template

_Because life is too short to configure Webpack manually_

- Create React App’s Redux+JS template
- abstracts away Webpack configuration
- uses Redux Toolkit and React-Redux to reduce boilerplate code

## Bing News Search API

_Bing News Search API retrieves the latest tabloid gossip on Kanye West’s impending divorce_

_Retrieved the latest tabloid gossip on Kanye West’s impending divorce with the Bing News Search API_

# Assets

## SASS

## Fonts

## SVGs

## images hosted on AWS S3

# Proxy API Calls

Automatically proxy API calls via the right port, without needing to swap anything between development and production.
To do this, jump into `client/package.json` and add a proxy property:

##### `client/package.json`

```json
"proxy": "http://localhost:3001/",
```

Once we hook everything up our scripts will be running the API on port `3001`, and we are configuring Rails to be our API.

# Heroku

## [How Heroku Works](https://devcenter.heroku.com/articles/how-heroku-works)

- the `build` command uses `yarn --cwd client` to tell yarn to `cd` into the `client/` directory before running `build`
- the `post-build` command gets run after heroku has built the application, or "slug"

## Heroku local

Having a Node server and a Rails server both running locally massviely speeds up development time. It's great for development, but overkill for production.

While we do need to run a Node server localy, we'll be depoying a pre-built bundle to heroku, and we won't need to run a Node server there.

### Heroku Command Line Interface

https://devcenter.heroku.com/articles/heroku-cli

### Procfiles

[Introduction to Procfiles by Heroku](https://devcenter.heroku.com/articles/procfile)

## Development

### Create a Procfile for starting the app in Development

##### `Procfile.dev`

```text
web: PORT=3000 yarn --cwd client start
api: PORT=3001 bundle exec rails s

```

### Use Heroku CLI to run the Procfile

##### in your console:

```bash
$ heroku local -f Procfile.dev
```

### Create a rake task to run the Dev Procfile

##### `lib/tasks/start.rake`

```ruby
namespace :start do
  task :development do
    exec 'heroku local -f Procfile.dev'
  end
end

desc 'Start development server'
task :start => 'start:development'

```

##### Run the rake task in your console:

```bash
$ yarn start
```

##### console output:

```bash
marstrong@mars-ideapad:~/yenius$ yarn start
yarn run v1.22.5
$ rails start
[OKAY] Loaded ENV .env File as KEY=VALUE Format
4:45:42 PM web.1 |  $ react-scripts start
4:45:45 PM api.1 |  => Booting Puma
4:45:45 PM api.1 |  => Rails 6.0.3.4 application starting in development
4:45:45 PM api.1 |  => Run `rails server --help` for more startup options
4:45:46 PM api.1 |  Puma starting in single mode...
4:45:46 PM api.1 |  * Version 4.3.7 (ruby 2.7.2-p137), codename: Mysterious Traveller
4:45:46 PM api.1 |  * Min threads: 5, max threads: 5
4:45:46 PM api.1 |  * Environment: development
4:45:46 PM api.1 |  * Listening on tcp://127.0.0.1:3001
4:45:46 PM api.1 |  * Listening on tcp://[::1]:3001
4:45:46 PM api.1 |  Use Ctrl-C to stop
4:45:46 PM web.1 |  ℹ ｢wds｣: Project is running at http://172.24.232.210/
4:45:46 PM web.1 |  ℹ ｢wds｣: webpack output is served from
4:45:46 PM web.1 |  ℹ ｢wds｣: Content not from webpack is served from /home/marstrong/yenius/client/public
4:45:46 PM web.1 |  ℹ ｢wds｣: 404s will fallback to /
4:45:46 PM web.1 |  Starting the development server...
4:46:12 PM web.1 |  Compiled successfully!
4:46:12 PM web.1 |  You can now view yenius-client in the browser.
4:46:12 PM web.1 |    Local:            http://localhost:3000
4:46:12 PM web.1 |    On Your Network:  http://172.24.232.210:3000
4:46:12 PM web.1 |  Note that the development build is not optimized.
4:46:12 PM web.1 |  To create a production build, use yarn build.
```

One command to fire up two servers! Heroku will start the front end, /client, on port 3000, and the API on port 3001.
It’ll then open the client, http://localhost:3000 in your browser.

## Production Environment

So, how do we get our Rails app serving the Webpack bundle in production?

Heroku's `heroku-postbuild` command will build the app (located in the `/client` directory), then copy the files into the `/public` directory to be served by Rails. We end up with a single Rails server manging both our front end and our back end.

##### `package.json`

```json
{
  "name": "list-of-ingredients",
  "license": "MIT",
  "engines": {
    "node": "10.15.3",
    "yarn": "1.15.2"
  },
  "scripts": {
    "build": "yarn --cwd client install && yarn --cwd client build",
    "deploy": "cp -a client/build/. public/",
    "heroku-postbuild": "yarn build && yarn deploy"
  }
}
```

### Create a Procfile for starting the app in Production

##### Procfile

```text
web: bundle exec rails s
release: bin/rake db:migrate
```

Heroku runs the `release` command just before a new release of the app is deployed. We'lll use it to make sure our database is migrated.

#### [more info on `release`...](https://devcenter.heroku.com/articles/release-phase)

## Configure Secrets

### [Encrypted Secrets](https://blog.engineyard.com/encrypted-rails-secrets-on-rails-5.1)

#### set up encrypted secrets

```bash
$ rails secrets:setup
```

This command creates 2 files.
`config/secrets.yml.key` contains the key the will encrypt and decrypt the secrets. This file should not be commit to GitHub.
`config/secrets.yml.enc` contains the encrypted secrets. The secrets have been encrypted with the key, and are safe to commit to GitHub.

#### edit encrypted secrets

```bash
$ rails secrets:edit
```

Opens the secrets as an unencrypted text file.
After the file is saved and closed, an encrypted version will be saved to `config/secrets.yml.enc`.

#### generate a new secret key base

```bash
$ rails secret
```

Use the Rails secret key base as the environmental variable RAILS_MASTER_KEY

### uptime-robot

# Code Style

## Configure Prettier, ESLint, pre-commit git hooks

https://prettier.io/docs/en/install.html

### Install Prettier dev dependency:

`npm install --save-dev --save-exact prettier`

### Create Prettier config file:

`echo {}> .prettierrc.json`

### Create `.prettierignore` file from `.gitignore`:

`cp .gitignore .prettierignore`

### Format all files with Prettier:

`npx prettier --write .`

### Install ESLint:

`npm install eslint --save-dev`

### Configure ESLint:

`npx eslint --init`

### Install eslint-config-prettier:

`npm install eslint-config-prettier --save-dev`

https://pre-commit.com/

### Create pre-commit config file:

```yaml
  repos:
    - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.4.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-yaml
      - id: check-added-large-files
    - repo: https://github.com/pre-commit/mirrors-prettier
    rev: "v2.2.1"
    hooks:
      - id: prettier

```

- Install pre-commit git hook: `pre-commit install`

# Design Decisions

the file structure of this project changed multiple times over the course of development.

- manual Webpack structure
- Rails Webpacker
- 2 repositories: CreateReactApp frontend, Rails 6 API backend
- Create React App (current)

# Future Development

## CMS

add CMS access with [ActiveAdmin](https://activeadmin.info/0-installation.html#setting-up-active-admin)

## User roles

multiple user roles:

- moderators can edit, delete all Comments
- admins can add, edit ArtistCreditTypes, SampleCreditTypes
- users can add, edit Albums, Artists, Songs, Lyrics, ArtistCredits, SampleCredits

## Popups on hover

mousing over an artist link should display the artist's headshot.
the headshot should disappear when the user mouses away.

# Acknowledgments

## [A Rock Solid, Modern Web Stack](https://blog.heroku.com/a-rock-solid-modern-web-stack)

I used this Heroku post when setting up my project.

From the post:

- [Create React App](https://github.com/facebookincubator/create-react-app)
  - All the power of a highly-tined Webpack config without the hassle.
- [Rails in API-only mode](http://edgeguides.rubyonrails.org/api_app.html)
  - Just the best bits, leaving React to handle the UI.
- [Active Admin](https://github.com/activeadmin/activeadmin)
  - An instant CMS backend.
- Seamless deployment on [Heroku](https://heroku.com/)
  - Same-origin (so no CORS complications) with build steps to manage both Node and Ruby.
- Single page app support with [React Router](https://github.com/ReactTraining/react-router)
  - So you can have lightning fast rendering on the front end.
