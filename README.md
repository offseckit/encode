# >_ osk encode

**Encode and decode text with 24+ operations — Base64, URL, Hex, HTML, and more with chaining.**

Part of [OffSecKit](https://offseckit.com) | [Browser version](https://offseckit.com/tools/encode) | [Unified CLI](https://github.com/offseckit/cli)

## Install

This tool is part of the OffSecKit CLI toolkit:

```bash
pip install offseckit
```

## Usage

```bash
# Base64 encode
osk encode -o base64-encode "Hello World"

# Chain: Base64 then URL encode
osk encode -o base64-encode -o url-encode "test payload"

# Double URL encode for WAF bypass
osk encode -o url-encode -o url-encode "<script>alert(1)</script>"

# Pipe from stdin
echo "secret" | osk encode -o hex-encode

# List all operations
osk encode list
```

## Related

- [OffSecKit CLI](https://github.com/offseckit/cli) — full toolkit (`pip install offseckit`)
- [Browser version](https://offseckit.com/tools/encode) — use in your browser
- [Encoding Guide](https://offseckit.com/blog/encoding-decoding-pentest-guide) — practical techniques for pentesters

## License

MIT
