## erace
erace is a flexible and lightweight in-memory cache package for Go, suitable for both single-cache applications and distributed systems with multiple clients.


Single Cache Example

```
package main

import (
	"fmt"
	"time"

	"github.com/anthdm/ggcache"
)

func main() {
	// Create a new cache instance
	cache := ggcache.New()

	// Set a key-value pair in the cache
	key := []byte("exampleKey")
	value := []byte("exampleValue")
	err := cache.Set(key, value, time.Second*30)
	if err != nil {
		fmt.Println("Error:", err)
	}

	// Get the value from the cache
	result, err := cache.Get(key)
	if err != nil {
		fmt.Println("Error:", err)
	} else {
		fmt.Println("Value:", string(result))
	}

	// Check if a key exists in the cache
	if cache.Has(key) {
		fmt.Println("Key exists in the cache.")
	}

	// Delete a key from the cache
	err = cache.Delete(key)
	if err != nil {
		fmt.Println("Error:", err)
	}
}
```
