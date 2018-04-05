# Exercise #15: Panic/Recover Middleware

[![exercise status: in progress](https://img.shields.io/badge/exercise%20status-in%20progress-yellow.svg?style=for-the-badge)](https://gophercises.com/exercises/recover)

## Exercise details

In the recover exercise we will be looking at the `panic` and `recover` mechanisms in Go and utilizing them to create middleware for an HTTP server.

Given a simple web server (see `main.go`) that can potentially panic, create an `http.Handler` that wraps the existing mux and will recover from any panics and then does the following:

1. Logs the error, as well as the stack trace.
2. Sets the status code to `http.StatusInternalServerError` (500) whenever a panic occurs.
3. Write a "Something went wrong" message when a panic occurs.
4. Ensure that partial writes and 200 headers aren't set even if the handler started writing to the `http.ResponseWriter` BEFORE the panic occurred (this one may be trickier)
5. If the environment is set to be development, print the stack trace and the error to the webpage as well as to the logs. Otherwise default to the "Something went wrong" message described in (3).

## Bonus

As a bonus exercises you can also look at ways to ensure you don't lose functionality like implementing the [http.Flusher](https://golang.org/pkg/net/http/#Flusher) or the [http.Hijacker](https://golang.org/pkg/net/http/#Hijacker) interfaces.
