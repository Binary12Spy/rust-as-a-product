I like to have strong restrictive linting - forcing me to maintain consistent patterns, leaving nothing uncertain.

# If using a Workspace

> Root workspace `Cargo.toml` (enforces lints across all crates)
```toml
[workspace.lints.rust]
missing_docs = "deny"          # Ensure all public items are documented
unused_must_use = "deny"       # Prevent accidentally ignoring important return values

[workspace.lints.clippy]
unwrap_used = "deny"           # Avoid panics in production code
expect_used = "deny"           # See above
panic = "deny"                 # Forces handling errors reliably
```

> Each project's `Cargo.toml` then must inherit formatting
```toml
[lints]
workspace = true
```

## If a single project
```toml
[lints.rust]
missing_docs = "deny"          # Ensure all public items are documented
unused_must_use = "deny"       # Prevent accidentally ignoring important return values

[lints.clippy]
unwrap_used = "deny"           # Avoid panics in production code
expect_used = "deny"           # See above
panic = "deny"                 # Forces handling errors reliably
```
