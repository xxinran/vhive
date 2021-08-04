FROM vhiveease/golang-builder AS builder
WORKDIR /vhive
COPY . .
WORKDIR /vhive/function-images/tests/mare/word-count
RUN go build -o bin/word-count .

FROM vhiveease/runner
RUN apt-get update && apt-get install -y ca-certificates
COPY --from=builder /vhive/function-images/tests/mare/word-count/word-count /usr/local/bin/word-count
ENTRYPOINT [ "/usr/local/bin/word-count" ]


