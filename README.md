# 🧠 Personal Quiz Generator

An **interactive quiz application** built with **Python and Tkinter** that allows users to take quizzes with multiple-choice questions. The UI is **modern**, featuring progress tracking, answer feedback, and user-friendly navigation.

https://github.com/user-attachments/assets/4422d322-df92-4677-bba4-422dc6a50ed4


## ✨ Features

✅ **Easy-to-use GUI** with a modern design  
✅ **Multiple-choice questions** with instant feedback  
✅ **User progress tracking** with a progress bar  
✅ **Randomized questions** for a unique experience each time  
✅ **Interactive buttons** with hover effects  
✅ **Final score summary** displayed at the end  
✅ **Stores user scores** in a JSON file  

---

## 📂 Project Structure
```plaintext
📁 Personal Quiz Generator
│── 📜 quiz.py            # Main Python script
│── 📜 ques.json          # JSON file with quiz questions
│── 📜 quiz_results.json  # Stores user scores
│── 📜 README.md          # Documentation
│── 📜 requirements.txt   # Dependencies list
```

## 🚀 Installation & Setup

### **1️⃣ Install Python**
Ensure **Python 3.x** is installed. Download it from [Python Official Website](https://www.python.org/).

### **2️⃣ Clone the Repository**
```bash
git clone https://github.com/yourusername/quiz-generator.git
cd quiz-generator
```
3️⃣ Install Required Libraries
```bash
pip install -r requirements.txt
The project primarily uses tkinter, which is included with Python by default.
```
4️⃣ Run the Application
```bash
python quiz.py
```
## 📖 Usage Guide
1️⃣ Run the script using python quiz.py.

2️⃣ Enter your name to start the quiz.

3️⃣ Answer the questions by selecting one of the four options.

4️⃣ Track your progress using the progress bar.

5️⃣ Get instant feedback on your answers.

6️⃣ See your final score at the end.

7️⃣ Click Finish to close the application.

### 📝 Question Format (ques.json)
The questions are stored in a JSON file (ques.json) using this structure:

```json
{
    "questions": [
        {
            "question": "What is the capital of France?",
            "options": ["Berlin", "Madrid", "Paris", "Rome"],
            "answer": "Paris"
        },
        {
            "question": "Who developed the theory of relativity?",
            "options": ["Isaac Newton", "Albert Einstein", "Galileo Galilei", "Nikola Tesla"],
            "answer": "Albert Einstein"
        }
    ]
}
```
You can modify ques.json to add more questions.

### 📊 Saving Quiz Results
After completing the quiz, the user's score is automatically saved in quiz_results.json in this format:

```json
[
    {"user": "Alice", "score": 3, "total": 5},
    {"user": "Bob", "score": 4, "total": 5}
]
```
## 🎨 UI Enhancements
Progress Bar shows how far along the quiz is.
Color Feedback (Green for correct answers, Red for wrong answers).
Hover Effects on buttons for a better user experience.
Clean and modern design using Tkinter.
## 🔧 Future Improvements
⏳ Timer for each question
🔊 Sound effects for correct/wrong answers
🏆 Leaderboard for highest scores
📱 Mobile-friendly version using Kivy
## 💡 Contributing
Want to improve this project? Contributions are welcome! 🚀

Fork this repository.
Clone your fork.
```bash
git clone https://github.com/yourusername/quiz-generator.git
```
Create a new branch for your feature.
```bash
git checkout -b feature-name
```
Commit your changes.
```bash
git commit -m "Added new feature"
```
Push to GitHub.
```bash
git push origin feature-name
```
Create a Pull Request.
📜 License
This project is open-source under the @Creative Commons Zero v1.0 Universal


📩 Contact
For any queries, feel free to reach out: 
📧 Email: kuasha10102@gmail.com
🐙 GitHub: @sayantichy
🔗linkedin: @sayantichy
🗝 X: @sayantichy

🚀 Enjoy your personalized quiz experience! 🎉
