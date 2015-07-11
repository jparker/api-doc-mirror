desc <<-END
Build Rails API and Guides documentation.

Source is the path of a Rails application in which to build the documentation.
Target is the directory to which the compiled documentation should be
installed.
END
task :build, :source, :target do |t, args|
  raise '+source+ and +target+ are required'

  Dir.chdir args[:source] do
    File.open 'Gemfile', 'a' do |f|
      f.puts "gem 'redcarpet'"
      f.puts "gem 'nokogiri'"
    end
    system 'bundle', 'install', '-j2'
    system 'bundle', 'exec', 'rake', 'doc:rails', 'doc:guides'
  end

  File.rename File.join(args[:source], 'doc'), args[:target]
end
