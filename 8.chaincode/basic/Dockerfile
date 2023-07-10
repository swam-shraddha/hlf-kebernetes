# This image is a microservice in golang for the Degree chaincode
FROM golang:1.17.7 AS build

COPY ./ /go/src/github.com/marbles
WORKDIR /go/src/github.com/marbles
RUN ls
# Build application
RUN go build -o chaincode -v .

# Production ready image
# Pass the binary to the prod image
FROM alpine:3.11 as prod

COPY --from=build /go/src/github.com/marbles/chaincode /app/chaincode
RUN ls

USER 1000

WORKDIR /app
RUN ls /app/chaincode
CMD ./chaincode
