require 'rubygems'
require 'bundler/setup'
require 'tfg_cap'

enable_recipe! :airbrake, :asset_pipeline

set :application,      'discourse'
set :display_name,     'Discourse'
set :repository,       'git@github.com:thefrontiergroup/discourse.git'
set :bundle_without,   [:development, :test, :test_mac]
set :release_regexp,   /2013/
set :ruby_interpreter, 'ruby-2.0.0-p247'
set :ruby_gemset,      'discourse'
set :seed_database,    false
set(:branch)           { ask_for_release_branch }
set :user,             'ubuntu'
set :group,            'ubuntu'

# Params:       shared/#{foo}  => current/{bar}
has_linked_dirs 'images'  => 'public/assets/images',
                'uploads' => 'public/uploads'

stage :staging do
  server 'soundwave.thefrontiergroup.net.au', :app, :web, :db, :primary => true
  set    :domain,    'discourse.tfgrails.com'
end
