# Quiz JSON Support

![VS Code Marketplace Version](https://img.shields.io/visual-studio-marketplace/v/onyekachiukwu.quiz-json-formatter)
![VS Code Marketplace Downloads](https://img.shields.io/visual-studio-marketplace/d/onyekachiukwu.quiz-json-formatter)
![License](https://img.shields.io/badge/license-MIT-green)

Provides validation and IntelliSense for `.quiz.json` files in Visual Studio Code.

This extension enforces a strict quiz structure using JSON Schema to ensure quizzes are properly formatted, validated, and error-free.

---

## ✨ Features

- ✅ Strict quiz structure validation
- ✅ Identification and Multiple Choice support
- ✅ Exactly 4 options required for multiple choice
- ✅ Correct answer must match index (0–3)
- ✅ No extra properties allowed
- ✅ IntelliSense support
- ✅ Real-time error highlighting

---

## 📦 Installation

1. Open **Extensions** in VS Code.
2. Search for: `Quiz JSON Support`
3. Click **Install**

Or install via command line:

```bash
code --install-extension YOUR_PUBLISHER.quiz-json
````

---

## 📁 File Format

This extension automatically validates files that match:

```
*.quiz.json
```

Example:

```
math.quiz.json
```

---

## 🧠 Quiz Structure Guide

A quiz file must follow this structure:

```json
{
  "title": "Quiz Title",
  "questions": []
}
```

---

## 🏷 Question Types

| Type Value | Meaning         |
| ---------- | --------------- |
| `0`        | Identification  |
| `1`        | Multiple Choice |

---

## 📝 Identification Question (`type: 0`)

Used for short-answer questions.

### Required Fields

* `type` → must be `0`
* `question` → string
* `answer` → string

### Example

```json
{
  "type": 0,
  "question": "What is 2 + 2?",
  "answer": "4"
}
```

---

## 🔘 Multiple Choice Question (`type: 1`)

Used for objective questions with exactly four options.

### Required Fields

* `type` → must be `1`
* `question` → string
* `options` → array of exactly **4 non-empty strings**
* `correctAnswer` → integer (0–3)

### Rules

* You must provide exactly **4 options**
* No option can be empty
* `correctAnswer` must match the index of the correct option:

  * `0` = first option
  * `1` = second option
  * `2` = third option
  * `3` = fourth option

### Example

```json
{
  "type": 1,
  "question": "Capital of France?",
  "options": ["Paris", "Rome", "Berlin", "Madrid"],
  "correctAnswer": 0
}
```

---

## ⚠ Validation Rules Enforced

This extension automatically checks:

* Quiz must contain a `title`
* Quiz must contain a `questions` array
* At least one question must exist
* Identification questions must include `answer`
* Multiple choice must:

  * Have exactly 4 options
  * Have no empty options
  * Use `correctAnswer` between 0 and 3
* No extra properties are allowed
* Invalid `type` values are rejected

Errors appear as red underlines in VS Code.

---

## 📦 Full Sample Quiz (20 Questions)

```json
{
  "title": "General Knowledge Quiz",
  "questions": [
    {
      "type": 0,
      "question": "What is the square root of 64?",
      "answer": "8"
    },
    {
      "type": 1,
      "question": "Which planet is known as the Red Planet?",
      "options": ["Earth", "Mars", "Jupiter", "Saturn"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "Who wrote Romeo and Juliet?",
      "answer": "William Shakespeare"
    },
    {
      "type": 1,
      "question": "Which gas do plants absorb from the atmosphere?",
      "options": ["Oxygen", "Carbon Dioxide", "Hydrogen", "Nitrogen"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "What is 9 squared?",
      "answer": "81"
    },
    {
      "type": 1,
      "question": "Which continent is the Sahara Desert located in?",
      "options": ["Asia", "Europe", "Africa", "Australia"],
      "correctAnswer": 2
    },
    {
      "type": 0,
      "question": "What is the capital of Japan?",
      "answer": "Tokyo"
    },
    {
      "type": 1,
      "question": "Which metal is liquid at room temperature?",
      "options": ["Iron", "Mercury", "Copper", "Aluminum"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "What is 15 × 3?",
      "answer": "45"
    },
    {
      "type": 1,
      "question": "Which programming language runs in the browser?",
      "options": ["Python", "C++", "Java", "JavaScript"],
      "correctAnswer": 3
    },
    {
      "type": 0,
      "question": "How many continents are there?",
      "answer": "7"
    },
    {
      "type": 1,
      "question": "Which organ pumps blood through the body?",
      "options": ["Brain", "Heart", "Lungs", "Kidney"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "What is the chemical symbol for Gold?",
      "answer": "Au"
    },
    {
      "type": 1,
      "question": "Which country is home to the Great Pyramid of Giza?",
      "options": ["India", "Egypt", "Mexico", "Peru"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "Who painted the Mona Lisa?",
      "answer": "Leonardo da Vinci"
    },
    {
      "type": 1,
      "question": "Which language is primarily spoken in Brazil?",
      "options": ["Spanish", "Portuguese", "French", "English"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "What is the boiling point of water in Celsius?",
      "answer": "100"
    },
    {
      "type": 1,
      "question": "Which device measures temperature?",
      "options": ["Barometer", "Thermometer", "Altimeter", "Hygrometer"],
      "correctAnswer": 1
    },
    {
      "type": 0,
      "question": "What is the largest mammal in the world?",
      "answer": "Blue Whale"
    },
    {
      "type": 1,
      "question": "Which ocean is the largest?",
      "options": ["Atlantic", "Indian", "Pacific", "Arctic"],
      "correctAnswer": 2
    }
  ]
}
```

---

## 💡 Best Practices

* Keep questions clear and concise
* Avoid duplicate options
* Double-check `correctAnswer` index
* Use descriptive quiz titles
* Keep formatting clean and readable

---

## 🛠 Development

To package locally:

```bash
vsce package
```

To publish:

```bash
vsce publish
```

---

## 📄 License

MIT License

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

Feel free to open issues or submit pull requests on GitHub.

---
