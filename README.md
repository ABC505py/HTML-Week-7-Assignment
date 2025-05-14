# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Local Storage & Animation</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <h1>Welcome to the Interactive Animation Page</h1>

  <!-- Button to trigger animation -->
  <button id="startAnimationBtn">Start Animation</button>

  <!-- Div that will be animated -->
  <div id="animatedBox"></div>

  <label for="colorPicker">Choose background color:</label>
  <input type="color" id="colorPicker" value="#ff0000">

  <script src="script.js"></script>

</body>
</html>

css

/* Style for the animated box */
#animatedBox {
  width: 100px;
  height: 100px;
  background-color: #ff0000;
  margin-top: 20px;
  transition: transform 2s ease-in-out; /* Adding transition for animation */
}

/* Animation keyframes */
@keyframes bounce {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-100px);
  }
  100% {
    transform: translateY(0);
  }
}

/* Animation class that will be toggled */
.bounce {
  animation: bounce 2s infinite;
}

script.js

// Check if a user preference for color exists in localStorage and apply it
function applyUserPreferences() {
  const storedColor = localStorage.getItem('backgroundColor');
  const colorPicker = document.getElementById('colorPicker');
  
  if (storedColor) {
    // Apply stored color as background color
    document.body.style.backgroundColor = storedColor;
    colorPicker.value = storedColor; // Update the color picker value
  }

  // Check if animation preference exists
  const storedAnimation = localStorage.getItem('animationEnabled');
  if (storedAnimation === 'true') {
    triggerAnimation(); // Apply the animation if it's enabled
  }
}

// Save the user's selected color to localStorage
function saveColorPreference() {
  const color = document.getElementById('colorPicker').value;
  localStorage.setItem('backgroundColor', color);
  document.body.style.backgroundColor = color;
}

// Trigger the animation on the animated box
function triggerAnimation() {
  const animatedBox = document.getElementById('animatedBox');
  animatedBox.classList.add('bounce'); // Add the bounce class to trigger animation
  localStorage.setItem('animationEnabled', 'true'); // Store the animation preference
}

// Stop the animation
function stopAnimation() {
  const animatedBox = document.getElementById('animatedBox');
  animatedBox.classList.remove('bounce'); // Remove the bounce class to stop the animation
  localStorage.setItem('animationEnabled', 'false'); // Store the preference
}

// Event listener to change background color when the color is selected
document.getElementById('colorPicker').addEventListener('input', function() {
  saveColorPreference(); // Save color on change
});

// Event listener for the start animation button
document.getElementById('startAnimationBtn').addEventListener('click', function() {
  triggerAnimation(); // Trigger animation when the button is clicked
});

// Apply user preferences when the page loads
window.onload = applyUserPreferences;

