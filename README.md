class TicTacToe:
    def __init__(self):
        self.board = [[' ' for _ in range(3)] for _ in range(3)]
        self.current_player = 'X'

    def print_board(self):
        for row in self.board:
            print('|'.join(row))
            print('-' * 5)

    def make_move(self, row, col):
        if self.board[row][col] == ' ':
            self.board[row][col] = self.current_player
            self.current_player = 'O' if self.current_player == 'X' else 'X'
        else:
            print('Invalid move! Try again.')

    def is_winner(self):
        # Check rows
        for row in self.board:
            if row[0] == row[1] == row[2] != ' ':
                return True

        # Check columns
        for col in range(3):
            if self.board[0][col] == self.board[1][col] == self.board[2][col] != ' ':
                return True

        # Check diagonals
        if self.board[0][0] == self.board[1][1] == self.board[2][2] != ' ':
            return True
        if self.board[0][2] == self.board[1][1] == self.board[2][0] != ' ':
            return True

        return False

    def is_board_full(self):
        for row in self.board:
            if ' ' in row:
                return False
        return True

    def play(self):
        print('Welcome to Tic-Tac-Toe!')
        print('Player 1: X')
        print('Player 2: O')
        print('To make a move, enter the row and column numbers (0-2).')

        while True:
            self.print_board()

            row = int(input('Enter the row: '))
            col = int(input('Enter the column: '))

            self.make_move(row, col)

            if self.is_winner():
                self.print_board()
                print(f'Player {self.current_player} wins!')
                break
            elif self.is_board_full():
                self.print_board()
                print("It's a tie!")
                break

if __name__ == '__main__':
    game = TicTacToe()
    game.play()
