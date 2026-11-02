# Chess Post-Mortem

A single-page chess game review: enter a Chess.com username and pick a game (or paste a PGN), and every move is graded by Stockfish 17.1 (brilliant, best, inaccuracy, mistake, blunder…), with accuracy, an estimated game rating, the engine's best line, and step-through playback. Everything runs in the browser; there is no server.

## Run locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000. (Opening `index.html` directly from disk won't load the engine; it needs to be served.)

## Deploy

Static site, no build step. On Cloudflare Pages: connect this repo, leave the build command empty, and set the output directory to `/`.

## Credits and licenses

- **Stockfish 17.1** (lite, single-threaded WebAssembly build), GNU GPL v3. `sf17-lite.wasm` is an unmodified binary from the [`stockfish` npm package](https://www.npmjs.com/package/stockfish) ([stockfish.js](https://github.com/nmrugg/stockfish.js)); engine source: https://github.com/official-stockfish/Stockfish. The loader script is fetched from unpkg at runtime. See `NOTICE-stockfish.md`.
- **Stockfish 10** (asm.js fallback), GPL v3, loaded from jsDelivr.
- **chess.js** 0.10.3, BSD-2-Clause, loaded from cdnjs.
- **Pieces:** "cburnett" by Colin M.L. Burnett, CC BY-SA 3.0.
