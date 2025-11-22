# Git

## Config

List current git config: `git config list`

First time repo setup:

Start new app in current environment (~/rails/): `rails new <app_name> --skip-bundle`
(spec rails ver. (like `rails _7.0.4_`) and `--skip-bundle` is optional)

```bash
cd ~/rails/app
git init
```

If you don't want a group locally: `bundle config set --local without 'production'`
Edit Gemfile and then run `bundle install`

Add project files to repo staging area, becoming pending changes: `git add -A`

See files in staging area: `git status`

Commit files in staging area: `git commit -m "message"`

See list of commit messages: `git log`

Restore anything that isn't commited: `git restore .` (last part is the path)

Template first push to GH:

```bash
git remote add origin https://github.com/<name>/hello_app.git
git branch -M main
git push -u origin main
```

Create and switch to new branch: `git switch -c <branchName>`

List all local branches: `git branch`

Add and commit all changes (not new files): `git commit -a -m "message"`

Switch branch (care to commit first if possible): `git switch <branch>`

Merge branch: `git merge <branch>`

Delete branch: `git branch -d <branch>` (-D will delete even if changes aren't merged)

Push when we've already pushed so we can omit origin main: `git push`

## Sub path setup

Use the deploy template.
In routes.rb, add the scope:

```ruby
Rails.application.routes.draw do
  scope(ENV.fetch("RAILS_RELATIVE_URL_ROOT", "/")) do
    ...
  end
end
```

## Secrets

- Option 2: Read secrets via a command
RAILS_MASTER_KEY=$(cat config/master.key)
KAMAL_REGISTRY_PASSWORD=$(bin/rails runner "puts Rails.application.credentials.docker.registry_password")
`bin/rails credentials:edit`
