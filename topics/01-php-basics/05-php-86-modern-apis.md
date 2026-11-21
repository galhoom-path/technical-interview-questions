# PHP 8.6 — what changed for professionals

> PHP examples use **PHP 8.6** syntax. Official: [release notes](https://www.php.net/releases/8.6/en.php) · [migration](https://www.php.net/manual/en/migration86.php)

**One-liner:** PHP 8.6 adds partial application, `clamp()`, `Time\Duration`, stronger stream/session defaults, and type-safer shared enums like `SortDirection` — write modern code, drop 8.6 deprecations early.

## Prefer (interview-ready)

| Prefer | Instead of |
|--------|------------|
| Partial application `version_compare(?, '8.6', '>=')` | Nested `fn ($v) => version_compare($v, ...)` noise |
| `clamp($v, $min, $max)` | `max($min, min($v, $max))` |
| `Time\Duration` for timeouts/backoff | Raw microsecond ints |
| Readonly property defaults | Constructor-only fixed getters |
| `SortDirection` in shared APIs | Magic `SORT_ASC` ints |
| Stream exception mode | `@file_get_contents` + `error_get_last()` |
| `#[\Override]` on constants / enum cases | Silent mismatches |

## Stop writing

- `return` inside `finally`
- `mb_ereg*` / `mb_split` → use `preg_*` + `u`
- `is_long` / `is_double` / `doubleval` → `is_int` / `is_float` / `floatval`
- `spl_object_hash()` → `spl_object_id()`
- Incomplete custom session handlers (need `create_sid` + `validateId`)

## Still true from 8.5 (do not re-attribute to 8.6)

- Pipe operator `\|>`
- `array_first()` / `array_last()`
- `clone($obj, [...])`
- `#[\NoDiscard]` + `(void)` cast

---

**Learn more:** [migration86.new-features](https://www.php.net/manual/en/migration86.new-features.php) · [migration86.deprecated](https://www.php.net/manual/en/migration86.deprecated.php)
