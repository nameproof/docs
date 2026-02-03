# Git

## Config

List current git config: `git config list`

## First time repo setup

Start new app in current environment (~/rails/): `rails new <app_name> --skip-bundle`
(spec rails ver. (like `rails _7.0.4_`) and `--skip-bundle` is optional)

```bash
cd ~/rails/app
git init
```

If you don't want a group locally: `bundle config set --local without 'production'`
Edit Gemfile and then run `bundle install`

### Template first push to GH

```bash
git add -A
git commit -m "init"
git remote add origin https://github.com/<name>/<appName>.git
git branch -M main
git push -u origin main
```

## General

Add project files to repo staging area, becoming pending changes: `git add -A`

See files in staging area: `git status`

Commit files in staging area: `git commit -m "message"`

See list of commit messages: `git log`

Restore anything that isn't commited: `git restore .` (last part is the path)

List all local branches: `git branch`

Add and commit all changes (not new files): `git commit -am "message"`

Push when we've already pushed so we can omit origin main: `git push`

## Branching

Create and switch to new branch: `git switch -c <branchName>`

Switch branch (care to commit first if possible): `git switch <branch>`

Merge branch: First switch to branch you want to commit into `git switch <branchMergeInto>` then `git merge <branchMergeFrom>`

Delete branch (optionally common after merging a branch): `git branch -d <branch>` (-D will delete even if changes aren't merged. Like mistakes on new branches)

### For illustration only; don't do this unless you mess up a branch

`git switch -c topic-branch`<br>
*really mess up the branch*<br>
`git add -A`<br>
`git commit -am`<br>
*Make major mistake*<br>
`git switch main`<br>
`git branch -D topic-branch`

## Kamal deploy Sub path setup

Use the deploy.yml template.<br>
In routes.rb, add the scope:

```ruby
Rails.application.routes.draw do
  scope(ENV.fetch("RAILS_RELATIVE_URL_ROOT", "/")) do
    ...
  end
end
```

Install rewrite gem:<br>
`gem "rack-rewrite", "~> 1.1"`

In (or preffered environment) config/environments/production.rb

```ruby
Rails.application.configure do
  # Settings specified here will take precedence over those in config/application.rb.

  # Enable Puma to serve static assets directly (required without nginx/reverse proxy for assets)
  config.public_file_server.enabled = true

  # Rewrite subpath asset requests to root-relative for static serving
  # (e.g., /sample_app/assets/tailwind-*.css -> /assets/tailwind-*.css internally)
  if relative_url_root = ENV['RAILS_RELATIVE_URL_ROOT'].presence
    config.middleware.insert_before 0, Rack::Rewrite do
      rewrite %r{#{Regexp.escape(relative_url_root)}(/assets/.*)}, '/$1'
    end
  end

  # ... rest of config ...
end
```

## Secrets

Option 2: Read secrets via a command

```yml
RAILS_MASTER_KEY=$(cat config/master.key)
KAMAL_REGISTRY_PASSWORD=$(bin/rails runner "puts Rails.application.credentials.docker.registry_password")
bin/rails credentials:edit
```
