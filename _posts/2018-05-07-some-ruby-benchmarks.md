---
layout: post
title:  "Ruby benchmarks"
date:   2018-05-07 14:13
comments: true
categories: ruby
---

### Loops and recursion:

```ruby
require 'benchmark/ips'

RubyVM::InstructionSequence.compile_option = {
  tailcall_optimization: true,
  trace_instruction: false
}

def rec_fact(n)
  return 1 if n <= 1
  n * rec_fact(n-1)
end

def tail_fact(n, acc=1)
  return acc if n <= 1
  tail_fact(n-1, n*acc)
end

def each_fact(n)
  total = 1
  (1..n).each do |n|
    total *= n   
  end
  total
end

def inject_fact(n)
  (1..n).inject(1, :*)
end

def forin_fact(n)
  raise InvalidArgument, "negative input given" if n < 0

  result = 1
  for i in (1..n) do
    result *= i
  end
  result
end

Benchmark.ips do |x|
  x.report('rec fact')  { rec_fact(1000) }
#  x.report('tail fact') { tail_fact(1000) }
  x.report('each fact') { each_fact(1000) }
  x.report('inject fact') { inject_fact(1000) }
  x.report('forin fact') { forin_fact(1000) }
  x.compare!
end
    
```

```
~/w/ruby> ruby recursion.rb
Warming up --------------------------------------
            rec fact   140.000  i/100ms
           tail fact   139.000  i/100ms
           each fact   148.000  i/100ms
         inject fact   136.000  i/100ms
          forin fact   151.000  i/100ms
Calculating -------------------------------------
            rec fact      1.584k (± 3.2%) i/s -      7.980k in   5.042005s
           tail fact      1.355k (± 5.2%) i/s -      6.811k in   5.040655s
           each fact      1.483k (± 6.3%) i/s -      7.400k in   5.012359s
         inject fact      1.521k (± 6.8%) i/s -      7.616k in   5.034439s
          forin fact      1.411k (±13.8%) i/s -      6.946k in   5.064435s

Comparison:
            rec fact:     1584.3 i/s
         inject fact:     1520.5 i/s 
           each fact:     1482.7 i/s 
          forin fact:     1410.9 i/s 
           tail fact:     1355.0 i/s - 1.17x  slower
```

### Attr reader and instance vars:

```ruby

require 'benchmark/ips'

class WithReader
  def initialize(name)
    @name = name
  end

  attr_reader :name

  def get_name
    name + ' bob'
  end
end

class WithoutReader
  def initialize(name)
    @name = name
  end

  def get_name
    @name + ' bob'
  end
end

Benchmark.ips do |x|
  x.report('Reader')  { WithReader.new('reader').get_name}
  x.report('Without') { WithoutReader.new('no reader').get_name }
  x.compare!
end

```


```
~/w/ruby> ruby class_test.rb
Warming up --------------------------------------
              Reader   111.107k i/100ms
             Without   120.671k i/100ms
Calculating -------------------------------------
              Reader      1.852M (±12.6%) i/s -      9.111M in   5.058722s
             Without      2.092M (±17.4%) i/s -      9.895M in   5.024920s

Comparison:
             Without:  2092257.0 i/s
              Reader:  1852263.3 i/s - same-ish: difference falls within error
```
