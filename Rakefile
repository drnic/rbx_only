require 'rake/clean'
require 'rake/gempackagetask'
require 'rake/testtask'

GEM_NAME='rbx_only'
GEM_VERSION='0.0.1'

desc "Builds and installs into Rubinius rubygems"
task :install => :gem do
  
end

spec = Gem::Specification.new do |s|
  s.platform = "rubinius"
  s.summary  = "Rubinius implementation of ruby-debug-base"
  s.name     = GEM_NAME
  s.version  = GEM_VERSION
  s.authors = ["Dr Nic Williams"]
  s.date = Time.now.strftime("YYYY-MM-DD")
  s.description = %q{A gem that can only be installed into Rubinius}
  s.email = ["drnicwilliams@gmail.com"]
  s.executables = ["rbx_only"]
  s.extra_rdoc_files = ["README.rdoc"]
  s.files = Dir["{bin,lib,test}/**/*"] + Dir["{*.txt,*.rdoc,Rakefile}"]
  s.homepage = %q{http://drnicwilliams.com/}
  s.rdoc_options = ["--main", "README.rdoc"]
  s.require_paths = ["lib"]
  s.rubyforge_project = %q{rbx_only}
  s.rubygems_version = %q{1.3.7}
  s.summary = %q{A gem that can only be installed into Rubinius. Perhaps only with rbc files!}
  s.test_files = Dir["test/**/test*.rb"]
end

gem_name = "#{GEM_NAME}-#{GEM_VERSION}-rubinius.gem"
# gem_name = "#{GEM_NAME}-#{GEM_VERSION}-#{spec.platform}.gem"

desc "Build the gem file #{gem_name}"
task :gem do
  gem_task = Rake::GemPackageTask.new(spec)
  # Create the gem, then move it to pkg.
  Gem::Builder.new(spec).build
  mkdir "pkg" unless File.exist? "pkg"
  mv(gem_task.gem_file, "pkg/#{gem_name}")
end