source ENV['GEM_SOURCE'] || "https://rubygems.org"

def location_for(place)
  if place =~ /^((?:git[:@]|https:)[^#]*)#(.*)/
    [{ :git => $1, :branch => $2, :require => false }]
  elsif place =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  else
    [place, { :require => false }]
  end
end

gem 'vanagon', *location_for(ENV['VANAGON_LOCATION'] || '~> 0.15.17')
gem 'packaging', *location_for('git://github.com/ciprianbadescu/packaging#maint/add-ubuntu2004-arm64' || '~> 0.99.43')
gem 'artifactory'
gem 'rake'
gem 'json'
gem 'octokit'
gem 'rubocop', "~> 0.34.2"

eval_gemfile("#{__FILE__}.local") if File.exist?("#{__FILE__}.local")
