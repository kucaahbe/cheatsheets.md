---
tags:
  - languages
---
### cli handlig

```ruby
#!/usr/bin/env ruby
ARGV.each do|a|
  puts "Argument: #{a}"
end

STDERR.puts
input = gets.chomp

abort "optional msg" unless input == 'yes'
```

### heredoc

https://ruby-doc.org/core-2.5.0/doc/syntax/literals_rdoc.html
do not use `<<HEREDOC`

```ruby
a = 1
query = <<-HTML.chomp # without trailing newline
  #{a}
  Article about heredocs

HTML

# with indentation:
  query = <<-HTML.chomp # without trailing newline
  #{a}
  Article about heredocs

HTML
```

interpolation disabled:
```ruby
doc = <<-'TIME'
Current time is #{Time.now}
TIME
```


### Profiling
start:
```ruby
require 'profile'

# not sure about this (this is for cases when needed to profile some long running code but no time to wait when it finishes)
Signal.trap("INT") do
  puts 'bye'
  File.open('_profile.txt', 'w') do |f|
    Profiler__.print_profile(f)
  end
  exit
end
```
or
```shellsession
ruby -rprofile script.rb
ruby -rprofile -S some_executable
```

## Gems
uninstall all gems
```sh-session
gem uninstall -aIx
```

compare gems versions:
```ruby
if Bundler.environment.specs['rails'][0].version < Gem::Version.new('5')
```

Find gem path

```ruby
Gem::Dependency.new('rails').to_spec.full_gem_path
#=> "/home/kuca/.rbenv/versions/1.9.3-p194/gemsets/candi/gems/rails-3.1.8"
```

## Misc

parse cookies:
```ruby
cookies = CGI::Cookie::parse(raw_cookie)
  .inject({}) { |data, (k,v)| data.merge(k => v.value.first) }
```
