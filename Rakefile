desc <<-END
Build Rails API and Guides documentation.

+source+ is the path of a Rails application in which to build the
documentation.

+bundle_opts+ are options that should be passed to `bundle install`.

END
task :build, :source, :bundle_opts do |t, args|
  raise '+source+ is required' unless args[:source]

  Dir.chdir args[:source] do
    File.open 'Gemfile', 'a' do |f|
      f.puts "gem 'redcarpet'"
      f.puts "gem 'nokogiri'"
    end
    system 'bundle', 'install', *args[:bundle_opts]
    system 'bundle', 'exec', 'rake', 'doc:rails', 'doc:guides'
  end
end
