---
layout: post
title: Tap and then
date: 2020-10-25 20:32
category: ruby
author: Volodymyr Yevtushenko
tags: ["ruby"]
summary: Notes about tap and then
---

In nutshell #then return result of a block and #tap returns self

```ruby
class Person
  def initialize(name:, email:)
    @name = name
    @email = email
  end
  attr_accessor :name, :email
end

Person.new(name: "Bob", email: "bob@example.com")
.then {|person| EmailTemplate.for(person.name, person.email)}
.then {|template| Email.notify(template)}

bob_for_tap = Person.new(
  name: "Bob for Tap", email: "bob_for_tap@example.com"
)
.tap {|persone| Verificator(person)}
# so at the end of block we return instance of Person
```
