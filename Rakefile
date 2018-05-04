require 'rspec/core/rake_task'
require "yaml"

task :default => [:serve]

desc "Build site."
task :build do
  sh "bundle exec jekyll build"
end

desc "Serve site."
task :serve do
  sh "bundle exec jekyll serve"
end

desc "Test site."
task :test => [:build] do
  RSpec::Core::RakeTask.new(:test)
end

desc "Find files in site that are not present in data files."
task :prune do
  files = Rake::FileList[]

  data_files = []

  to_remove = []
  files.each { |file|
    if not data_files.include?(File.basename(file))
      to_remove << file
    end
  }

  if ! to_remove.empty?
    puts "These files are extras and can probably be removed."
    to_remove.each { |file|
       puts File.expand_path(file)
    }
  end

end
