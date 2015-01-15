# hipchat-go 

Go client library for the [HipChat API v2](https://www.hipchat.com/docs/apiv2).

[![GoDoc](https://godoc.org/github.com/tbruyelle/hipchat-go/hipchat?status.svg)](https://godoc.org/github.com/tbruyelle/hipchat-go/hipchat)
[![Build Status](https://travis-ci.org/tbruyelle/hipchat-go.svg??branch=master)](https://travis-ci.org/tbruyelle/hipchat-go)

Currently only a small part of the API is implemented, so pull requests are welcome.

### Usage

```go
import "github.com/tbruyelle/hipchat-go/hipchat"
```

Build a new client, then use the `client.Room` service to spam all the rooms you have access to (not recommanded):

```go
c := hipchat.NewClient("<your AuthToken here>")

rooms, _, err := c.Room.List()
if err != nil {
	panic(err)
}

notifRq := &hipchat.NotificationRequest{Message: "Hey there!"}

for _, room := range rooms.Items {
	_, err := c.Room.Notification(room.Name, notifRq)
	if err != nil {
		panic(err)
	}
}
```


---
The code architecture is hugely inspired by [google/go-github](github.com/google/go-github).


