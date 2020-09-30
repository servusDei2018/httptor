# httptor.go
Use tor with `http.DefaultClient`. Make sure you have tor running on `localhost:9050`.

Install using:
```
go get github.com/servusDei2018/httptor
```

Import it:
```
import _ "github.com/servusDei2018/httptor"
```

## Example
```
package main

import (
	"io"
	"log"
	"net/http"
	"os"

	_ "github.com/servusDei2018/httptor"
)

func main() {
	resp, err := http.Get("https://check.torproject.org/api/ip")
	if err != nil {
		log.Fatal(err)
	}
	defer resp.Body.Close()

	if _, err := io.Copy(os.Stdout, resp.Body); err != nil {
		log.Fatal(err)
	}
}
```
