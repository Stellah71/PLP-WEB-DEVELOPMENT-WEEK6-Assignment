# PLP-WEB-DEVELOPMENT-WEEK6-Assignment

# 1.Index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>JS Event Assignment</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Welcome to the Event Playground 🎉</h1>

  <!-- Event Buttons -->
  <button id="clickBtn">Click Me</button>
  <button id="hoverBtn">Hover Over Me</button>
  <button id="secretBtn">Double Click Me</button>

  <!-- Interactive Elements -->
  <div class="gallery">
    <img src="https://via.placeholder.com/150" id="galleryImg" alt="Gallery">
    <button id="nextImg">Next Image</button>
  </div>

  <div class="tabs">
    <button class="tabBtn" data-tab="1">Tab 1</button>
    <button class="tabBtn" data-tab="2">Tab 2</button>
    <div id="tabContent"></div>
  </div>

  <!-- Form Validation -->
  <form id="signupForm">
    <input type="text" id="name" placeholder="Name" required>
    <input type="email" id="email" placeholder="Email" required>
    <input type="password" id="password" placeholder="Password" required>
    <button type="submit">Sign Up</button>
    <p id="formFeedback"></p>
  </form>

  <script src="script.js"></script>
</body>
</html>

 
 # 2. style.css (optional but adds flair)
css
Copy
Edit
body {
  font-family: Arial, sans-serif;
  margin: 20px;
}

button {
  margin: 10px;
  padding: 10px;
}

#galleryImg {
  width: 150px;
  height: 150px;
  transition: transform 0.3s;
}

#galleryImg:hover {
  transform: scale(1.1);
}

.tabs {
  margin-top: 20px;
}

#formFeedback {
  color: red;
  font-size: 0.9em;
}



# 3. script.js
javascript
Copy
Edit
// 1. Event Handling

document.getElementById('clickBtn').addEventListener('click', () => {
  alert('Button clicked!');
});

document.getElementById('hoverBtn').addEventListener('mouseover', () => {
  document.getElementById('hoverBtn').style.backgroundColor = 'lightgreen';
});

document.addEventListener('keypress', (e) => {
  console.log(`Key pressed: ${e.key}`);
});

document.getElementById('secretBtn').addEventListener('dblclick', () => {
  alert('Secret double-click action triggered! 🎉');
});

// 2. Interactive Elements

let galleryImages = [
  "https://via.placeholder.com/150/FF0000",
  "https://via.placeholder.com/150/00FF00",
  "https://via.placeholder.com/150/0000FF"
];
let currentImg = 0;

document.getElementById('nextImg').addEventListener('click', () => {
  currentImg = (currentImg + 1) % galleryImages.length;
  document.getElementById('galleryImg').src = galleryImages[currentImg];
});

// Tabs
const tabContent = {
  1: "You selected Tab 1 content!",
  2: "Welcome to Tab 2!"
};

document.querySelectorAll('.tabBtn').forEach(button => {
  button.addEventListener('click', () => {
    const tabId = button.getAttribute('data-tab');
    document.getElementById('tabContent').textContent = tabContent[tabId];
  });
});

// 3. Form Validation

document.getElementById('signupForm').addEventListener('submit', (e) => {
  e.preventDefault();
  const email = document.getElementById('email').value;
  const pwd = document.getElementById('password').value;
  const feedback = document.getElementById('formFeedback');

  if (!email.includes('@')) {
    feedback.textContent = 'Invalid email format';
  } else if (pwd.length < 8) {
    feedback.textContent = 'Password must be at least 8 characters';
  } else {
    feedback.style.color = 'green';
    feedback.textContent = 'Form submitted successfully!';
  }
});
