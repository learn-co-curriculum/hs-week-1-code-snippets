---
tags: sinatra, kids, ruby, advanced, code snippets
language: ruby
level: 2
type: code snippets
---

## Gimme that code!

There are several pieces of relatively standard code that we will need to set up in our Sinatra application. All of that code for each of the files below is provided for your copy and pasting convenience. 

## Gemfile

```ruby
source "https://rubygems.org"

gem "sinatra"

group :development do
  gem "pry"
  gem "tux"
end
```

## config.ru

```ruby
require './app/controllers/application_controller'

run ApplicationController
```

## environment.rb (in the config directory)

```ruby
require 'bundler'
Bundler.require
```

## application_controller.rb
(This doesn't include the routes you will be creating in class.)

```ruby
require './config/environment'
require './app/models/tweet'

class ApplicationController < Sinatra::Base

  configure do
    set :public_folder, 'public'
    set :views, 'app/views'
  end

end
```