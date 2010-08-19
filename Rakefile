require 'rake/clean'
require 'rake/gempackagetask'
require 'rake/testtask'

GEM_NAME='rbx_only'
GEM_VERSION='0.0.1'

desc "Builds and installs into Rubinius rubygems"
task :install => :gem do
  
end

spec = Gem::Specification.new do |s|
  s.name          = GEM_NAME
  s.version       = GEM_VERSION
  s.description   = %q{A gem that can only works in Rubinius}
  s.summary       = %q{A gem that can only works in Rubinius with only rbc compiled files.}
  s.authors       = ["Dr Nic Williams"]
  s.email         = ["drnicwilliams@gmail.com"]
  s.homepage      = %q{http://drnicwilliams.com/}
  s.date          = Time.now.strftime("YYYY-MM-DD")
  s.executables   = ["rbx_only"]
  # s.files       = Dir["{bin,lib,test}/**/*"] + Dir["{*.txt,*.rdoc,Rakefile}"] NORMAL
  s.files         = Dir["bin/**/*"] + Dir["lib/**/*.rbc"] + Dir["{*.txt,*.rdoc}"]
  s.require_paths = ["lib"]
  s.test_files    = Dir["test/**/test*.rb"]
end

desc "Build the gem file"
task :gem => :build do
  gem_task = Rake::GemPackageTask.new(spec)
  Gem::Builder.new(spec).build
  mkdir "pkg" unless File.exist? "pkg"
  mv(gem_task.gem_file, "pkg/")
end

task :build do
  # build the .rbc files if they don't exist yet
end