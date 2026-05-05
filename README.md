<!DOCTYPE html>
<html>
<head>
    <title>Calorie Predictor</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h2>Calorie Burn Predictor</h2>

    <form action="predict" method="post">
        <input type="number" name="age" placeholder="Age" required>
        <input type="number" name="weight" placeholder="Weight (kg)" required>
        <input type="number" name="duration" placeholder="Duration (minutes)" required>
        <input type="number" name="heartRate" placeholder="Heart Rate" required>

        <select name="gender">
            <option value="male">Male</option>
            <option value="female">Female</option>
        </select>

        <button type="submit">Predict Calories</button>
    </form>
</div>

</body>
</html>
