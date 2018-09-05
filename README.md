# Golang type conversion quick reference

## Basic types
``` go
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32, represents a Unicode code point

float32 float64

complex64 complex128
```

## Other common types
big.Int

## Type conversion

### string

### int

### []byte2big.Int
``` go
import "math/big"
new(big.Int).SetBytes([]byte) 
```

### []byte2hex
``` go
import "github.com/ethereum/go-ethereum/common"
common.Bytes2Hex([]byte)
```
