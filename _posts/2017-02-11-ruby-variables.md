---
layout: post
title:  "About variables in ruby"
date:   2017-02-11 13:11
comments: true
categories: ruby variables
---

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
