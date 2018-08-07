# testing_logger
A Rust library to support testing of code that uses `log` crate.

[![Version][version-img]][version-url] [![Documentation][doc-img]][doc-url]
![license][license-img]
[![Status][status-img]][status-url]
## Example

```rust
#[macro_use]
extern crate log;
use log::Level;
extern crate testing_logger;

#[test]
fn test_something() {
    testing_logger::setup();
    warn!("Something went wrong with {}", 10);
    testing_logger::validate( |captured_logs| {
        assert_eq!(captured_logs.len(), 1);
        assert_eq!(captured_logs[0].body, "Something went wrong with 10");
        assert_eq!(captured_logs[0].level, Level::Warn);
    });
}
```

[status-img]:https://travis-ci.com/brucechapman/rust_testing_logger.svg?branch=master
[status-url]:https://travis-ci.com/brucechapman/rust_testing_logger
[version-img]:https://img.shields.io/crates/v/testing_logger.svg
[version-url]:https://crates.io/crates/testing_logger
[doc-img]:https://docs.rs/testing_logger/badge.svg
[doc-url]:https://docs.rs/testing_logger
[license-img]:https://img.shields.io/crates/l/testing_logger.svg
