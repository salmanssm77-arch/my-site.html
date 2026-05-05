<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Advanced Calorie Burn Predictor</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
        color: white;
        text-align: center;
        padding: 20px;
    }

    h1 {
        margin-bottom: 10px;
    }

    .container {
        max-width: 450px;
        margin: auto;
        background: rgba(255,255,255,0.05);
        padding: 25px;
        border-radius: 15px;
        box-shadow: 0 0 20px rgba(0,0,0,0.5);
    }

    input, select {
        width: 90%;
        padding: 12px;
        margin: 10px 0;
        border-radius: 8px;
        border: none;
        font-size: 14px;
    }

    button {
        width: 95%;
        padding: 12px;
        background: #00e676;
        border: none;
        border-radius: 8px;
        font-size: 16px;
        cursor: pointer;
        font-weight: bold;
    }

    button:hover {
        background: #00c853;
    }

    .result {
        margin-top: 20px;
        font-size: 18px;
        font-weight: bold;
    }

    .info {
        font-size: 13px;
        opacity: 0.8;
    }
</style>
</head>

<body>

<h1>🔥 Calorie Burn Predictor</h1>
<p class="info">Smart estimation based on your body & workout</p>

<div class="container">

    <input type="number" id="age" placeholder="Age">
    <input type="number" id="weight" placeholder="Weight (kg)">
    <input type="number" id="height" placeholder="Height (cm)">
    <input type="number" id="duration" placeholder="Workout Duration (minutes)">
    <input type="number" id="heartrate" placeholder="Heart Rate (bpm)">

    <select id="gender">
        <option value="male">Male</option>
        <option value="female">Female</option>
    </select>

    <select id="activity">
        <option value="5">Light Exercise</option>
        <option value="8">Moderate Exercise</option>
        <option value="10">Intense Workout</option>
    </select>

    <button onclick="calculateCalories()">Calculate Calories</button>

    <div class="result" id="result"></div>
</div>

<script>
function calculateCalories() {

    let age = parseInt(document.getElementById("age").value);
    let weight = parseFloat(document.getElementById("weight").value);
    let height = parseFloat(document.getElementById("height").value);
    let duration = parseInt(document.getElementById("duration").value);
    let hr = parseInt(document.getElementById("heartrate").value);
    let gender = document.getElementById("gender").value;
    let activity = parseFloat(document.getElementById("activity").value);

    if (!age || !weight || !height || !duration || !hr) {
        document.getElementById("result").innerHTML = "⚠️ Please fill all fields";
        return;
    }

    let calories = 0;

    if (gender === "male") {
        calories = ((age * 0.2017) - (weight * 0.09036) + (hr * 0.6309) - 55.0969) * duration / 4.184;
    } else {
        calories = ((age * 0.074) - (weight * 0.05741) + (hr * 0.4472) - 20.4022) * duration / 4.184;
    }

    // Activity multiplier
    calories = calories * (activity / 8);

    // BMI Calculation
    let bmi = weight / ((height/100) * (height/100));

    let bmiStatus = "";
    if (bmi < 18.5) bmiStatus = "Underweight";
    else if (bmi < 25) bmiStatus = "Normal";
    else if (bmi < 30) bmiStatus = "Overweight";
    else bmiStatus = "Obese";

    document.getElementById("result").innerHTML =
        "🔥 Calories Burned: " + Math.round(calories) + " kcal<br><br>" +
        "📊 BMI: " + bmi.toFixed(1) + " (" + bmiStatus + ")<br><br>" +
        "💡 Tip: Higher heart rate & longer workouts burn more calories!";
}
</script>

</body>
</html>
