#!/usr/bin/env rake
require "bundler/gem_tasks"
require 'rubygems/package_task'
require 'rubygems/specification'

gemspec = eval(IO.read("scry.gemspec"))

Gem::PackageTask.new(gemspec).define

begin
  require 'rspec/core/rake_task'

  RSpec::Core::RakeTask.new do |t|
    t.pattern = 'spec/**/*_spec.rb'
  end
rescue LoadError
  desc "rspec is not installed, this task is disabled"
  task :spec do
    abort "rspec is not installed. `(sudo) gem install rspec` to run unit tests"
  end
end

task :default => :spec
