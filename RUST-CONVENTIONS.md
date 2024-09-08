# Rust conventions

## Tooling

### Linting

Use Rust's `Clippy` with our custom setting to ensure your code follows our conventions. Please lint and format often and before pushing code. If the linter finds issues with the code, the CI/CD will fail and the pull requests will not be pulled until the issues are resolved.

### Building

While not specifically connected to Rust, our go-to build tool is currently the famous `make`. If you are writing `Makefile`-s please ensure that it runs on Windows as well. Be aware: Cross-platform `Makefile`-s are a separate art form.

## Coding

### C ABI

Please make all public functions and types `extern "C"` and `#[repr(C)]` respectively. You can also alternatively provide a C ABI equivalent to the public native Rust function alongside it to fulfill the FFI compatibility requirements we have for this new kernel. 

### Comments

## Assembly

Both **inline** and **separate**.
