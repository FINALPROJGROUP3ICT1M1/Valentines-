
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine?</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            font-family: 'Arial', sans-serif;
            background-color: #fce4ec; /* Light pink background */
            text-align: center;
        }

        #question-container {
            padding: 40px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        }

        h1 {
            color: #d81b60; /* Deep pink text */
            margin-bottom: 30px;
            font-size: 2.5em;
        }

        #buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            position: relative; /* Needed for the 'no' button to move relative to this container */
            height: 50px; /* Gives space for buttons */
        }

        button {
            padding: 10px 25px;
            font-size: 1.2em;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: bold;
        }

        #yes-btn {
            background-color: #4caf50; /* Green */
            color: white;
        }

        #yes-btn:hover {
            background-color: #43a047;
            transform: scale(1.05);
        }

        #no-btn {
            background-color: #f44336; /* Red */
            color: white;
            position: absolute; /* Allows for random movement */
            left: 50%;
            transform: translateX(-50%);
            transition: none; /* Crucial: removes transition for the 'No' button's position */
        }

        #cat-screen {
            display: none; /* Hidden by default */
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: white;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 100;
        }

        #cat-image {
            width: 300px;
            height: auto;
            border-radius: 15px;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
            margin-bottom: 30px;
        }

        #cat-screen p {
            font-size: 3em;
            color: #d81b60;
            font-weight: 900;
            animation: pulse 1s infinite alternate;
        }
        
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }
    </style>
</head>
<body>

    <div id="question-container">
        <h1>Will you be my Valentine?</h1>
        <div id="buttons">
            <button id="yes-btn" onclick="handleYes()">Yes! ❤️</button>
            <button id="no-btn" onmouseover="moveNoButton()" onclick="alert('You can only say yes! 😉')">No 💔</button>
        </div>
    </div>
    
    <div id="cat-screen">
        <img id="cat-image" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Cat03.jpg/1200px-Cat03.jpg" alt="A very cute cat image">
        <p>I knew you liked me! Happy Valentine's Day! 🥰</p>
    </div>

    <script>
        const noButton = document.getElementById('no-btn');
        const container = document.getElementById('buttons');
        const catScreen = document.getElementById('cat-screen');
        
        /**
         * Moves the "No" button to a random position within its parent container.
         * This function is triggered when the mouse hovers over the "No" button.
         */
        function moveNoButton() {
            // Get the size of the container and the button
            const containerWidth = container.offsetWidth;
            const containerHeight = container.offsetHeight;
            const buttonWidth = noButton.offsetWidth;
            const buttonHeight = noButton.offsetHeight;
            
            // Calculate random coordinates. The '- buttonSize' ensures the button stays fully inside the container.
            // We use 'container' for relative positioning.
            const newX = Math.random() * (containerWidth - buttonWidth);
            const newY = Math.random() * (containerHeight - buttonHeight);

            noButton.style.left = `${newX}px`;
            noButton.style.top = `${newY}px`;
        }

        /**
         * Handles the click on the "Yes" button.
         * It hides the question and displays the final white screen with the cat.
         */
        function handleYes() {
            // Hide the question container
            document.getElementById('question-container').style.display = 'none';
            
            // Display the cat screen with flex to center the content
            catScreen.style.display = 'flex';
        }

        // Initially position the No button to avoid it starting off-center when the JS loads
        // The CSS has a initial position, but this ensures it's set relative to the container.
        window.onload = () => {
             noButton.style.left = '60%'; // Arbitrary starting position on the right side
             noButton.style.top = '0';
        };

    </script>
</body>
</html>
