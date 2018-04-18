---
layout: post
title:  "Go interfaces"
date:   2018-04-18 13:33
comments: true
categories: go, pointers
---

```go
import (
    "fmt"
    "strings"
)

type animal interface {
    greet() string
}

type cat struct {name string}
type dog struct {name string}


func main() {
    bob := cat{name: "Bob"}
    doge := dog{name: "Doge"}
    fmt.Println(bob.greet())
    fmt.Println(doge.greet())
}

func (c cat) greet() string {
    s := []string{c.name, "meow"}
	return strings.Join(s, ",")
}

func (d dog) greet() string {
    voice := make([]string, 3)

    for i,_ := range(voice) {
        voice[i] = d.name
    }

    return strings.Join(counter, ",")
}

```

- interface is *not* a `generic`
- interface is implicit
- inerface is a contract to help us manage types
- interface is tough
