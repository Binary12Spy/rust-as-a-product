I find writing doc-strings that are concise while conveying all of the information a future maintainer would need to feel comfortable after a read-through or two to be cathartic.

## File Headers
Each Rust source file would begin with a copyright (if applicable):
```rust
// Copyright (c) YourCompany YYYY and later.
// All rights reserved.
// This program is proprietary software; you may not redistribute it or modify it without permission.
```
## Crate-Level and Module Documentation
Use `//!` style at the top of lib.rs, main.rs, mod.rs, and other module files.

```rust
//! # CrateName
//!
//! [High-level description of the crate or binary’s responsibilities and goals]
```
## Public Modules
Even if a module just exposes sub-modules, mod.rs must include documentation.
```rust
/// Submodule one
pub mod submodule_one;
/// Submoodule two
pub mod submodule_two;
```
## Public Re-exports (pub use)
When re-exporting modules or types via pub use, add comments explaining their purpose.
```rust
// Used by clients in config setup
pub use crate::internal::important_service;
```
## Structs
Use `///`. Describe the struct’s purpose, responsibilities, and public fields.
```rust
/// Represents a network packet decoded from raw bytes.
struct Packet {
    /// Raw payload data.
    pub payload: Vec<u8>,
    /// Timestamp of when the packet was received.
    pub timestamp: u64,
}
```
## Enums
Document the enum and each variant.
```rust
/// Represents the current status of a connection.
enum ConnectionStatus {
    /// Connection is initializing and not ready.
    Initializing,
    /// Connection is active and ready to send data.
    Connected,
    /// Connection has been closed.
    Disconnected,
}
```
## Constants
Document usage and semantics.
```rust
/// Maximum number of attempts before giving up a retry.
const MAX_RETRY_ATTEMPTS: u32 = 5;
```
## Methods and Functions
Document with details including purpose, parameters, results, panics, examples, and safety concerns.
```rust
/// Attempts to connect to the server using the provided configuration.
///
/// # Parameters
/// - `config`: Configuration for the connection.
///
/// # Returns
/// A `Result` indicating success or failure.
///
/// # Example
/// ```rust, ignore
/// let client = Client::connect(config)?;
/// ```
///
/// # Panics
/// This function panics if the configuration is invalid.
///
/// # Safety
/// This method is safe and does not perform any unsafe operations.
fn connect(config: Config) -> Result<Client, Error> {
}
```
## Trait Implementations
Document the reason or behavior when implementing traits, especially for external traits.
```rust
/// Implements equality comparison based on ID.
impl PartialEq for Person {
    fn eq(&self, other: &Self) -> bool {
        self.id == other.id
    }
}
```
## Implementations
Implementations define a logically grouped API, add a high-level comment to describe the functionality.
```rust
/// Implements core methods for working with TCP Streams.
impl TcpStream {
    // method definitions
}
```
## Macros
Document use cases and generated code examples for reusable macros.
```rust
/// Logs a value with its expression and returns it unchanged.
/// Useful for inline debugging.
///
/// # Example
/// ```rust
/// let x = dbg_value!(some_computation());
/// ```
#[macro_export]
macro_rules! dbg_value {
    // implementation
}
```
## Unit Tests
Use inline module-level doc to describe purpose or special setup for unit tests.
```rust
/// Tests for the account module logic.
#[cfg(test)]
mod unit_tests {
    use super::*;
}
```