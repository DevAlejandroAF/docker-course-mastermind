FROM rust AS builder
WORKDIR /app
COPY . .
RUN cargo build --release

FROM debian:bookworm
WORKDIR /app
COPY --from=builder /app/target/release/hello ./
EXPOSE 3000
CMD ./hello
