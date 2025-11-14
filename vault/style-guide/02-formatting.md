I like to leverage both `editorconfig` and `rustfmt`. They have different but related purposes.
- editorconfig keeps consistent indentation style and width, handles line endings, trailing white spaces and newlines.
- rustfmt keeps consistent line width, brace styles, and spacing.

> `.editorconfig`

```dotfile
# To learn more about .editorconfig see https://aka.ms/editorconfigdocs
# top-most EditorConfig file
root = true
###############################
# Core EditorConfig Options   #
###############################
# All files
[*]
insert_final_newline = true
indent_style = space
indent_size = 4
trim_trailing_whitespace = true

###############################
# Rust files                  #
###############################
[*.rs]
insert_final_newline = true
```

> `rustfmt.toml`

```toml
# To learn more about rustfmt.toml see https://rust-lang.github.io/rustfmt
hex_literal_case = "Upper"
```