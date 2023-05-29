<!DOCTYPE html>
<html>
<head>
    <title>Minimum Lecture Calculation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f2f2f2;
            margin: 0;
            padding: 20px;
        }

        h1 {
            color: #333;
            text-align: center;
            margin-top: 0;
        }

        .container {
            max-width: 400px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 4px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        label {
            display: block;
            margin-bottom: 10px;
        }

        input[type="number"] {
            width: 100%;
            padding: 10px;
            border-radius: 4px;
            border: 1px solid #ccc;
        }

        button {
            background-color: #4CAF50;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
        }

        button:hover {
            background-color: #45a049;
        }

        .result {
            margin-top: 20px;
        }

        .result-label {
            font-weight: bold;
        }

        .highlight {
            color: red;
        }

        .creator {
            position: fixed;
            bottom: 20px;
            right: 20px;
            font-size: 12px;
            color: #777;
        }
    </style>
    <script>
        // JavaScript program to find minimum
        // number of lectures to attend
        // to maintain 75% attendance

        // Define a global variable to store the label
        let labelO = "Minimum number of lectures to attend (O)";
        let X = 0;

        // Method to compute minimum lecture
        function minimumLectures(m, n) {
            let ans = 0;
            let x = 1.33333 * n;

            // Formula to compute
            if (n < Math.ceil(0.75 * m)) {
                ans = Math.ceil(((0.75 * m) - n) / 0.25);
            } else {
                ans = 0;
            }

            return {
                lecturesToAttend: ans,
                xMinusM: x - m
            };
        }

        function calculateMinimumLectures() {
            // Prompt the user to input M (total no of classes) and N (classes attended)
            let M = parseInt(document.getElementById("total-classes").value);
            let N = parseInt(document.getElementById("classes-attended").value);

            // Call the minimumLectures function with user-input values
            let result = minimumLectures(M, N);
            let resultLabel = document.getElementById("result-label");
            resultLabel.innerHTML = labelO + ": " + result.lecturesToAttend;
            if (result.lecturesToAttend > 0) {
                resultLabel.classList.add("highlight");
            } else {
                resultLabel.classList.remove("highlight");
            }

            // Display 75% of total classes held
            let seventyFivePercent = Math.ceil(0.75 * M);
            document.getElementById("seventy-five-percent").innerHTML = seventyFivePercent;

            // Calculate and display the number of classes that can be left
            if (result.lecturesToAttend === 0) {
                let classesCanBeLeft = result.xMinusM;
                document.getElementById("classes-can-be-left").innerHTML = "No of classes which can be left: " + classesCanBeLeft;
            } else {
                document.getElementById("classes-can-be-left").innerHTML = "";
            }
        }
    </script>
</head>
<body>
    <div class="container">
        <h1>Theory Attendance Calculator</h1>
        <label for="total-classes">Total number of classes (M):</label>
        <input type="number" id="total-classes" placeholder="Enter M" />
        <br />
        <label for="classes-attended">Number of classes attended (N):</label>
        <input type="number" id="classes-attended" placeholder="Enter N" />
        <br />
        <button onclick="calculateMinimumLectures()">Calculate</button>
        <br />
        <p id="result-label"></p>
        <p>75% of total classes held is: <span id="seventy-five-percent"></span></p>
        <p id="classes-can-be-left"></p>
    </div>
    <div class="creator">Created by: Johndoe</div>
</body>
</html>
