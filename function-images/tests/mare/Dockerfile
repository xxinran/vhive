FROM vhiveease/golang-builder AS builder
WORKDIR /vhive
COPY . .
WORKDIR /vhive/function-images/tests/mare
RUN go build -o driver .

FROM vhiveease/runner
RUN apt-get update && apt-get install -y ca-certificates
COPY --from=builder /vhive/function-images/tests/mare/driver /usr/local/bin/driver
ENTRYPOINT [ "/usr/local/bin/driver" ]
