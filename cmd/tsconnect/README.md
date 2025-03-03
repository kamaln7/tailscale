# tsconnect

The tsconnect command builds and serves the static site that is generated for
the Tailscale Connect JS/WASM client.

## Development

To start the development server:

```
./tool/go run ./cmd/tsconnect dev
```

The site is served at http://localhost:9090/. JavaScript and CSS changes can be picked up with a browser reload. Go changes (including to the `wasm` package) require the server to be stopped and restarted. In development mode the state the Tailscale client is stored in `sessionStorage` and will thus survive page reloads (but not the tab being closed).

## Deployment

To build the static assets necessary for serving, run:

```
./tool/go run ./cmd/tsconnect build
```

To serve them, run:

```
./tool/go run ./cmd/tsconnect serve
```

By default the build output is placed in the `dist/` directory and embedded in the binary, but this can be controlled by the `-distdir` flag. The `-addr` flag controls the interface and port that the serve listens on.
