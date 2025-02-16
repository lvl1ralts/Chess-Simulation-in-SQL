# Chess Simulation in C/C++ and SQL

## Overview
This project is a Chess game simulator written in C and C++ that reads moves from a CSV file, simulates the game, and stores all the moves in an SQL database. The program generates SQL `INSERT` commands to store the moves, making it useful for analysis and record-keeping.

## Features
- Reads chess moves from a CSV file.
- Simulates the game based on the provided moves.
- Generates SQL `INSERT` statements to store all moves in a database.
- Supports standard chess notation including:
  - `+` for check
  - `#` for checkmate
  - `x` for captures
  - `O-O` for kingside castling
  - `O-O-O` for queenside castling
- Can be used for game analysis, logging, or replaying past games.

## Prerequisites
To run this project, you need:
- A C or C++ compiler (e.g., `gcc`, `g++`)
- SQLite or any SQL database to execute the generated `INSERT` commands
- A CSV file containing chess moves in the expected format

## Installation & Compilation
1. Clone the repository:
   ```sh
   git clone https://github.com/lvl1ralts/Chess-Simulation-in-SQL.git
   cd Chess-Simulation-in-SQL
   ```
2. Compile the C program:
   ```sh
   gcc chess_simulation.c -o chess_simulation
   ```
   Or compile the C++ program:
   ```sh
   g++ chess_simulation.cpp -o chess_simulation
   ```

## Usage
1. Prepare a CSV file with chess moves in the expected format.
2. Run the program, providing the CSV file as input:
   ```sh
   ./chess_simulation moves.csv
   ```
3. The program will:
   - Parse the moves from the CSV file.
   - Simulate the game.
   - Output SQL `INSERT` commands to store moves in a database.

## Database Integration
To store the moves in an SQL database:
1. Run the program and redirect the output to a file:
   ```sh
   ./chess_simulation moves.csv > moves.sql
   ```
2. Execute the generated SQL script in your database:
   ```sh
   sqlite3 chess.db < moves.sql
   ```
   or for MySQL:
   ```sh
   mysql -u username -p database_name < moves.sql
   ```

## Example CSV Format
Ensure your input CSV file follows this structure:
```
WhiteMove,BlackMove
Nf3,Nf6
g3,d5
Bg2,e6
O-O,Be7
d3,O-O
Qd1xQd8+,Kd8
...
```

## Example Board Representation
Before Move:
```
0 0 0 0 0 0 R 0
0 0 0 0 0 p 0 0
0 0 0 0 p k 0 P
p 0 r 0 0 0 p 0
0 p P 0 b 0 0 0
0 0 0 0 P 0 0 0
P 0 0 K 0 0 0 0
0 0 R 0 0 0 0 0
```
Move: `Rf1+`
After Move:
```
0 0 0 0 0 0 R 0
0 0 0 0 0 p 0 b
0 0 0 0 p k 0 P
p 0 r 0 0 0 p 0
0 p P 0 0 0 0 0
0 0 0 0 P 0 0 0
P 0 0 K 0 0 0 0
0 0 R 0 0 0 0 0
```
