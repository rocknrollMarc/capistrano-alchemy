# Capistrano::Alchemy - Capistrano Tasks for Alchemy CMS

Capistrano::Alchemy adds four folders to Capistranos `shared_folders` array: `uploads/pictures`, `uploads/attachments`, `tmp/cache/assets`, and Alchemy's picture cache. It also runs Alchemy's Seeder after migrating the database.

In addition, it offers several tasks to synchronize your shared folders and your database between environments.


## Installation

Add this line to your application's Gemfile:

```ruby
gem 'capistrano-alchemy', github: 'mamhoff/capistrano-alchemy', branch: 'doc-and-export', group: :development, require: false
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install capistrano-alchemy

You also have to add the `Capistrano::Alchemy` tasks to your Capfile

```ruby
require 'capistrano/alchemy'
```

## Usage


### Synchronize your data

Alchemy Capistrano receipts offer much more then only deployment related tasks. We also have tasks to make your local development easier. To get a list of all receipts type:

```shell
$ bundle exec cap -T alchemy
```

#### Import data from server

```shell
$ bundle exec cap staging alchemy:import:all
```

This imports your staging server's data onto your local development machine. This is very handy if you want to clone the current server state. Replace `staging` for `production` if you need the production data.

#### Export data to server

That even works the other way around:

```shell
$ bundle exec cap alchemy:export:all
```

**NOTE:** This will **overwrite the database** on your server. But calm down my dear friend, Alchemy will ask you to perform a backup before overwriting it.

## Contributing

1. Fork it ( https://github.com/[my-github-username]/capistrano-alchemy/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
