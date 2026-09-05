# GS1 Barcode & Digital Link Decoder — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-gs1-decoder.svg)](https://crates.io/crates/stanzaapi-gs1-decoder)
[![Documentation](https://docs.rs/stanzaapi-gs1-decoder/badge.svg)](https://docs.rs/stanzaapi-gs1-decoder)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Decode GS1 DataMatrix, GS1-128, FNC1 barcodes, and GS1 Digital Link URIs into structured JSON in sub-5ms.

Official high-performance, asynchronous Rust client library for **GS1 Barcode & Digital Link Decoder**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/gs1-decoder)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/gs1-decoder)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-gs1-decoder = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-gs1-decoder
```

---

## 🚀 Quickstart

```rust
use stanzaapi_gs1_decoder::Gs1DecoderClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    let client = Gs1DecoderClient::new(None, None);

    let response = client.validate("(01)00123456789012(21)12345").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "gtin": "00123456789012",
    "serial_number": "12345",
    "ai_elements": [
      {
        "ai": "01",
        "label": "GTIN",
        "value": "00123456789012"
      },
      {
        "ai": "21",
        "label": "SERIAL",
        "value": "12345"
      }
    ]
  }
}
```

---

## 🔗 Useful Links

* [GS1 Barcode & Digital Link Decoder Interactive Sandbox](https://stanzaapi.com/tools/gs1-decoder)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/stanzaapi/gs1-decoder-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
