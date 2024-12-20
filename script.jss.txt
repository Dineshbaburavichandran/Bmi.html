// Select DOM elements
const heightInput = document.getElementById("height");
const weightInput = document.getElementById("weight");
const calculateBtn = document.getElementById("calculateBtn");
const resultDiv = document.getElementById("result");

// Calculate BMI
calculateBtn.addEventListener("click", () => {
  const height = parseFloat(heightInput.value) / 100; // Convert cm to meters
  const weight = parseFloat(weightInput.value);

  if (isNaN(height) || isNaN(weight) || height <= 0 || weight <= 0) {
    resultDiv.textContent = "Please enter valid height and weight!";
    resultDiv.style.color = "red";
    return;
  }

  const bmi = (weight / (height * height)).toFixed(2);

  let category = "";
  if (bmi < 18.5) {
    category = "Underweight";
    resultDiv.style.color = "#ff9900";
  } else if (bmi < 24.9) {
    category = "Normal weight";
    resultDiv.style.color = "#5cb85c";
  } else if (bmi < 29.9) {
    category = "Overweight";
    resultDiv.style.color = "#ffcc00";
  } else {
    category = "Obese";
    resultDiv.style.color = "red";
  }

  resultDiv.textContent = Your BMI is ${bmi} (${category}).;
});