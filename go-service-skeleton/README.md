# A simple REST service skeleton in Go

The service exposes a simple REST API

## Running Locally

Execute the following command for building the service

``` bash
make build
```

It will create an executable binary in the `bin` folder

## Testing

Each packages has its own unit tests written inside them.
Please run the following command to run all unit tests

``` bash
make test
```

## Push message

``` bash
curl -v --header "Content-Type: application/json" \
  --request POST \
  --data '{"text": "ama"}' \
  http://localhost:8080/api/v1/messages

curl -v --header "Content-Type: application/json" \
  --request POST \
  --data '{"text": "amad"}' \
  http://localhost:8080/api/v1/messages

curl -v --header "Content-Type: application/json" \
  --request GET \
  http://localhost:8080/api/v1/messages

curl -v --header "Content-Type: application/json" \
  --request GET \
  http://localhost:8080/health

curl -v --header "Content-Type: application/json" \
  --request GET \
  http://localhost:8080/metrics
```

## API endpoints

GET `/api/v1/messages` Returns all the messages

GET `/api/v1/messages/{id}` Returns a message with ID and also tells if the message is a palindrome or not

```js
{
"messageText": "Amore, roma",
"isPalindrome": "true"
}
```

POST `/api/v1/messages` Adds a new message to the list of messages to be requested later

DELETE `api/v1/messages{id}` Removes a message with ID or returns `404` if the message doesn't exist

### Observability

This is done through **_middlewares_** that are responsible for _logging_ every incoming request and attaches some metrics to the request. Also, every request is tagged with a unique ID (unless otherwise sent as part of request header `X-Request-ID` for **_tracing_** the request should anything go wrong with that request.
