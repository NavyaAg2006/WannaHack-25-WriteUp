# Easy Sudoku
## Challenge Description
An nc command is given to us that gives us sudoku puzzles to solve. We have to solve 10 sudoku puzzles to get the flag.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/2d7b67bd-e645-4d4b-ba68-6aa39bcd5667" />

## Solution
In order to solve the sudoku puzzles efficiently, we write a code in cpp to solve sudoku puzzles. Which is

```cpp
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;

const int N = 9;

// Function to check if it's safe to place the number in the current cell
bool isSafe(vector<vector<int>>& board, int row, int col, int num) {
    // Check the row
    for (int i = 0; i < N; i++) {
        if (board[row][i] == num) return false;
    }

    // Check the column
    for (int i = 0; i < N; i++) {
        if (board[i][col] == num) return false;
    }

    // Check the 3x3 subgrid
    int startRow = row - row % 3, startCol = col - col % 3;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (board[i + startRow][j + startCol] == num) return false;
        }
    }
    return true;
}

// Function to solve the Sudoku using backtracking
bool solveSudoku(vector<vector<int>>& board) {
    for (int row = 0; row < N; row++) {
        for (int col = 0; col < N; col++) {
            if (board[row][col] == 0) {  // Empty cell
                for (int num = 1; num <= N; num++) {
                    if (isSafe(board, row, col, num)) {
                        board[row][col] = num;
                        if (solveSudoku(board)) {
                            return true;
                        }
                        board[row][col] = 0;  // Backtrack
                    }
                }
                return false;  // No valid number found
            }
        }
    }
    return true;  // All cells filled correctly
}

// Function to print the solved Sudoku board
void printBoard(const vector<vector<int>>& board) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cout << board[i][j] << " ";
        }
        cout << endl;
    }
}

int main() {
    vector<vector<int>> board(N, vector<int>(N));

    // Input the Sudoku board where '_' represents empty cells
    cout << "Enter the Sudoku puzzle (use '_' for empty cells):\n";
    string input;
    for (int i = 0; i < N; i++) {
        getline(cin, input);
        stringstream ss(input);
        for (int j = 0; j < N; j++) {
            char c;
            ss >> c;
            if (c == '_') {
                board[i][j] = 0;  // Empty cell is represented by 0
            } else {
                board[i][j] = c - '0';  // Convert character to integer
            }
        }
    }

    if (solveSudoku(board)) {
        cout << "Solved Sudoku puzzle:\n";
        printBoard(board);
    } else {
        cout << "No solution exists\n";
    }

    return 0;
}
```

now we just give the sudoku puzzles as input and get our solved puzzle and get the flag!
