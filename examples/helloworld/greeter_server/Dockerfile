FROM golang:1.14.1 as builder
RUN CGO_ENABLED=0 go get github.com/grpc-ecosystem/grpc-health-probe
RUN CGO_ENABLED=0 go get github.com/buzzsurfr/grpc-examples/examples/helloworld/greeter_server

FROM scratch
COPY --from=builder /go/bin/grpc-health-probe /grpc-health-probe
COPY --from=builder /go/bin/greeter_server /greeter_server
EXPOSE 50051
CMD ["/greeter_server"]
