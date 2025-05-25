# scrum-assingment


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SCRUM Quizzer - TIS Autotest</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 30px auto;
      background-color: #f9f9f9;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
    }
    .question {
      margin-top: 20px;
    }
    .options button {
      display: block;
      margin: 10px 0;
      width: 100%;
      padding: 10px;
      border-radius: 6px;
      border: 1px solid #ccc;
      background-color: #fff;
      cursor: pointer;
    }
    .options button:hover {
      background-color: #e0e0e0;
    }
    #result {
      font-weight: bold;
      text-align: center;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>SCRUM Quizzer</h1>
  <div id="quiz">
    <div class="question" id="question"></div>
    <div class="options" id="options"></div>
    <div id="result"></div>
    <button onclick="nextQuestion()" style="margin-top:20px;">Next</button>
  </div>

  <script>
    const quizData = [
      {
        question: "What is the role of the Product Owner in SCRUM?",
        options: [
          "Manages the team directly",
          "Owns the product backlog and prioritizes items",
          "Supervises developers daily",
          "Tests the product"
        ],
        answer: 1
      },
      {
        question: "Which of these is NOT a SCRUM artifact?",
        options: [
          "Product Backlog",
          "Burnup Chart",
          "Sprint Backlog",
          "Increment"
        ],
        answer: 1
      },
      {
        question: "What is the time-box for a daily scrum?",
        options: [
          "15 minutes",
          "1 hour",
          "30 minutes",
          "45 minutes"
        ],
        answer: 0
      },
      {
        question: "Which event happens at the end of each sprint?",
        options: [
          "Sprint Planning",
          "Sprint Review",
          "Product Grooming",
          "Daily Scrum"
        ],
        answer: 1
      },
      {
        question: "What is the purpose of splitting user stories?",
        options: [
          "Make backlog shorter",
          "Help developers take breaks",
          "Make them small and manageable",
          "Assign more tasks"
        ],
        answer: 2
      }
    ];

    let current = 0;
    let score = 0;

    function loadQuestion() {
      const q = quizData[current];
      document.getElementById("question").textContent = q.question;
      const opts = q.options.map((opt, idx) => `<button onclick="checkAnswer(${idx})">${opt}</button>`).join("");
      document.getElementById("options").innerHTML = opts;
      document.getElementById("result").textContent = "";
    }

    function checkAnswer(selected) {
      const correct = quizData[current].answer;
      const result = document.getElementById("result");
      if (selected === correct) {
        result.textContent = "✅ Correct!";
        score++;
      } else {
        result.textContent = `❌ Wrong! Correct answer: ${quizData[current].options[correct]}`;
      }
    }

    function nextQuestion() {
      current++;
      if (current < quizData.length) {
        loadQuestion();
      } else {
        document.getElementById("quiz").innerHTML = `<h2>🎉 Quiz Completed!</h2><p>Your score: ${score}/${quizData.length}</p>`;
      }
    }

    loadQuestion();
  </script>
</body>
</html>
