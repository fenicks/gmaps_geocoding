# encoding: utf-8
require 'bundler/gem_tasks'
require 'rake/testtask'

lib = File.expand_path('../lib/', __FILE__)
$:.unshift lib unless $:.include?(lib)
require('gmaps_geocoding/version')

task gem: :build
task :build do
  system 'gem build gmaps_geocoding.gemspec'
end

task install: :build do
  system "gem install gmaps_geocoding-#{GmapsGeocoding::VERSION}.gem"
end

task release: :build do
  system "git tag -a v#{GmapsGeocoding::VERSION} -m 'Tagging #{GmapsGeocoding::VERSION}'"
  system 'git push --tags'
  system "gem push gmaps_geocoding-#{GmapsGeocoding::VERSION}.gem"
  # system "rm gmaps_geocoding-#{GmapsGeocoding::VERSION}.gem"
end

Rake::TestTask.new do |t|
  t.libs << 'lib/gmaps_geocoding'
  t.test_files = FileList['test/*_test.rb']
  t.verbose = true
end

task default: :test
