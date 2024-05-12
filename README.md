## Rust Web Server

`The main purpose of using [Rust](https://www.google.com) is enhanced safety, speed, and concurrency, or the ability to run multiple computations parallelly. In simple words, Rust is used for three essential purposes in programming: performance, safety, and memory management.`

```bash
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    git clone https://github.com/fc0101/rust-web-server.git
    cargo run
```

`Port : 127.0.0.1:7878`

```rust
    let listener = TcpListener::bind("127.0.0.1:7878").unwrap();
    let pool = ThreadPool::new(4);

    for stream in listener.incoming().take(2) {
        let stream = stream.unwrap();

        pool.execute(|| {
            handle_connection(stream);
        });
    }
```
