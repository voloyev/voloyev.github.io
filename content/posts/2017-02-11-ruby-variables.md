+++
categories = ['ruby', 'variables']
date = 2017-02-11T13:11:00+02:00
title = 'About variables in ruby'
description = 'Fun with vars'
+++


```ruby
#  Local
	
v = "Ruby"
# => "Ruby"
 
v.class
# => String
 
v.kind_of? String
# => true
 
defined? v
# => "local-variable"

# Instance
	
@i = "Ruby"
# => "Ruby"
 
defined? @i
# => "instance-variable"

# Global

$g = "Ruby"
# => "Ruby"
 
defined? $g
# => "global-variable"

# Constant

C = "Ruby"
# => "Ruby"
defined? C
# => "constant"
```
