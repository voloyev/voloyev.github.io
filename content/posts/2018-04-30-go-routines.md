+++
categories = ['go']
date = 2018-04-30T13:16:00+02:00
title = 'Go routines'
description = 'snippet that demonstrates usage of goroutines'
+++

Lets look at folowing code

```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	links := []string{
		"http://google.co",
		"http://facebook.com",
		"http://golang.org",
		"http://cafephilo.lviv.ua",
		"http://http://10.6.193.162:3000/",
		"http://10.25.12.143:3000/",
	}

	for _, el := range links {
		checkLink(el)
	}
}

func checkLink(link string) {
	_, err := http.Get(link)
	if err != nil {
		fmt.Println(link, "it might be down")
		return
	}

	fmt.Println(link, "is up")
}

```

And think how we are going to make it more async.
