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

### intX to intY
if X < Y
``` go
i := int32(10)
j := int64(i)
```

if X > Y, be careful the overflow
``` go
i := int(3545298788787)
j := int8(i)
fmt.Println(j)  // -77     overflowed!
```

### string to float
Use the strconv.ParseFloat function to parse a string as a floating-point number with the precision specified by bitSize: 32 for float32, or 64 for float64.
``` go
f := "3.14159265"
if s, err := strconv.ParseFloat(f, 32); err == nil {
    fmt.Println(s) // 3.1415927410125732
}
if s, err := strconv.ParseFloat(f, 64); err == nil {
    fmt.Println(s) // 3.14159265
}
```

### float to string
``` go
strconv.FormatFloat(f float64, fmt byte, prec, bitSize int) string
```



### string to big.Int
``` go
bi := new(big.Int)
bi, ok := bi.SetString(str, 10)
if !ok {
	return nil, errors.New("string to bigint convert error")
}
return bi, nil
```

### string to []string
``` go
strings.Split(str string, seperator string) []string
```

## []string to string
``` go
strings.Join(arr []string, seperator string) string
```

### big.Int to string
``` go
bigint := big.NewInt(123)
bigstr := bigint.String()
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


