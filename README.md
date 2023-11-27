# stopw1atch
<!DOCTYPE html>
<html lang ="en">
<head>
  <title>Stopwatch App</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- The heading element for the stopwatch app -->
  <h1>Stopwatch</h1>

  <!-- The container for the stopwatch and buttons -->
  <div class="stopwatch">
    <!-- The element to display the timer value -->
    <div class="timer" id="timer">00:00</div>

    <!-- The container for the buttons -->
    <div class="btn-container">
      <!-- The start button -->
      <button class="btn" id="start">Start</button>

      <!-- The stop button -->
      <button class="btn" id="stop">Stop</button>

      <!-- The reset button -->
      <button class="btn" id="reset">Reset</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
   let minutes = 0;
let seconds = 0;
let isRunning = false;
let intervalId;

// Get the timer element from the HTML
const timerElement = document.getElementById("timer");

// Add event listeners to the start, stop, and reset buttons
document.getElementById("start").addEventListener("click", startTimer);
document.getElementById("stop").addEventListener("click", stopTimer);
document.getElementById("reset").addEventListener("click", resetTimer);

// Function to start the timer
function startTimer() {
  if (!isRunning) {
    isRunning = true;
    intervalId = setInterval(() => {
      // Increment seconds and handle minute rollover
      seconds++;
      if (seconds === 60) {
        minutes++;
        seconds = 0;
      }
      // Update the timer display
      timerElement.textContent = formatTime(minutes, seconds);
    }, 1000); // Run the interval every second (1000 milliseconds)
  }
}

// Function to stop the timer
function stopTimer() {
  if (isRunning) {
    isRunning = false;
    clearInterval(intervalId); // Clear the interval to stop the timer
  }
}

// Function to reset the timer
function resetTimer() {
  stopTimer();
  minutes = 0;
  seconds = 0;
  // Reset the timer display
  timerElement.textContent = formatTime(minutes, seconds);
}

// Function to format the time as "MM:SS"
function formatTime(minutes, seconds) {
  return `${padZero(minutes)}:${padZero(seconds)}`;
}

// Function to pad single-digit values with a leading zero
function padZero(value) {
  return value < 10 ? `0${value}` : value;
}


body {
    background-color: skyblue; /* Set the background color of the body to sky blue */
    text-align: center; /* Center-align the content within the body */
    font-family: Arial, sans-serif; /* Set the font family for the body */
  }

  h1 {
    color: #333; /* Set the color of the heading to a dark gray (#333) */
  }

  .stopwatch {
    margin: 50px auto; /* Center the stopwatch container horizontally with a top margin of 50px */
    width: 300px; /* Set the width of the stopwatch container to 300px */
    padding: 20px; /* Add 20px of padding to the stopwatch container */
    background-color: burlywood; /* Set the background color of the stopwatch container to burlywood */
    border-radius: 5px; /* Add a border radius of 5px to the stopwatch container */
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.2); /* Add a box shadow effect to the stopwatch container */
  }

  .timer {
    font-size: 36px; /* Set the font size of the timer to 36px */
    font-weight: bold; /* Set the font weight of the timer to bold */
    margin-bottom: 20px; /* Add a bottom margin of 20px to the timer */
    color: #fff; /* Set the color of the timer to white */
  }

  .btn-container {
    display: flex; /* Use flexbox to display the buttons in a row */
    justify-content: space-around; /* Distribute the space evenly between the buttons */
    gap: 10px; /* Add a gap of 10 pixels between buttons */
  }

  #start {
    background-color: #4CAF50; /* Set the background color of the Start button to green */
  }

  #stop {
    background-color: #FF0000; /* Set the background color of the Stop button to red */
  }

  #reset {
    background-color: #FFC107; /* Set the background color of the Reset button to yellow */
  }

  .btn {
    display: block; /* Display the buttons as block elements */
    padding: 8px 20px; /* Add padding of 8px on the top and bottom, and 20px on the left and right */
    font-size: 16px; /* Set the font size of the buttons to 16px */
    border: none; /* Remove the border from the buttons */
    border-radius: 3px; /* Add a border radius of 3px to the buttons */
    color: #fff; /* Set the color of the buttons to white */
    cursor: pointer; /* Change the cursor to a pointer on hover */
  }

  .btn:hover {
    opacity: 0.8; /* Reduce opacity on hover effect */
  }


