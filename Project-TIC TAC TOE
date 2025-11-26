import tkinter as tk

from tkinter import messagebox



# Main window

root = tk.Tk()

root.title("Tic Tac Toe - 2 Players")

root.geometry("420x500")

root.config(bg="#1e1e1e")



# Global variables

current_player = "X"

buttons = []



# Label showing turn

turn_label = tk.Label(root, text="Player 1 (X) Turn", font=("Arial", 20, "bold"),

                      bg="#1e1e1e", fg="white")

turn_label.pack(pady=20)



# Frame for the board

frame = tk.Frame(root, bg="#1e1e1e")

frame.pack()



# Function to check for winner

def check_winner():

    # Rows

    for i in range(3):

        if buttons[i][0]["text"] == buttons[i][1]["text"] == buttons[i][2]["text"] != "":

            return True



    # Columns

    for i in range(3):

        if buttons[0][i]["text"] == buttons[1][i]["text"] == buttons[2][i]["text"] != "":

            return True



    # Diagonals

    if buttons[0][0]["text"] == buttons[1][1]["text"] == buttons[2][2]["text"] != "":

        return True

    if buttons[0][2]["text"] == buttons[1][1]["text"] == buttons[2][0]["text"] != "":

        return True



    return False



# Function to check for draw

def check_draw():

    for row in buttons:

        for btn in row:

            if btn["text"] == "":

                return False

    return True



# Button click handler

def on_click(row, col):

    global current_player



    if buttons[row][col]["text"] == "":

        buttons[row][col]["text"] = current_player

        buttons[row][col].config(fg="cyan" if current_player == "X" else "orange")



        # Check winner

        if check_winner():

            winner = "Player 1 (X)" if current_player == "X" else "Player 2 (O)"

            messagebox.showinfo("Game Over", f"{winner} wins!")

            reset_board()

            return



        # Check draw

        if check_draw():

            messagebox.showinfo("Game Over", "It's a Draw!")

            reset_board()

            return



        # Switch player

        current_player = "O" if current_player == "X" else "X"

        turn_label.config(text=f"Player {1 if current_player=='X' else 2} ({current_player}) Turn")



# Create 3x3 grid of buttons

for row in range(3):

    row_buttons = []

    for col in range(3):

        btn = tk.Button(frame, text="", font=("Arial", 32, "bold"),

                        width=3, height=1, bg="#333333", fg="white",

                        command=lambda r=row, c=col: on_click(r, c))

        btn.grid(row=row, column=col, padx=10, pady=10)

        row_buttons.append(btn)

    buttons.append(row_buttons)



# Reset function

def reset_board():

    global current_player

    current_player = "X"

    turn_label.config(text="Player 1 (X) Turn")



    for row in buttons:

        for btn in row:

            btn.config(text="", fg="white")



# Reset button

reset_btn = tk.Button(root, text="Reset Game", font=("Arial", 16, "bold"),

                      bg="#444444", fg="white", command=reset_board)

reset_btn.pack(pady=20)



root.mainloop()
