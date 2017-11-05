[![crates.io](https://img.shields.io/crates/v/rusterpassword.svg)](https://crates.io/crates/rusterpassword)
[![API Docs](https://docs.rs/rusterpassword/badge.svg)](https://docs.rs/rusterpassword/)
[![Build Status](https://img.shields.io/travis/myfreeweb/rusterpassword.svg?style=flat)](https://travis-ci.org/myfreeweb/rusterpassword)
[![unlicense](https://img.shields.io/badge/un-license-green.svg?style=flat)](http://unlicense.org)

# rusterpassword

A [Rust] implementation of the [Master Password algorithm], created for [freepass].

Uses [secstr] secure strings and [libsodium] through [sodiumoxide]'s underlying `libsodium-sys`.

Also includes a C API for calling from other languages.

[Rust]: https://www.rust-lang.org
[Master Password algorithm]: https://ssl.masterpasswordapp.com/algorithm.html
[freepass]: https://github.com/myfreeweb/freepass
[secstr]: https://github.com/myfreeweb/secstr
[libsodium]: https://github.com/jedisct1/libsodium
[sodiumoxide]: https://github.com/dnaq/sodiumoxide

## Usage

```rust
extern crate secstr;
extern crate rusterpassword;
extern crate sodiumoxide;

use sodiumoxide;
use secstr::*;
use rusterpassword::*;

fn main() {
    sodiumoxide::init();
    let master_key = gen_master_key(SecStr::from("Correct Horse Battery Staple"), "Cosima Niehaus").unwrap();
    let site_seed = gen_site_seed(&master_key, "twitter.com", 5).unwrap();
    let password = gen_site_password(site_seed, TEMPLATES_MAXIMUM);
}
```

## Contributing

Please feel free to submit pull requests!

By participating in this project you agree to follow the [Contributor Code of Conduct](http://contributor-covenant.org/version/1/4/).

[The list of contributors is available on GitHub](https://github.com/myfreeweb/rusterpassword/graphs/contributors).

## License

This is free and unencumbered software released into the public domain.  
For more information, please refer to the `UNLICENSE` file or [unlicense.org](http://unlicense.org).
