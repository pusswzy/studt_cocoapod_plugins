source 'https://rubygems.org'

path = Pathname.new(__FILE__ ).realpath
dir = File.dirname(path)

gem 'cocoapods', path: "#{dir}/CocoaPods-master"
gem 'cocoapods-project-hmap', path: "#{dir}/cocoapods-project-hmap-main"
gem 'cocoapods-lee_anything', path: "#{dir}/cocoapods-lee_anything"

# 这个不知道是为啥
group :debug do
	gem 'debase'
	gem 'ruby-debug-ide'
end