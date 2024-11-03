#!/usr/bin/env ruby

require 'rake'
require 'haml'

task default: :compile

task :compile do
  # Look for all .haml files in the current directory
  FileList.new('./*.haml').each do |filename|
    # Get the name of the HTML file to be created
    html_filename = filename.sub(/\.haml$/, '.html')
    
    # Render the HAML file and write to the corresponding HTML file
    begin
      File.open(html_filename, 'w') do |f|
        f.write Haml::Engine.new(File.read(filename)).render
      end
      puts "Converted #{filename} to #{html_filename}."
    rescue StandardError => e
      puts "Error converting #{filename}: #{e.message}"
    end
  end
end

task :clean do
  # Remove all HTML files generated
  FileUtils.rm_f(Dir.glob('./*.html'))
end
