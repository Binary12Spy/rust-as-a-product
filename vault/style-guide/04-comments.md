Outside of the usual doc-strings, comments *inside* a function are important as well.

Comments should be clear, concise, and meaningful.
The goal is to treat code as a product: someone will read it, someone will maintain it, and clarity is non-negotiable.
# General guidelines
- Prefer expressive code over comments when possible.
- Explain “why,” not just “what.” We can often read the “what” from the code.
- Write comments for business rules, design constraints, non-obvious decisions, or edge cases.
- Write comments as if explaining to a future teammate.
- Avoid duplicitous comments ("increment i by one"; we can read code).
# Commonly useful inline comments
## Business logic reasoning
```rust
// Grace period is required due to partner API accepting late-duration tokens
let grace_ms = 500;
```
## Design reasoning
```rust
// Avoiding clone() here to reduce memory pressure during high load
let user_id = extract_user_id(&message_metadata)?;
```
## `unsafe` use and clippy overrides
```rust
#[allow(clippy::too_many_arguments)]
// This function is called once in startup and is easier to read with full config
fn create_app_context(...) { ... }

// Required due to interaction with C FFI where lifetime annotations can't be relied on
unsafe {
    call_external_api(ptr);
}
```
# Patterns to avoid
- No-op comments: `let result = 3 + 1; // add 3 and 1`
- Commenting out large unused code blocks — rely on version control.
- In-joke or ambiguous comments: `// well... it works 😅`