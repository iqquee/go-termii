# Go-Termii

[Termii](https://developers.termii.com/) client application written in Go

## Usage

### Install Package

```bash
go get github.com/Uchencho/go-termii
```

### Documentation

Please see [the docs](https://developers.termii.com/) for the most up-to-date documentation of the Termii API.

#### TERMII

- Sample Usage

```go
package main

import (
    termii "github.com/Uchencho/go-termii"
    "log"
)

func main() {
    // Ensure TERMII_URL ends with '/' i.e 'https://termii.com/'
   var httpClient *http.Client

	termiiConfig := termii.Config{
		APIKey:   os.Getenv("TERMII_API_KEY"),
		BaseURL:  os.Getenv("TERMII_BASE_URL"),
		SenderID: os.Getenv("TERMII_SENDER_ID"),
	}

	client := termii.NewClient(termiiConfig, httpClient)

    req := termii.AutoGeneratedMessageRequest{
        To:  "2347066554433",
        Sms: "Hello from termii", // You do not need to set the API Key in this request struct
    }
    resp, err := client.SendAutoGeneratedMessage(req)
    if err != nil {
        log.Fatal("error in sending autogenerated message", err)
        return
    }
    log.Printf("Response : %+v", resp)
}

```

> **NOTE**
> Check the `client` directory to see a sample implementation and termii_test.go file to see sample tests
