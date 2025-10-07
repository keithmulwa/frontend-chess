### Mchezo wa Sataranji (Chess Game)
A full-stack chess application built with React and Flask, featuring AI opponent gameplay, user authentication, and game state persistence.

### 🎮 Features
Interactive Chess Gameplay: Full chess implementation with all piece movements
AI Opponent: Play against a computer opponent (blue pieces)
User Authentication: Secure login and registration system
Game Persistence: Save and resume games automatically
Real-time Move Validation: Valid moves highlighted during piece selection
Swahili UI: User interface in Swahili language
Visual Indicators: Move indicators showing regular moves and captures

### 📁 Project Structure
chess-app/
├── src/
│   ├── components/
│   │   ├── board.jsx          # Main game board component
│   │   ├── login.jsx           # User login page
│   │   ├── register.jsx        # User registration page
│   │   ├── aiLogic.jsx         # AI move selection logic
│   │   └── moveLogic.jsx       # Move generation coordinator
│   ├── pieces/
│   │   ├── index.jsx           # Piece component factory
│   │   ├── pawn.jsx            # Pawn piece logic
│   │   ├── rook.jsx            # Rook piece logic
│   │   ├── knight.jsx          # Knight piece logic
│   │   ├── bishop.jsx          # Bishop piece logic
│   │   ├── queen.jsx           # Queen piece logic
│   │   └── king.jsx            # King piece logic
│   ├── assets/                 # Chess piece images and backgrounds
│   ├── css/                    # Styling files
│   ├── App.jsx                 # Main app router
│   └── main.jsx                # React entry point


### 🚀 Getting Started
## Prerequisites

Node.js (v14 or higher)
npm or yarn
Flask backend server running on http://127.0.0.1:5000

## Installation

Clone the repository

bash   git clone <repository-url>
   cd chess-app

## Install dependencies

bash   npm install

Required npm packages

bash   npm install react react-dom react-router-dom axios

Start the development server

bash   npm run dev

Ensure Flask backend is running

The application expects a Flask backend at http://127.0.0.1:5000
Required endpoints are documented below



### 🎯 How to Play

Register/Login: Create an account or login with existing credentials
Game Board: You play as white pieces (bottom), AI plays as blue pieces (top)
Making Moves:

Click on your piece to see valid moves (highlighted squares)
Click on a highlighted square to move
Captures are indicated with red indicators


AI Response: After your move, the AI will automatically respond after 5 seconds
Coordinate System: Board uses [x,y] coordinates (0-7 for both axes)

### 🔧 Technical Details
Coordinate System

X-axis: 0-7 (left to right)
Y-axis: 0-7 (top to bottom)
Blue pieces: Rows 0-1 (top of board)
White pieces: Rows 6-7 (bottom of board)

Piece Movement Logic
Each piece has its own movement calculation function:

Pawn: Forward movement, diagonal captures, promotion, en passant
Rook: Horizontal and vertical sliding
Knight: L-shaped jumps
Bishop: Diagonal sliding
Queen: Combined rook and bishop movement
King: One square in any direction

Move Types

move: Regular movement to empty square
capture: Taking an opponent's piece
promotion-move: Pawn reaching end rank (empty square)
promotion-capture: Pawn capturing while promoting
en-passant: Special pawn capture

### 🔌 Backend API Endpoints
The application requires these Flask endpoints:
Authentication
Register User
POST /user/add
Body: { username, email, password }
Response: { user: {...}, token: "..." }
Login User
POST /user/login
Body: { email, password }
Response: { user: {...}, token: "..." }
Game Management
Create/Resume Game
POST /game/create
Headers: { Authorization: "Bearer <token>" }
Body: { user_id: <id> }
Response: { 
  game_id: <id>, 
  message: "New game created" | "Existing game resumed",
  game_state: "[{x, y, color, type}, ...]"
}
Make Move
POST /move/<game_id>
Headers: { Authorization: "Bearer <token>" }
Body (Player): { 
  player: "white", 
  from_x, from_y, 
  to_x, to_y 
}
Body (AI): { 
  player: "blue" 
}
Response: { 
  game_state: "[...]",
  current_turn: "white" | "blue",
  player_move: {...},
  ai_turn_next: boolean
}
Game State Format
javascript[
  { x: 0, y: 0, color: "blue", type: "rook" },
  { x: 1, y: 0, color: "blue", type: "knight" },
  // ... more pieces
]


### 🎨 Styling
The application uses custom CSS with:

Alternating white and blue tiles
Selected piece highlighting
Valid move indicators
Player labels with avatars
Responsive layout

### 🔐 Authentication

JWT tokens stored in localStorage
Token included in all authenticated requests
Automatic token retrieval on page load
Logout clears user session and token

### 🤖 AI Logic
Current implementation:

Random move selection from all valid moves
Evaluates all pieces and their legal moves
Can be extended for more sophisticated algorithms (minimax, alpha-beta pruning)

### 📝 State Management

React useState hooks for game state
Board state synchronized with backend
Automatic game state loading on component mount
Turn-based state updates

### 🐛 Known Limitations

No check/checkmate detection on frontend
No castling implementation shown
AI uses random selection (no strategic evaluation)
No move history display
localStorage used for token (consider more secure alternatives for production)

### 🔮 Future Enhancements

 Check and checkmate detection
 Castling implementation
 Move history/replay
 AI difficulty levels
 Game timer
 Player statistics
 Multiplayer support
 Stalemate detection
 Pawn promotion UI
 Sound effects

## 📄 License
Its For Educational Purposes under Moringa School

👥 Contributors
Shainnah Mugure, Eric Mbithi, Allan Kingori and Keith Mulwa.
