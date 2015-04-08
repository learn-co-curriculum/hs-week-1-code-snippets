---
tags: sinatra, kids, ruby, advanced, code snippets
language: ruby
level: 2
type: code snippets
---

## Gimme that code!

There are several pieces of relatively standard code that we will need to set up in our Sinatra application. All of that code for each of the files below is provided for your copy and pasting convenience. 

Take heed of the spacing and indentation. Pretty code = easy to read code = happy developers.

### Gemfile - Code Snippet 1 

```ruby
source "https://rubygems.org"

gem "sinatra"

group :development do
  gem "pry"
  gem "tux"
end
```

### config.ru - Code Snippet 2

```ruby
require './app/controllers/application_controller'

run ApplicationController
```

### environment.rb - Code Snippet 3
(In the config directory.)

```ruby
require 'bundler'
Bundler.require
```

### application_controller.rb - Code Snippet 4
(In the app/controllers directory.)

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

### app/models/tweet.rb - Code Snippet 5
```ruby
  class Tweet
    attr_accessor :username, :status

    ALL_TWEETS = []

    def initialize(username, status)
      @username = username
      @status = status
      ALL_TWEETS << self
    end

    def self.all
      ALL_TWEETS
    end

  end
```

### tweets.erb - Code Snippet 6
(In the app/views directory. This includes a link to the Bootstrap stylesheeet.)

```html
<!doctype html>
<html>
  <head>
    <title>Week 1</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
  </head>
  <body> 
    <div class="container">


    </div>
  </body>
</html>
```

### Code Snippet 7

application_controller.rb:

```ruby
  get '/'
    "Welcome to Fwitter"
  end
```


###Code Snippet 8

application_controller.rb

```ruby
  get '/tweets'
    erb :tweet
  end
```

### Code Snippet 9:

application_controller.rb:
```ruby
  get '/tweets'
    @tweet1 = Tweet.new("flatironschool", "We <3 Coding")
    @tweet2 = Tweet.new("flatironschool", "Flatiron Pre-College Academy is amazing!")
    @tweet3 = Tweet.new("flatironschool", "Our students can build Twitter, can yours?")
    @tweet4 = Tweet.new("flatironschool", "#learnlovecode")
    @tweet5 = Tweet.new("flatironschool", "Developers Developers Developers!"
    @tweets = Tweet.all
    erb :tweet
  end
```

tweets.erb:

<!doctype html>
<html>
  <head>
    <title>Week 1</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
  </head>
  <body> 
    <div class="container">
      <% @tweets.each do |tweet| %>
        <p><%= tweet%></p>
      <% end %>
    </div>
  </body>
</html>
