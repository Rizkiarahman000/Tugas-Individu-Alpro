import time
import os

class NQueensSolver:
    def __init__(self, n=4, delay=0.6):
        self.n = n
        self.board = [['.' for _ in range(n)] for _ in range(n)]
        self.delay = delay
        self.solutions = 0

    def clear_screen(self):
        os.system('cls' if os.name == 'nt' else 'clear')

    def print_board(self, row=None, col=None, message=""):
        self.clear_screen()
        print("=" * (self.n * 4))
        print(f"N-Queens Backtracking Visualization (N = {self.n})")
        print("=" * (self.n * 4))
        if message:
            print(message)
        print()

        for r in range(self.n):
            for c in range(self.n):
                if r == row and c == col:
                    print(f"[{self.board[r][c]}]", end=" ")
                else:
                    print(f" {self.board[r][c]} ", end=" ")
            print()
        print()
        time.sleep(self.delay)

    def is_safe(self, row, col):
        # cek kolom di atas
        for i in range(row):
            if self.board[i][col] == 'Q':
                return False

        # cek diagonal kiri atas
        i, j = row - 1, col - 1
        while i >= 0 and j >= 0:
            if self.board[i][j] == 'Q':
                return False
            i -= 1
            j -= 1

        # cek diagonal kanan atas
        i, j = row - 1, col + 1
        while i >= 0 and j < self.n:
            if self.board[i][j] == 'Q':
                return False
            i -= 1
            j += 1

        return True

    def solve(self, row=0):
        # jika semua queen berhasil ditempatkan
        if row == self.n:
            self.solutions += 1
            self.print_board(message=f"Solusi ditemukan! Total solusi: {self.solutions}")
            return True

        found_solution = False

        for col in range(self.n):
            self.print_board(row, col, f"Mencoba menempatkan queen di baris {row+1}, kolom {col+1}")

            if self.is_safe(row, col):
                self.board[row][col] = 'Q'
                self.print_board(row, col, f"AMAN -> Queen ditempatkan di ({row+1}, {col+1})")

                if self.solve(row + 1):
                    found_solution = True

                # backtracking
                self.board[row][col] = '.'
                self.print_board(row, col, f"BACKTRACK -> Queen di ({row+1}, {col+1}) dihapus")
            else:
                self.print_board(row, col, f"TIDAK AMAN -> posisi ({row+1}, {col+1}) ditolak")

        return found_solution


def main():
    print("=== Program N-Queens dengan Backtracking ===")
    try:
        n = int(input("Masukkan jumlah queen / ukuran papan (misal 4): "))
        delay = float(input("Masukkan delay visualisasi dalam detik (misal 0.5): "))
    except ValueError:
        print("Input tidak valid. Program memakai default N=4 dan delay=0.5")
        n = 4
        delay = 0.5

    solver = NQueensSolver(n, delay)
    result = solver.solve()

    solver.clear_screen()
    print("=" * 35)
    print("HASIL AKHIR")
    print("=" * 35)
    if result:
        print(f"Ditemukan {solver.solutions} solusi untuk N = {n}")
    else:
        print(f"Tidak ada solusi untuk N = {n}")

if __name__ == "__main__":
    main()
