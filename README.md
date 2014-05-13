# DbSync

Have you ever gone to test a specific or develop a feature, except it requires use of data that currently only exists in production?   

Instead of going through a very time-consuming database dump and load process, you can use this gem instead. 

It works by dumping certain tables you want into some yaml files in db_dump.  You can then easily load them into your database.  

This works a an alternative to ludicast/yaml_db for some use cases.

## Installation

Add this line to your application's Gemfile:

    gem 'db_sync'


And in config/initializers/db_sync.rb

    DbSync.configure do |config|
      config.sync_tables = ["TABLE_NAME"]
    end

## Usage 

Run this to dump the tables you specified in the initializer to db_dump
   
    bundle exec rake db_sync:dump_data 
    
Or run against a specific rails environment

    bundle exec rake db_sync:dump_data RAILS_ENV=production

Run this to load the tables back in.
WARNING: this overwrites the contents of this existing table.  
   
    bundle exec rake db_sync:load_data

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
