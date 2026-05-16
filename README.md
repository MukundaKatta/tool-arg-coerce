# tool-arg-coerce

[![crates.io](https://img.shields.io/crates/v/tool-arg-coerce.svg)](https://crates.io/crates/tool-arg-coerce)

Fix common type slips in LLM-generated tool arguments. `"42"`→`42`,
`"true"`→`true`, `["x"]`→`"x"`. Lossy and forgiving.

```rust
use tool_arg_coerce::{coerce_args, Type};
use serde_json::json;
let fixed = coerce_args(json!({"count": "42"}), &[("count", Type::Int)]);
assert_eq!(fixed["count"], json!(42));
```

MIT or Apache-2.0.
