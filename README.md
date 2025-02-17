This is the single-file web interface for Picocrypt for offline use. You can save `index.html` anywhere and it will run offline.

**You will probably want to use https://picocrypt.github.io (https://github.com/Picocrypt/picocrypt.github.io) instead for more safety checks and reliability.**

# Compiling
To build the web interface from source, you will need to compile the Go code into a WebAssembly file:
```
GOOS=js GOARCH=wasm go build -ldflags="-s -w" index.go
```
This will create a binary file. Compress it with [LZMA](https://github.com/LZMA-JS/LZMA-JS), encode it in Base64, and paste the final result to [L198](https://github.com/Picocrypt/Web/blob/main/index.html#L198).

You'll also need to update [`wasm_exec.js`](https://cdn.jsdelivr.net/gh/golang/go@go1.24.0/lib/wasm/wasm_exec.min.js) (replace the Go version accordingly) on [L197](https://github.com/Picocrypt/Web/blob/main/index.html#L197) to glue everything together.
