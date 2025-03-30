# game-project


def print_board(board):
    for row in board:
        print(" | ".join(row))
        print("-" * 9)

def play_tic_tac_toe():
    board = [[" ", " ", " "], [" ", " ", " "], [" ", " ", " "]]
    player = "X"

    for _ in range(9):  # Maximum 9 moves
        print_board(board)
        row = int(input(f"Player {player}, row (0-2): "))
        col = int(input(f"Player {player}, col (0-2): "))

        if board[row][col] == " ":
            board[row][col] = player
        else:
            print("That spot is taken!")
            continue #restart loop

        # Check win conditions (simplified)
        win_conditions = [
            board[0], board[1], board[2],  # Rows
            [board[0][0], board[1][0], board[2][0]], #cols
            [board[0][1], board[1][1], board[2][1]],
            [board[0][2], board[1][2], board[2][2]],
            [board[0][0], board[1][1], board[2][2]], #diagonal
            [board[0][2], board[1][1], board[2][0]]
        ]

        if [player, player, player] in win_conditions:
            print_board(board)
            print(f"Player {player} wins!")
            return

        player = "O" if player == "X" else "X" #switch player

    print_board(board)
    print("It's a draw!")

play_tic_tac_toe()
