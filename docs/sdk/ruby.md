# Ruby SDK

We have made our own Ruby SDK for Errordeck. You can find it [here](https://github.com/errordeck/errordeck-ruby).

Right now it support Rack out of the box.

## How to use the Ruby SDK

You can use the Ruby SDK like this:

```ruby
require 'errordeck'

Errordeck.configure do |config|
  config.token = "_r-3A7egL7uMHgAkdRodzxxxAQo"
  config.project_id = "1"
  config.environment = "development" # optional - if not set, it will be set to Rails.env
  config.release = "0.0.0" # optional
  config.dist = "0.0.0" # optional
end

# send a message to errordeck
Errordeck.message("test")


begin
  raise "test"
rescue => exception
  Errordeck.capture(exception)
end
```

## How to install the Ruby SDK

You can install the Ruby SDK like this:

```bash
gem install errordeck
```
You can also add it to your Gemfile:

```ruby
gem 'errordeck'
```