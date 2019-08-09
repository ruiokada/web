task :build do
  puts "Building site"
  sh 'bundle exec jekyll b'
end
task b: :build

task :serve do
  sh 'bundle exec jekyll s'
end
task s: :serve

task default: :build
