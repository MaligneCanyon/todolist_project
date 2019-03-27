require 'bundler/gem_tasks' # req'd to produce a Gem from a project
require "rake/testtask" # autom build a list of test files
require 'find' # find files and dirs

task :hello do
  puts "Hello there. This is the 'hello' task."
end

# desc 'Run tests'
# task :test do
#   sh 'ruby ./test/todolist_project_test.rb'
# end

# automate test file inclusion:
Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end # desc is still 'Run tests'

desc 'Run tests'
task :default => :test

# exercise:
desc 'Find files'
task :finder do
  Find.find(ENV["PWD"]) do |path| # chk the proj dir and its subdirs
    if File.basename(path)[0] == ?. # ignore files or dirs that start w/ '.'
      Find.prune # skip the file or dir
    elsif File.file?(path)
      puts path # outputs the full path
    end
  end
end

# exercise solution:
desc 'Display inventory of all files'
task :inventory do
  Find.find('.') do |name|
    next if name.include?('/.') # Excludes files and directories with . names
    puts name if File.file?(name) # outputs the relative path
  end
end
