FROM golang:1.22-bullseye AS build

WORKDIR /app

COPY go.mod ./
COPY go.sum ./

RUN go mod download

COPY server.go ./

RUN go build -o /my-app

FROM gcr.io/distroless/base-debian11

COPY --from=build /my-app /my-app

CMD ["/my-app"]