#
# MULTI-STAGE IMAGE
#
FROM golang AS builder

WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
# compila la app de go y ademas las librerias necesarias para ejecutarlo en otras distribuciones linux
RUN CGO_ENABLED=0 go build -a -installsuffix cgo -o go-app .

FROM alpine

WORKDIR /app
COPY --from=builder /app/go-app ./

EXPOSE 8080

CMD ./go-app
