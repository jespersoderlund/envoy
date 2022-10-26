FROM golang:alpine@sha256:845f16d6c1c1501505a9f35978494bcd77a03f4f0cfeef56e3d8788325bea4a3 AS builder

RUN apk --no-cache add make
COPY . /app
RUN make -C /app/grpc-service

FROM alpine@sha256:bc41182d7ef5ffc53a40b044e725193bc10142a1243f395ee852a8d9730fc2ad

COPY --from=builder /app/grpc-service/server /app/server
CMD ["/app/server", "-users", "/etc/users.json"]
