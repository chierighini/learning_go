# Golang Notes

Using this repo to store stuff while I got through the Golang tutorial from their [docs](https://go.dev/doc/).

## Module and workspace stuff
* you need to do `go mod init source-name/module-name` in your module so it creates `go.mod` file. 
* To add new dependencies you do `go mod tidy` which I think it's a pretty neat command.
* If you use vs code the same way I do, opening a parent dir to several modules, Go doesn't get it unless you tell it to. So you run `go work init` in the parent dir and `go work use ./module-name` to add any modules.
* whenever you add local modules you can do `go mod edit -replace source -name/module-name=../module-dir-name` in your current module

**NOTE**: `source-name`has to be something that Go can download from, such as github