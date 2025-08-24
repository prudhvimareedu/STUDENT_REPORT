# STUDENT_REPORT
This project is a Student Report Card Generator that takes student details and marks for five subjects as input, calculates the average, and displays the results along with the grade.


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Student Report Card Generator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background-color: #f4f4f9;
    }
    h2 {
      color: #333;
    }
    label {
      font-size: 1.1em;
      display: block;
      margin-top: 10px;
    }
    input, button {
      padding: 8px;
      font-size: 1em;
      margin-top: 5px;
      margin-bottom: 20px;
    }
    input[type="text"], input[type="number"] {
      width: 100%;
      max-width: 300px;
    }
    button {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
    .result {
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      display: none;
    }
    .result p {
      font-size: 1.2em;
    }
  </style>
</head>
<body>

  <h2>🧑‍🎓 Student Report Card Generator</h2>

  <form id="reportForm">
    <label for="rollNo">Roll Number:</label>
    <input type="number" id="rollNo" required>

    <label for="name">Name:</label>
    <input type="text" id="name" required>

    <label for="marks">Marks (5 subjects):</label>
    <input type="number" id="mark1" required placeholder="Subject 1">
    <input type="number" id="mark2" required placeholder="Subject 2">
    <input type="number" id="mark3" required placeholder="Subject 3">
    <input type="number" id="mark4" required placeholder="Subject 4">
    <input type="number" id="mark5" required placeholder="Subject 5">

    <button type="button" onclick="generateReport()">Generate Report</button>
  </form>

  <div class="result" id="result">
    <h3>📝 Report Card</h3>
    <p id="resultText"></p>
    <p id="grade"></p>
  </div>

  <script>
    function generateReport() {
      // Get form data
      const rollNo = document.getElementById('rollNo').value;
      const name = document.getElementById('name').value;
      const marks = [
        parseFloat(document.getElementById('mark1').value),
        parseFloat(document.getElementById('mark2').value),
        parseFloat(document.getElementById('mark3').value),
        parseFloat(document.getElementById('mark4').value),
        parseFloat(document.getElementById('mark5').value)
      ];

      // Calculate total, average, and grade
      const total = marks.reduce((sum, mark) => sum + mark, 0);
      const avg = total / 5;
      let grade;

      if (avg >= 90) grade = 'A';
      else if (avg >= 75) grade = 'B';
      else if (avg >= 60) grade = 'C';
      else if (avg >= 40) grade = 'D';
      else grade = 'F';

      // Show result
      const resultText = `Roll No: ${rollNo}<br>Name: ${name}<br>Marks: ${marks.join(' ')}<br>Average: ${avg.toFixed(2)}`;
      document.getElementById('resultText').innerHTML = resultText;
      document.getElementById('grade').innerText = `Grade: ${grade}`;

      document.getElementById('result').style.display = 'block';
    }
  </script>

</body>
</html>
