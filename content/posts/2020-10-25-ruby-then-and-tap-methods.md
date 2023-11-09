+++
author = 'Volodymyr Yevtushenko'
categories = ['ruby']
date = 2019-10-25T20:32:00+02:00
description = 'Notes about tap and then'
tags = ['ruby']
title = 'Tap and then methods in ruby'
+++

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
