index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>CSS Animations & JavaScript Functions</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>🎉 CSS Animations with Local Storage Example</h1>

  <!-- Button to trigger animation and change color -->
  <button id="actionButton" onclick="changeButtonColor()">Click Me!</button>

  <script src="script.js"></script>
</body>
</html>
styles.css
  /* Button styling */
button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease; /* Smooth background transition */
  }
  
  /* Animation for button click */
  @keyframes grow {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.2);
    }
    100% {
      transform: scale(1);
    }
  }
  
  /* Class to trigger the animation */
  .grow-animation {
    animation: grow 0.5s ease-in-out;
  }
  
script.js
// Function to change button color and store preference in localStorage
function changeButtonColor() {
    const button = document.getElementById("actionButton");
    const newColor = button.style.backgroundColor === "green" ? "blue" : "green";
    
    // Change button color dynamically
    button.style.backgroundColor = newColor;
    
    // Save the user's preference in localStorage
    localStorage.setItem('buttonColor', newColor);
  
    // Trigger the animation
    button.classList.add("grow-animation");
  
    // Remove the animation class after it completes
    setTimeout(() => {
      button.classList.remove("grow-animation");
    }, 500); // Match the animation duration
  }
  
  // Function to load the user's preference from localStorage
  function loadUserPreferences() {
    const storedColor = localStorage.getItem('buttonColor');
    if (storedColor) {
      document.getElementById("actionButton").style.backgroundColor = storedColor;
    }
  }
  
  // Load preferences when the page loads
  window.onload = loadUserPreferences;
  
