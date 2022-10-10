# Golang Notes

Using this repo to store stuff while I got through the Golang tutorial from their [docs](https://go.dev/doc/).

## Module and workspace stuff
* You need to do `go mod init source-name/module-name` in your module so it creates `go.mod` file. 
* To add new dependencies you do `go mod tidy` which I think it's a pretty neat command.
* If you use vs code the same way I do, opening a parent dir to several modules, Go doesn't get it unless you tell it to. So you run `go work init` in the parent dir and `go work use ./module-name` to add any modules.
* Whenever you add local modules you can do `go mod edit -replace source -name/module-name=../module-dir-name` in your current module

**NOTE**: `source-name`has to be something that Go can download from, such as github

## Slices
* Basically a piece of an array that takes low and high bounds: `a[low:high]`. It includes the first element and excludes the last: `a[1:4]` includes elements 1 through 3 of a.
* Slices do not store any data, they just point to a section of the underlying array, but changes made to the slices go through to the array and other slices that may point to the same data.
* Ommitting any bound defaults to zero for the low bound and the slice length for the high bound.
* Python has this, but I can't recall if they give it a name.

## Maps
* Can be declare as a variable type, or initialized with a `make` function:
```
var m map[string]int //map of string keys with int values
```
As they state in their docs:
> Map types are reference types, like pointers or slices, and so the value of m above is nil; it doesn’t point to an initialized map. A nil map behaves like an empty map when reading, but attempts to write to a nil map will cause a runtime panic.

The preferred way to initialize maps is with the `make` function:
```
m = make(map[string]int)
```
* Using maps
```
m["example_key"] = 10 // adds a key called "example_key" that has a value of 10

i :=m["example_key"] // retrieves the value of "example_key" and assigns it to a new variable i

j :=m["non_existant_key"] // if a key does not exist we get that type's zero value, since value type is int, we get j==0

n :=len(m) // retrieves number of items in map

delete(m, "route") // removes an entry from a map

for key,value := range m{ // iterate through maps
    fmt.Println("Key:", key, "Value:", value)
}
```
