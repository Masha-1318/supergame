import tkinter as tk
import random

options = ["Камінь", "Ножиці", "Папір"]
user_score = 0
bot_score = 0

def play(user_choice):
    global user_score, bot_score
    bot_choice = random.choice(options)

  if user_choice == bot_choice:
        result = "Нічия!"
    elif (user_choice == "Камінь" and bot_choice == "Ножиці") or \
         (user_choice == "Ножиці" and bot_choice == "Папір") or \
         (user_choice == "Папір" and bot_choice == "Камінь"):
        result = "Ти виграв раунд!"
        user_score += 1
    else:
        result = "Бот виграв раунд!"
        bot_score += 1

  result_label.config(
        text=f"Ти: {user_choice}\nБот: {bot_choice}\n➡ {result}"
    )
    score_label.config(
        text=f"Рахунок: Ти {user_score} — {bot_score} Бот"
    )

window = tk.Tk()
window.title("Камінь — Ножиці — Папір")
window.geometry("350x380")
window.configure(bg="#e6f7ff")

tk.Label(window, text="Оберіть:", font=("Arial", 16), bg="#e6f7ff").pack(pady=10)

for opt in options:
    tk.Button(window, text=opt, font=("Arial", 12), width=15, command=lambda o=opt: play(o)).pack(pady=5)

result_label = tk.Label(window, text="", font=("Arial", 13), bg="#e6f7ff", fg="blue")
result_label.pack(pady=15)

score_label = tk.Label(window, text="Рахунок: Ти 0 — 0 Бот", font=("Arial", 13, "bold"), bg="#e6f7ff", fg="darkgreen")
score_label.pack(pady=5)

window.mainloop()
