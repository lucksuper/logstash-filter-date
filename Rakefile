@files=[]

task :default do
  system("rake -T")
end

require "logstash/devutils/rake"

task :vendor => :gradle

task :gradle => "gradle.properties" do
  system("./gradlew vendor")
end

task "gradle.properties" do
  delete_create_gradle_properties
end

def delete_create_gradle_properties
  root_dir = File.dirname(__FILE__)
  gradle_properties_file = "#{root_dir}/gradle.properties"
  lsc_path = `/Users/qukangning/Downloads/logstash-6.6.0/logstash-core`
  FileUtils.rm_f(gradle_properties_file)
  File.open(gradle_properties_file, "w") do |f|
    f.puts "logstashCoreGemPath=#{lsc_path}"
  end
  puts "-------------------> Wrote #{gradle_properties_file}"
  puts `cat #{gradle_properties_file}`
end

