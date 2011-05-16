require 'rake/rdoctask'
require 'fileutils'

$:.unshift "."

Rake::RDocTask.new(:rdoc_spec) do |rd|
  spec_file = File.join(ENV["RUBYGEMS_DIR"].to_s, "lib", "rubygems", "specification.rb")
  raise "#{spec_file} does not exist" unless File.exist?(spec_file)

  rd.rdoc_files.include(spec_file)
  rd.template = "jekdoc"
end

desc "move spec guide into the right place"
task :move_spec do
  FileUtils.mv "html/Gem/Specification.html", "specification-reference.md"
end

desc "clean up after rdoc"
task :clean do
  FileUtils.rm_rf "html"
end

desc "generate specification guide"
task :spec_guide => [:rdoc_spec, :move_spec, :clean]