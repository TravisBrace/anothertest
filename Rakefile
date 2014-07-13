#!/usr/bin/env rake
# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require File.expand_path('../config/application', __FILE__)

Againtesting::Application.load_tasks

initializer 'setup_asset_pipeline', :group => :all  do |app|
  # We don't want the default of everything that isn't js or css, because it pulls too many things in
  app.config.assets.precompile.shift

  # Explicitly register the extensions we are interested in compiling
  app.config.assets.precompile.push(Proc.new do |path|
    File.extname(path).in? [
      '.html', '.erb', '.haml',                 # Templates
      '.png',  '.gif', '.jpg', '.jpeg',         # Images
      '.eot',  '.otf', '.svc', '.woff', '.ttf', # Fonts
    ]
  end)

