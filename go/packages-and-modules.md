# 📦 Packages and Modules

- [📦 Packages and Modules](#-packages-and-modules)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📚 Concepts](#-concepts)
  - [🛠️ Let's Create a Simple Calculator Program](#️-lets-create-a-simple-calculator-program)
  - [🔐 Public and Private Identifiers](#-public-and-private-identifiers)

## 👀 Fast Lookup

- **Package**: Collection of Go files in the same directory
- **Module**: Collection of packages with `go.mod` file
- **`go mod init`**: Initialize a new module
- **Import path**: `modulename/packagename` format
- **Public identifiers**: Start with uppercase letter (exported)
- **Private identifiers**: Start with lowercase letter (unexported)
- **Main package**: Special package for executable programs
- **Package declaration**: `package name` at top of each .go file

## 📚 Concepts

- **Package** is a collection of Go files in the same directory.
- **Module** is a collection of packages.
- **Program** is a collection of main package and its dependencies.
- **Process** is a running instance of a program.

## 🛠️ Let's Create a Simple Calculator Program

```bash
go mod init simplecalc
```

This will create a `go.mod` file in current directory. `simplecalc` is the name of the module.

```plaintext
simplecalc/            # This is the root directory of the module (where go mod init simplecalc was executed)
├── go.mod             # Module definition file
├── main.go            # Main package file (main.go)
└── mymath/            # Directory for mymath package
    ├── add.go         # package mymath
    ├── subtract.go    # package mymath
    └── ...            # (Other files in the mymath package)
```

```go
package main

import (
  "fmt"
  "simplecalc/mymath" // simplecalc is the module name, mymath is the package name
)

func main() {
  sum := mymath.Add(1, 2)
  fmt.Println("1 + 2 =", sum)
}
```

## 🔐 Public and Private Identifiers

In Go, identifiers (names of variables, functions, types, etc.) are public if they start with a capital letter and private if they start with a lowercase letter.

```go
package mymath

func Add(a, b int) int {
  return a + b
}

func subtract(a, b int) int {
  return a - b
}
```

In the above code, `Add` is a public function and `subtract` is a private function.
