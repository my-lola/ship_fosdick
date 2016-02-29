# ShipFosdick

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'ship_fosdick'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install ship_fosdick

## Usage

### Upload

Since Fosdick reads from an XML file uploaded to an S3 bucket, 
This Gem exposes a simple factory: `ShipFosdick::UploadFactory` 
That has a single public method: `call` that will kick off the following:

1. Collect all shipments created during the past day
1. Create a single xml string that is parsable from Fosdick
1. Upload this string to a file in S3 called fosdick_shipments.xml

A simple rake task to get this working could be as easy as:

```
shipper = ShipFosdick::UploadFactory.new
shipper.call
```

## Setup

Most Solidus and Spree stores will be running Paperclip. 
This, at the moment relies on the 3 environment variables that should be set if running Paperclip:

```
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
S3_BUCKET
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. 
Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`.
To release a new version, 
update the version number in `version.rb`,
and then run `bundle exec rake release`, 
which will create a git tag for the version, 
push git commits and tags, 
and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/dynamomtl/ship_fosdick.
This project is intended to be a safe, 
welcoming space for collaboration, 
and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct. 
All changed items are recorded in the CHANGELOG.md

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

