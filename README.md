# Golang type conversion quick reference

## Basic types
``` go
uint8       the set of all unsigned  8-bit integers (0 to 255)
uint16      the set of all unsigned 16-bit integers (0 to 65535)
uint32      the set of all unsigned 32-bit integers (0 to 4294967295)
uint64      the set of all unsigned 64-bit integers (0 to 18446744073709551615)

int8        the set of all signed  8-bit integers (-128 to 127)
int16       the set of all signed 16-bit integers (-32768 to 32767)
int32       the set of all signed 32-bit integers (-2147483648 to 2147483647)
int64       the set of all signed 64-bit integers (-9223372036854775808 to 9223372036854775807)

float32     the set of all IEEE-754 32-bit floating-point numbers
float64     the set of all IEEE-754 64-bit floating-point numbers

complex64   the set of all complex numbers with float32 real and imaginary parts
complex128  the set of all complex numbers with float64 real and imaginary parts

byte        alias for uint8
rune        alias for int32
```

## Other common types
``` go
big.Int
```

## Type conversion

### string to big.Int
``` go
package main

import (
	"fmt"
	"log"
	"math/big"
)

func main() {
	// The Scan function is rarely used directly;
	// the fmt package recognizes it as an implementation of fmt.Scanner.
	i := new(big.Int)
	_, err := fmt.Sscan("18446744073709551617", i)
	if err != nil {
		log.Println("error scanning value:", err)
	} else {
		fmt.Println(i)
	}
}
```

### int64 to big.Int
``` go
	bi := big.NewInt(int64Value)
```

### int32 to big.Int
``` go
	bi := big.NewInt(int64(int32Value))
```

### []byte to big.Int
``` go
import "math/big"
new(big.Int).SetBytes([]byte) 
```

### []byte to hex
``` go
import "github.com/ethereum/go-ethereum/common"
common.Bytes2Hex([]byte)
```

### uint64 to int64
``` go
int64(uint64)
```

### big.Int to big.Float
``` go
i := big.NewInt(12345)
f := new(big.Float).SetInt(i)
```

### big.Int to float64
``` go
// big.Int to big.Float first
i := big.NewInt(12345)
f := new(big.Float).SetInt(i)

// big.Float then to float64
todo:


