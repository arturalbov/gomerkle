# gomerkle

[![version](https://img.shields.io/github/release/arturalbov/gomerkle.svg)](https://github.com/arturalbov/gomerkle/releases/latest)
[![Coverage Status](https://coveralls.io/repos/github/arturalbov/gomerkle/badge.svg?branch=master)](https://coveralls.io/github/arturalbov/gomerkle?branch=master)
[![Go Report Card](https://goreportcard.com/badge/github.com/arturalbov/gomerkle)](https://goreportcard.com/report/github.com/arturalbov/gomerkle)
[![LoC](https://tokei.rs/b1/github/arturalbov/gomerkle)](https://github.com/arturalbov/gomerkle)
[![license](https://img.shields.io/github/license/arturalbov/gomerkle.svg)](https://github.com/arturalbov/gomerkle/blob/master/LICENSE)
[![contributors](https://img.shields.io/github/contributors/arturalbov/gomerkle.svg)](https://github.com/arturalbov/gomerkle/graphs/contributors)
[![contribute](https://img.shields.io/badge/contributions-welcome-orange.svg)](https://github.com/arturalbov/gomerkle/graphs/contributors)
[![telegram](https://img.shields.io/badge/Telegram-%40arturalbov-blue.svg?style=social&logo=telegram)](https://t.me/arturalbov)

Golang merkle tree implementation based on [RFC-6962](https://tools.ietf.org/html/rfc6962#section-2.1) standard.

```
import "github.com/arturalbov/gomerkle"
```
## Usage

```go
package main

import (
	"crypto/sha256"
	"fmt"
	"github.com/arturalbov/gomerkle/merkle"
)

func main() {
	tree := merkle.NewTree(sha256.New())

	data := [][]byte{
		[]byte("Audrey Garza"),
		[]byte("Jan Neal"),
		[]byte("Kelly Taylor"),
		[]byte("Henrietta Oliver"),
		[]byte("Rebecca Stewart"),
		[]byte("Johnny Ross"),
		[]byte("Mark Reese"),
		[]byte("Holly Robertson"),
		[]byte("Jaime Davidson"),
		[]byte("Leo Montgomery"),
	}

	tree.BuildNewWithData(data)

	tree.Push([]byte("Karen Rice"))
	tree.Push([]byte("Van Briggs"))
	tree.Push([]byte("Eunice Greene"))

	proofs := tree.GetIndexProofs(2)

	fmt.Println(tree.ValidateIndexByProofs(2, data[2], proofs))
}
```

## Issues

If you have any problems with or questions about this package, please contact us
through a [GitHub issue](https://github.com/arturalbov/gomerkle/issues).

## Contributing

You are invited to contribute new features, fixes, or updates, large or small;
I am always thrilled to receive pull requests, and do my best to process them
as fast as I can.