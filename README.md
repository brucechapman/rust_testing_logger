# rust_testing_logger [![Status][status-img]][status-url]
A Rust library to support testing of code that uses Log crate.
## Example
```rust_testing_logger#[macro_use]
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
