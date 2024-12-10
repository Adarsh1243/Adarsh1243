### HTML (index.html)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Racing Game</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div id="gameArea">
        <div id="car"></div>
        <div id="obstacle"></div>
    </div>
    <div id="score">Score: 0</div>
    <script src="script.js"></script>
</body>
</html>
```

### CSS (styles.css)
```css
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background: #333;
}

#gameArea {
    position: relative;
    width: 400px;
    height: 600px;
    border: 2px solid #fff;
    overflow: hidden;
}

#car {
    position: absolute;
    bottom: 10px;
    left: 50%;
    width: 50px;
    height: 100px;
    background: red;
    transform: translateX(-50%);
}

#obstacle {
    position: absolute;
    top: -100px;
    left: 50%;
    width: 50px;
    height: 100px;
    background: blue;
    transform: translateX(-50%);
}

#score {
    position: absolute;
    top: 10px;
    color: white;
    font-size: 20px;
}
```

### JavaScript (script.js)
```javascript
const car = document.getElementById('car');
const obstacle = document.getElementById('obstacle');
const scoreDisplay = document.getElementById('score');
let score = 0;
let gameSpeed = 2;

document.addEventListener('keydown', moveCar);

function moveCar(event) {
    const carRect = car.getBoundingClientRect();
    switch (event.key) {
        case 'ArrowLeft':
            if (carRect.left > 0) {
                car.style.left = `${carRect.left - 10}px`;
            }
            break;
        case 'ArrowRight':
            if (carRect.right < 400) {
                car.style.left = `${carRect.left + 10}px`;
            }
            break;
    }
}

function startGame() {
    obstacle.style.top = '-100px';
    setInterval(() => {
        const obstacleRect = obstacle.getBoundingClientRect();
        obstacle.style.top = `${obstacleRect.top + gameSpeed}px`;

        if (obstacleRect.top > 600) {
            obstacle.style.top = '-100px';
            score++;
            scoreDisplay.textContent = `Score: ${score}`;
        }

        if (obstacleRect.top > 500 && obstacleRect.left < car.getBoundingClientRect().right && obstacleRect.right > car.getBoundingClientRect().left) {
            alert('Game Over! Final Score: ' + score);
            document.location.reload();
        }
    }, 20);
}

startGame();
```

### Explanation:
- **HTML**: Sets up the game area, car, and obstacle.
- **CSS**: Styles the game elements.
- **JavaScript**: Controls car movement, obstacle generation, score tracking, and collision detection. - 👋 Hi, I’m @Adarsh1243
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Adarsh1243/Adarsh1243 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
