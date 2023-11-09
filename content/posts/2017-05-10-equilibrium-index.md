+++
categories = ['ruby']
date = 2017-05-10T23:22:00+02:00
title = 'Equgilibrium index'
description = 'Equgilibrium index in python and ruby'
+++


```ruby
def equilib(list)
  left, right = 0, list.reduce(:+)
  equilib_list = []
  
  list.each_with_index do |val, i|
    right -= val
    # puts i.to_s + ' :' +val.to_s if right == left
    equilib_list << i if left == right
    left += val
  end
  return -1 if equilib_list.empty?
  equilib_list[0]
end

p equilib([-1, 3, -4, 5, 1, -6, 2, 1])
```

## ruby whith while ##

```ruby
def eq(arr)
right = arr.reduce(:+) # sum of all elements in array
left = 0
i = 0
while i < arr.len
  right -= arr[i]
  puts i if left == right 
  left += arr[i]
  i+=1
end

p eq([-1, 3, -4, 5, 1, -6, 2, 1])
```

## and python ##

```python
def eqilibrium_index(list):
    left = 0
    right = sum(list)
    i = 0
    eq = []
    while(i < len(list)):
        right -= list[i]
        if(right == left):
            eq.append(i)
        left += list[i]
        i += 1
    if(len(eq) == 0):
        return -1
    else:
        return eq[0]
```
