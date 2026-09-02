# Mega Tic-Tac-Toe

A browser-based **Mega Tic-Tac-Toe** game: a large 3×3 board made up of nine smaller 3×3 Tic-Tac-Toe boards. Your move in a small board determines which small board your opponent must play in next.

🎮 **Play online:** https://azp3001.github.io/tictactoe/

## Features

- 🧩 **Mega Tic-Tac-Toe** — play across nine nested Tic-Tac-Toe boards.
- 👥 **Local multiplayer** — two players can play on the same device.
- 🌐 **Online multiplayer** — create a game, share its code/link, or join an open game.
- 🔵 **Blue vs. Orange** — Blue plays `X`; Orange plays `O`.
- ▶️ **Choose who starts** before a game begins.
- 🔄 **New Game / Leave Game** controls for restarting or leaving an online match.
- 📱 **Responsive interface** designed for desktop and mobile browsers.
- ⚡ **Single-file app** — the UI, styling, and game logic live in `index.html`.

The repository currently contains a single application file, `index.html`, plus GitHub Actions configuration.

## How to Play

Mega Tic-Tac-Toe follows the standard nested-board rules:

1. The game contains **9 small Tic-Tac-Toe boards** arranged as a 3×3 mega board.
2. Make a move in any available cell of the current small board.
3. The position of that cell determines the **next small board** your opponent must play in.
4. Winning a small board claims that position on the mega board.
5. Win three claimed small boards in a row horizontally, vertically, or diagonally to win the overall game.
6. A small board that fills without a winner is treated as a draw. Once the target small board has already been decided, the next player may play in any available small board.

The implementation tracks nine 3×3 boards, restricts moves to the active board, resolves completed small boards, and checks the resulting 3×3 mega board for the final winner or draw.

## Online Multiplayer

Online play is implemented in the browser with **PeerJS 1.5.4**. The app creates a peer for each player, supports a lobby/open-game list, and also supports joining directly with a game code. The game can generate a shareable URL containing the game code.

### Create a Game

1. Open the [live game](https://azp3001.github.io/tictactoe/) or run the app locally.
2. Choose **Online**.
3. Create a game.
4. Share the displayed game code or generated link with the other player.
5. The host plays as **X / Blue** and the joining player plays as **O / Orange**.

### Join a Game

Use the open-games list or enter the host's game code to join directly.

> Online functionality requires an internet connection because the app loads PeerJS from a CDN and uses peer-to-peer networking.

## Tech Stack

| Technology | Purpose |
| --- | --- |
| HTML5 | Page structure and game UI |
| CSS3 | Responsive styling, layout, and visual effects |
| Vanilla JavaScript | Game state, rules, UI interaction, and networking logic |
| PeerJS 1.5.4 | Browser-to-browser online multiplayer |
| GitHub Pages | Public web deployment |

PeerJS is loaded from `unpkg.com`, with a jsDelivr fallback if the primary CDN is unavailable.

## Project Structure

```text
tictactoe/
├── .github/
│   └── workflows/    # GitHub Actions configuration
└── index.html        # Complete game application
```

## Development Notes

The project is intentionally lightweight: there is no frontend framework and no dependency installation step. Most of the application is contained directly in `index.html`, including the styles, DOM structure, game engine, and PeerJS networking code.

When working on the game logic, keep these core state concepts in mind:

- `boards` — the nine inner 3×3 boards.
- `boardStatus` — the result of each inner board (`X`, `O`, or draw).
- `activeBoard` — the small board in which the next move is allowed.
- `currentPlayer` — the player whose turn it is.
- `gameOver` — whether the mega board has reached a final result.

These states are used by the implementation to validate moves and render the game.

## Contributing

Contributions are welcome. For larger changes, open an issue first to discuss the proposed direction, then submit a pull request.

When contributing, please keep the project dependency-light and test both local and online gameplay where the change affects networking or turn synchronization.

## Deployment

The repository is configured for GitHub Pages and is currently published at:

**https://azp3001.github.io/tictactoe/**

The project is a static web application, so deployment does not require a backend application server.

## License

No `LICENSE` file is currently visible in the repository. Add a license file if you want to explicitly define how others may use, modify, and redistribute the project.

## Repository

https://github.com/AZP3001/tictactoe
