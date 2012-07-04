desc "Packages the template"
task :package do
  `git submodule init`
  `git submodule update`
  
  `cd wordpress-cookbook; compass compile -e production`
  
  `rm -rf package`
  `rm -rf build`
  `rm -f Cookbook.zip`
  `rm -f cookbook.zip`
  
  `mkdir -p build/cookbook`
  
  theme_files = %w(screenshot.png functions.php lib images index.php javascripts style.css stylesheets sass)
  theme_files_for_zip = theme_files.map { |f| "wordpress-cookbook/#{f}"}
  
  `cp -r #{theme_files_for_zip.join(' ')} build/cookbook`
  
  puts `cd build; zip -r ../cookbook-theme.zip cookbook -x .gitignore .gitkeep .DS_Store`
  
  `rm -r build`
  
  `mkdir -p build/Cookbook`
  
  packages_files = %w(Licensing cookbook-theme.zip Documentation)
  `cp -r #{packages_files.join(' ')} build/Cookbook`
  `rm -rf build/Cookbook/Documentation/.sass-cache build/Cookbook/Documentation/sass`
  
  puts `cd build; zip -r ../Cookbook.zip Cookbook -x .gitignore .gitkeep .DS_Store`
  
  `rm -fr package`
  `mkdir -p package`
  
  `mv Cookbook.zip cookbook-theme.zip package`
end
