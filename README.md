# Tic Tac Toe - Networked and AI Game 🎮

This project implements a Tic Tac Toe game with both networked multiplayer 🌐 and single-player modes 🤖, allowing players to compete against each other over a network or against an AI opponent. It includes a server component to manage networked game states and client applications for players to interact with the game.

## Features

*   **Networked Gameplay:** Play Tic Tac Toe against another player over a network. 🤝
*   **AI Opponent:** Play Tic Tac Toe against an AI (Minimax Algorithm). 🧠
*   **Game Lobby:** Players can create new games or join existing ones (Networked Mode). 🚪
*   **Real-time Updates:** Game board updates are synchronized between players in real-time (Networked Mode). 🔄
*   **Error Handling:** Handles disconnections and invalid moves gracefully (Networked Mode). ⚠️
*   **Simple UI:** Uses Pygame for a basic and intuitive graphical interface. ✨

## Technologies Used

*   **Python:** The primary programming language. 🐍
*   **Sockets:** Used for network communication between the server and clients (Networked Mode). 📡
*   **Pygame:** Used for creating the graphical user interface. 🎨
*   **Threading:** Used on the server to handle multiple client connections concurrently (Networked Mode). 🧵
*   **Pickle:** Used for serializing and deserializing game board data (Networked Mode). 📦
*   **Minimax Algorithm:** Used for AI opponent in single-player mode. 🤔

## Requirements

*   Python 3.x
*   Pygame (`pip install pygame`)

## Setup and Installation

1.  **Clone the repository:**

    ```
    git clone [repository URL]
    cd [repository directory]
    ```

2.  **Install Pygame:**

    ```
    pip install pygame
    ```

## Usage

### Single-Player Mode (Against AI) 🤖

1.  Start the Client:

    ```
    python client.py
    ```

2.  Select "Play against AI".
3.  Play the game against the AI opponent. ❌⭕

### Multi-Player Mode (Networked) 🌐

1.  **Start the Server:**

    ```
    python server.py
    ```

    The server will start listening for connections on `127.0.0.1:8000` by default (or the IP you configured).

2.  **Start the Clients:**

    Run two instances of the client application:

    ```
    python client.py
    ```

3.  **Game Play:**

    *   In one client, choose to create a new game ("Host Game"). This client will be player X. A game ID will be displayed.
    *   In the other client, choose to join the existing game ("Join Game") and enter the game ID provided by the first client. This client will be player O.
    *   Players take turns clicking on the game board to make their moves.
    *   The game automatically detects a win, loss, or tie and displays the result. 🎉

## File Structure

*   `server.py`: Contains the server-side logic for managing game states and client connections (Networked Mode).
*   `client.py`: Contains the client-side logic for interacting with the server (Networked Mode), handling the AI opponent (Single-Player Mode), and rendering the game board.
*   `tictactoe.py`: Contains the core Tic Tac Toe game logic (e.g., checking for wins, making moves, AI using Minimax, etc.).
*   `OpenSans-Regular.ttf`: Font file used by Pygame for text rendering.
*   `README.md`: This file. ℹ️

## Code Overview

### `server.py`

*   **`TicTacToeServer` Class:**
    *   Handles client connections using sockets (Networked Mode).
    *   Manages game states (board, players) (Networked Mode).
    *   Uses threading to handle multiple games concurrently (Networked Mode).
    *   Implements methods for creating new games, joining games, and processing player moves (Networked Mode).
*   **`handle_client` Method:**
    *   Receives requests from clients to create or join a game (Networked Mode).
    *   Calls `handle_game_moves` to manage the actual gameplay (Networked Mode).
*   **`handle_game_moves` Method:**
    *   Receives and validates player moves (Networked Mode).
    *   Updates the game board (Networked Mode).
    *   Sends updated board states to both players (Networked Mode).
    *   Checks for game over conditions (win, loss, tie) (Networked Mode).

### `client.py`

*   **Pygame Initialization:** Sets up the Pygame window and fonts.
*   **Game Mode Selection:** Allows the player to select between playing against another player or the AI.
*   **`connect_to_server` Function:** Establishes a connection to the game server (Networked Mode).
*   **`create_game` Function:** Sends a request to the server to create a new game (Networked Mode).
*   **`join_game` Function:** Sends a request to the server to join an existing game (Networked Mode).
*   **`listen_for_messages` Function:** Runs in a separate thread, listening for messages from the server (board updates, game over messages, etc.) (Networked Mode).
*   **`process_messages` Function:** Processes messages received from the server and updates the game state accordingly (Networked Mode).
*   **AI Integration:** When playing against the AI, the client uses the `tictactoe.py` functions to determine the AI's move.
*   **Game Loop:** Handles user input (mouse clicks), updates the game board, and renders the UI using Pygame.

### `tictactoe.py`

*   **Core Game Logic:** Contains functions for:
    *   `initial_state()`: Returns the initial state of the board.
    *   `player(board)`: Returns which player has the next turn.
    *   `actions(board)`: Returns all legal moves.
    *   `result(board, action)`: Returns the board state after a move is made.
    *   `winner(board)`: Returns the winner of the game (X or O) or None if there is no winner. 🏆
    *   `terminal(board)`: Returns True if the game is over, False otherwise.
    *   `utility(board)`: Returns the utility of the board.
    *   `minimax(board)`: Implements the Minimax algorithm to determine the optimal move for the AI.

## Future Enhancements

*   **Improved UI:** Enhance the graphical interface with better graphics and user experience. ➕
*   **AI Difficulty Levels:** Implement different difficulty levels for the AI opponent.
*   **Game Lobby Browser:** Add a lobby browser to easily find and join available games (Networked Mode).
*   **More Robust Error Handling:** Implement more comprehensive error handling and recovery mechanisms (Networked Mode).
*   **Security:** Implement security measures to prevent cheating and unauthorized access (Networked Mode). 🛡️

## Contributing

Contributions are welcome! 🤝 Please fork the repository and submit a pull request with your changes.

## License

[Choose a license, e.g., MIT License] 📜

---

**Note:** Replace `[repository URL]` with the actual URL of your GitHub repository and `[repository directory]` with the name of the directory created when cloning. Also, choose a suitable license for your project. Remember to update the `host` variable in `client.py` to the correct IP address of the server if they are running on different machines (Networked Mode). Make sure the client can choose which game to play.
