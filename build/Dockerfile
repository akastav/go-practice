# stage 1: build
FROM golang:1.20 as build
LABEL stage=intermediate
WORKDIR /app
COPY . .
RUN make build

# stage 2: scratch
FROM scratch as scratch
COPY --from=build /app/bin/go-practice /bin/go-practice
CMD ["go-practice"]
