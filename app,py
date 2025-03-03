import tkinter as tk
from tkinter import simpledialog, messagebox, ttk
import json
import random
import os

class QuizApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Interactive Quiz")
        self.root.geometry("600x450")
        self.root.configure(bg="#f0f8ff")

        self.user_name = None
        self.questions = []
        self.score = 0
        self.question_index = 0

        # Title Label
        self.title_label = tk.Label(root, text="🌟 Welcome to the Ultimate Quiz! 🌟",
                                    font=("Arial", 18, "bold"), bg="#f0f8ff", fg="#2c3e50")
        self.title_label.pack(pady=10)

        # Question Label
        self.question_label = tk.Label(root, text="", wraplength=500, font=("Arial", 14, "bold"),
                                       bg="#f0f8ff", fg="#2c3e50")
        self.question_label.pack(pady=20)

        # Progress Bar
        self.progress = ttk.Progressbar(root, orient="horizontal", length=400, mode="determinate")
        self.progress.pack(pady=5)

        # Option Buttons
        self.option_buttons = []
        for i in range(4):
            btn = tk.Button(root, text="", width=40, height=2, font=("Arial", 12, "bold"),
                            bg="#3498db", fg="white", activebackground="#2980b9", borderwidth=3,
                            command=lambda idx=i: self.check_answer(idx))
            btn.bind("<Enter>", lambda e, b=btn: b.config(bg="#2980b9"))
            btn.bind("<Leave>", lambda e, b=btn: b.config(bg="#3498db"))
            self.option_buttons.append(btn)
            btn.pack(pady=5)

        # Progress Label
        self.progress_label = tk.Label(root, text="", font=("Arial", 12), bg="#f0f8ff", fg="black")
        self.progress_label.pack()

        # Start Button
        self.start_button = tk.Button(root, text="Start Quiz 🚀", command=self.start_quiz,
                                      font=("Arial", 14, "bold"), bg="#2ecc71", fg="white", padx=20, pady=10, borderwidth=3)
        self.start_button.pack(pady=20)

        # Finish Button (Initially Hidden)
        self.finish_button = tk.Button(root, text="Finish ❌", command=self.root.quit,
                                       font=("Arial", 14, "bold"), bg="#e74c3c", fg="white", padx=20, pady=10, borderwidth=3)
        self.finish_button.pack(pady=20)
        self.finish_button.pack_forget()

    def load_questions(self):
        try:
            with open("ques.json", "r", encoding="utf-8") as f:
                data = json.load(f)
                return data.get("questions", [])
        except FileNotFoundError:
            messagebox.showerror("Error", "Questions file not found!")
            return []
        except json.JSONDecodeError:
            messagebox.showerror("Error", "Invalid JSON format!")
            return []

    def start_quiz(self):
        self.user_name = simpledialog.askstring("User Info", "Enter your name to start the quiz:")
        if not self.user_name:
            messagebox.showerror("Input Error", "You must enter a name to start the quiz.")
            return

        self.questions = self.load_questions()
        if not self.questions:
            self.question_label.config(text="Error: No questions found!")
            return

        random.shuffle(self.questions)
        self.score = 0
        self.question_index = 0

        self.start_button.pack_forget()
        self.finish_button.pack_forget()
        self.progress["value"] = 0

        self.ask_question()

    def ask_question(self):
        if self.question_index < len(self.questions):
            question = self.questions[self.question_index]
            self.question_label.config(text=question['question'])
            self.progress_label.config(text=f"Question {self.question_index + 1} of {len(self.questions)}")
            self.progress["value"] = ((self.question_index + 1) / len(self.questions)) * 100  # Update progress bar

            for i, option in enumerate(question['options']):
                self.option_buttons[i].config(text=option, state=tk.NORMAL, bg="#3498db", fg="white")
        else:
            self.end_quiz()

    def check_answer(self, index):
        selected_option = self.option_buttons[index]['text']
        correct_answer = self.questions[self.question_index]['answer']

        if selected_option == correct_answer:
            self.score += 1
            self.option_buttons[index].config(bg="#2ecc71")  # Green for correct
        else:
            self.option_buttons[index].config(bg="#e74c3c")  # Red for incorrect

        self.root.after(1000, self.next_question)

    def next_question(self):
        self.question_index += 1
        self.ask_question()

    def end_quiz(self):
        self.question_label.config(text=f"🎉 Quiz Over! {self.user_name}, your score: {self.score}/{len(self.questions)} 🎉")
        self.progress_label.config(text="")

        for button in self.option_buttons:
            button.pack_forget()

        self.finish_button.pack()
        self.save_results()

    def save_results(self):
        result_data = {"user": self.user_name, "score": self.score, "total": len(self.questions)}
        file_path = "quiz_results.json"

        if os.path.exists(file_path):
            with open(file_path, "r", encoding="utf-8") as f:
                try:
                    results = json.load(f)
                except json.JSONDecodeError:
                    results = []
        else:
            results = []

        results.append(result_data)

        with open(file_path, "w", encoding="utf-8") as f:
            json.dump(results, f, indent=4)

if __name__ == "__main__":
    root = tk.Tk()
    app = QuizApp(root)
    root.mainloop()
