
<h2 align="center">Learning</h2>
<h3 align="center">A simple readme with list of concepts to be covered to <strong>learn Go language</strong> and also <strong>code snippets helping in using golang in Web Development</strong></h3>

## Contents
* [Concepts to learn before diving into Web](#Initial-Concepts-List)
* [Basic Hello World](#Basic-Hello-World)
* [Adding static assets](#Adding-static-asset)
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
    * Arrays





## Basic Hello World

```go
package main

import (
    "fmt"
    "net/http"
)

func main() {
    http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Hello, World !")
    })

    http.ListenAndServe(":8000", nil)
}
```


## Adding static asset

```go
func main() {
    http.HandleFunc("/", func (w http.ResponseWriter, r *http.Request) {
        fmt.Fprintf(w, "Hello World!")
    })
   
    fs := http.FileServer(http.Dir("assets/"))
    http.Handle("/static/", http.StripPrefix("/static/", fs))

    http.ListenAndServe(":8000", nil)
}
```

## Adding Routes

```go
package main

import (
    "fmt"
    "encoding/json"
    "net/http"
    "github.com/gorilla/mux"
)


type Tasks struct {
    ID 			string  	`json:"id,omitempty"`
    TASKNAME 	string 		`json:"task,omitempty"`
}

var task []Tasks

func getAllTask(w http.ResponseWriter, r *http.Request) {
	json.NewEncoder(w).Encode(task)
}


func getTask(w http.ResponseWriter, r *http.Request) {
	params := mux.Vars(r)
	for _,item := range task {
		if item.ID == params["id"] {
			json.NewEncoder(w).Encode(item)
			return
		}
	}
	json.NewEncoder(w).Encode(&Tasks{})
}


func main() {
   router := mux.NewRouter()
	router.HandleFunc("/task", getAllTask).Methods("GET")
	router.HandleFunc("/task/{id}", getTask).Methods("GET")

    http.ListenAndServe(":8000", router)
}

```