# stage 1: build
ARG GOLANG_IMAGE="golang:1.18"

FROM ${GOLANG_IMAGE} as build

LABEL stage=intermediate

WORKDIR /app

COPY . .

RUN make build

# stage 2: alpine
FROM alpine

LABEL stage=production

COPY --from=build /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs

COPY --from=build /app/bin/go-practice /usr/local/bin/

ENTRYPOINT ["go-practice"]
