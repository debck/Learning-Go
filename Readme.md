This is just a simple readme where I have jotted down my learning of Golang.

## Contents

* [Basic Hello World](#Basic-Hello-World)
* [Creating HTTP Server]()
* [Creating Routes]()
* [Adding Forms]()
* [Adding MiddleWare]()
* [Sessions Management]()
* [Adding Database]()
* [Working with Websockets]()
* [templating Engines]()


## Basic Hello World

```go
package main

import (
    "fmt"
    "net/http"
)

func main() {
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Hello, you've requested: %s\n", r.URL.Path)
    })

    http.ListenAndServe(":80", nil)
}
```