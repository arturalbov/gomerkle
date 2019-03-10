# gomerkle

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