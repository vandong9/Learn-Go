# Tour
Learning golang

# Program
  Program start with package main
  

# Module
- Function init() will be call automatically at program startup, after global variables have been initialized.
- Funciton init is called after all the variable declarations in the package have evaluated their initializers, and those are evaluated only after all the imported packages have been initialized.
- A common use of init functions is to verify or repair correctness of the program state before real execution begins
- build module by command: go build,  the output if execute file BUT can not execute directly, Need to move to directory which install go (ex: /usr/local/go/bin) to be able to called

# Package
  command go mod init <module name> will create  go.mod
  go.mod : will auto update by adding new package that import by code file .go in this module (folder)
           can update by replace specify module with local module ex: replace example.com/greetings => ../greetings   (greeting is local module of package)
           will be updated again when build
  go.sum  is summary of package imported in this module
  
  package is cached in /Users/<current user>/go/pkg/mod/cache/download
  log.Fatal => cause app exit
  
  value wanted to export outside package need have name start with UPPERCASE character
  
# Scope

 
  
# Testing
  Go support build-in by package "testing"
  Test file need have suffix: \_test.go
  Function test with prefix "Test" and param is pointer testing.T  ex: func TestHelloEmpty(t \*testing.T){}
  Test with command: go test


# Some package
## fmt
  fmt.Sprintf => format string

## rand
  Before get random value, need set Seed   If not, it will return the last value

# Convention

## General
 - Should not use naked return
 - Import should group as ex:
  import (
	"fmt"
	"math"
)
## Package
  By convention, the package name is the same as the last element of the import path. For instance, the "math/rand" package comprises files that begin with the statement package rand.
