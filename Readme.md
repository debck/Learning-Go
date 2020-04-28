
<h2 align="center">Learning</h2>
<h3 align="center">A simple readme with list of concepts to be covered to <strong>learn Go language</strong> and also <strong>code snippets helping in using golang in Web Development</strong></h3>

## Contents
* [Concepts to learn before diving into Web](#Initial-Concepts-List)
* [Basic Hello World](#Basic-Hello-World)
* [Creating HTTP Server]()
* [Creating Routes]()
* [Adding Forms]()
* [Adding MiddleWare]()
* [Sessions Management]()
* [Adding Database]()
* [Working with Websockets]()
* [Templating Engines]()




## Initial Concepts List

* Basic Understanding of
    * Variables
    * Constants
    * Packages and import/export
    * Functions
    * Pointers
    * Mutability
 * Types
    * Type Conversion 
    * Type assertion**
    * Structs
    * Composition
 * Collection Types
   * 





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