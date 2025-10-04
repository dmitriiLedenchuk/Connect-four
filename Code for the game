#code 
# core game logic

#game loop
def main():
    board = create_board()
    current_player = 1  # Player 1 starts
    print("Welcome to Connect Four (6x7).")
    print(f"Enter a column number (1-{COLS}) to drop your piece, or 'q' to quit.")

    try:
        while True:
            print_board(board)
            piece = get_piece_for_player(current_player)

            # Read input
            user_input = input(f"Player {current_player} [{piece}], choose column (1-{COLS}): ").strip().lower()

            # Allow quitting
            if user_input == 'q':
                print("Game ended. Goodbye.")
                break

            # Basic input validation: must be an integer in range
            try:
                col = int(user_input) - 1  # convert to 0-based index
            except ValueError:
                print(f"Please type a number between 1 and {COLS}.")
                continue

            if col < 0 or col >= COLS:
                print(f"Column out of range. Try 1-{COLS}.")
                continue

            if not is_valid_location(board, col):
                print("That column is full.")
                continue

            # Make the move
            row = get_next_open_row(board, col)
            drop_piece(board, row, col, piece)

            # Check win
            if winning_move(board, piece):
                print_board(board)
                print(f"Player {current_player} [{piece}] wins!")
                break

            # Check draw
            if is_draw(board):
                print_board(board)
                print("It's a draw.")
                break

            # Next player's turn
            current_player = switch_player(current_player)

    except KeyboardInterrupt:
        # Clean exit on Ctrl+C
        print("\nInterrupted. Game ended.")


if __name__ == "__main__":
    main()

#additional features 
