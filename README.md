DiffParser
===========
[![GoDoc](https://img.shields.io/badge/godoc-reference-blue.svg)](https://godoc.org/github.com/RickLeee/diffparser)

DiffParser is a Golang package which parse's a git diff.

Install
-------

```sh
go get github.com/RickLeee/diffparser
```

Usage Example
-------------

```go
package main

import (
	"fmt"
	"github.com/RickLeee/diffparser"
)

// error handling left out for brevity
func main() {
	byt, _ := ioutil.ReadFile("example.diff")
	diff, _ := diffparser.Parse(string(byt))

	// You now have a slice of files from the diff,
	file := diff.Files[0]

	// diff hunks in the file,
	hunk := file.Hunks[0]

	// new and old ranges in the hunk
	newRange := hunk.NewRange

	// and lines in the ranges.
	line := newRange.Lines[0]
}
```

More Examples
-------------

See diffparser_test.go for further examples.
