# >_ encode

**Encoding/decoding multi-tool CLI — Base64, URL, Hex, HTML, and more with chaining.**

Part of [OffSecKit](https://offseckit.com) — free offensive security tools. Also available as a [browser tool](https://offseckit.com/tools/encode).

## Install

```bash
pip install offseckit-encode
```

Or clone and install locally:

```bash
git clone https://github.com/offseckit/encode.git
cd encode
pip install .
```

## Quick Start

```bash
# Encode to Base64
encode -o base64-encode "Hello World"

# Decode Base64
encode -o base64-decode "SGVsbG8gV29ybGQ="

# Chain operations: Base64 encode then URL encode
encode -o base64-encode -o url-encode "test payload"

# Pipe from stdin
echo "secret data" | encode -o hex-encode

# Show intermediate steps
encode -o base64-encode -o url-encode -o hex-encode "test" --steps
```

## Usage

```
encode [OPTIONS] [TEXT]
encode list [--category encode|decode]
```

## Options

| Flag | Description |
|---|---|
| `-o, --op` | Operation to apply (repeatable, chained in order) |
| `-i, --input` | Input text (alternative to positional arg) |
| `-s, --steps` | Show intermediate results for chained operations |
| `--help` | Show help |

## Commands

| Command | Description |
|---|---|
| `encode list` | List all available operations |
| `encode list -c encode` | List encoding operations only |
| `encode list -c decode` | List decoding operations only |

## Supported Operations

| Operation | ID |
|---|---|
| Base64 Encode | `base64-encode` |
| Base64 Decode | `base64-decode` |
| URL Encode | `url-encode` |
| URL Decode | `url-decode` |
| URL Encode (Full) | `url-encode-full` |
| Hex Encode | `hex-encode` |
| Hex Decode | `hex-decode` |
| Hex Encode (\x prefix) | `hex-encode-prefixed` |
| HTML Entity Encode | `html-encode` |
| HTML Entity Decode | `html-decode` |
| HTML Entity Encode (All) | `html-encode-all` |
| Unicode Escape | `unicode-escape` |
| Unicode Unescape | `unicode-unescape` |
| Binary Encode | `binary-encode` |
| Binary Decode | `binary-decode` |
| Decimal Encode | `decimal-encode` |
| Decimal Decode | `decimal-decode` |
| Octal Encode | `octal-encode` |
| Octal Decode | `octal-decode` |
| ROT13 | `rot13` |
| Reverse String | `reverse` |
| Uppercase | `uppercase` |
| Lowercase | `lowercase` |

## Examples

```bash
# Double URL encode for WAF bypass
encode -o url-encode -o url-encode "<script>alert(1)</script>"

# Decode multi-layer CTF flag
encode -o base64-decode -o hex-decode "NjE2YzY1NzI3NDI4MzEyOQ=="

# Hex encode shellcode-style
encode -o hex-encode-prefixed "/bin/sh"

# HTML entity encode for XSS
encode -o html-encode-all "<img src=x onerror=alert(1)>"

# ROT13
encode -o rot13 "Uryyb Jbeyq"

# Chain with intermediate steps
encode -o base64-encode -o url-encode -o hex-encode "payload" --steps
```

## Requirements

- Python 3.8+
- click

## Related

- [OffSecKit](https://offseckit.com) — free offensive security toolkit
- [Browser version](https://offseckit.com/tools/encode) — encode/decode in the browser with visual chaining
- [Encoding guide](https://offseckit.com/blog/encoding-decoding-pentest-guide) — practical encoding techniques for pentesters

## License

MIT
