### cli handlig

```ruby
#!/usr/bin/env ruby
ARGV.each do|a|
  puts "Argument: #{a}"
end

STDERR.puts
input = gets.chomp

abort "optiona msg" unless input == 'yes'
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
# 
```

interpolation disabled:
doc = <<-'TIME'
Current time is #{Time.now}
TIME
