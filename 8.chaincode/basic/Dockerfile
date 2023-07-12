# This image is a microservice in golang for the Degree chaincode
FROM golang:1.20-alpine AS build

COPY ./ /go/src/github.com/marbles
WORKDIR /go/src/github.com/marbles

# Build application
RUN go build -o chaincode -v .

# Production ready image
# Pass the binary to the prod image
FROM alpine:3.11 as prod

USER 1000

COPY --from=build /go/src/github.com/marbles/chaincode /chaincode
#RUN ls /go/src/github.com/marbles/chaincode
RUN ls /chaincode

#USER nonroot:nonroot

#WORKDIR /app
#CMD ./chaincode
ENTRYPOINT ["/chaincode"]

