# FROM fuzzers/go-fuzz:1.2.0
FROM golang:1.18 as builder

COPY . /rebecca
WORKDIR /rebecca

RUN go mod init github.com/dave/rebecca
RUN go get github.com/dave/gopackages
RUN go get github.com/dave/jennifer/jen

RUN go build cmd/becca/becca.go

FROM debian:bookworm-slim
COPY --from=builder /rebecca/becca /