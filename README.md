# computing
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grade Estimation Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f8f9fa;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background: #ffffff;
            box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        h1 {
            text-align: center;
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            background: #007bff;
            color: #ffffff;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background: #0056b3;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Grade Estimation Calculator</h1>
        <form id="gradeForm">
            <label for="assignment">Assignment (Weight: 20%)</label>
            <input type="number" id="assignment" placeholder="Enter score (0-100)" min="0" max="100">

            <label for="exam1">Exam I (Weight: 40%)</label>
            <input type="number" id="exam1" placeholder="Enter score (0-100)" min="0" max="100">

            <label for="exam2">Exam II (Weight: 40%)</label>
            <input type="number" id="exam2" placeholder="Enter score (0-100)" min="0" max="100">

            <label for="expectedGrade">Expected Grade</label>
            <select id="expectedGrade">
                <option value="90">A (90%)</option>
                <option value="85">B+ (85%)</option>
                <option value="80">B (80%)</option>
                <option value="75">C+ (75%)</option>
                <option value="70">C (70%)</option>
                <option value="65">D+ (65%)</option>
                <option value="60">D (60%)</option>
            </select>

            <button type="button" onclick="calculateGrade()">Calculate Missed %</button>
        </form>
        <div class="result" id="result">Missed %: --</div>
    </div>

    <script>
        function calculateGrade() {
            // Get input values
            const assignment = parseFloat(document.getElementById("assignment").value) || 0;
            const exam1 = parseFloat(document.getElementById("exam1").value) || 0;
            const exam2 = parseFloat(document.getElementById("exam2").value) || 0;
            const expectedGrade = parseFloat(document.getElementById("expectedGrade").value);

            // Calculate weighted total score
            const weightedScore = (assignment * 0.2) + (exam1 * 0.4) + (exam2 * 0.4);

            // Calculate missed percentage
            const missed = Math.max(0, expectedGrade - weightedScore);

            // Display the result
            document.getElementById("result").textContent = `Missed %: ${missed.toFixed(2)}`;
        }
    </script>
</body>
</html>
