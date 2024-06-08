<div align="center">

# <span style="color: #555;">Developing Artificial Intelligence Through Data Science</span>

[AI Guide](https://guide.repleteai.com/)
  <canvas id="gameCanvas" width="400" height="400"></canvas>
  
  <script>
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    
    // Game variables
    const gridSize = 20;
    const snake = [{x: 200, y: 200}];
    let dx = gridSize;
    let dy = 0;
    let food = {x: 0, y: 0};
    let score = 0;
    
    // Game loop
    function gameLoop() {
      // Move the snake
      const head = {x: snake[0].x + dx, y: snake[0].y + dy};
      snake.unshift(head);
      
      // Check for collision with food
      if (head.x === food.x && head.y === food.y) {
        score++;
        generateFood();
      } else {
        snake.pop();
      }
      
      // Draw the game
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      
      // Draw the snake
      ctx.fillStyle = 'green';
      snake.forEach(segment => {
        ctx.fillRect(segment.x, segment.y, gridSize, gridSize);
      });
      
      // Draw the food
      ctx.fillStyle = 'red';
      ctx.fillRect(food.x, food.y, gridSize, gridSize);
      
      // Display the score
      ctx.fillStyle = 'black';
      ctx.font = '20px Arial';
      ctx.fillText(`Score: ${score}`, 10, 30);
      
      // Check for game over
      if (gameOver()) {
        clearInterval(gameLoopInterval);
        ctx.fillStyle = 'black';
        ctx.font = '30px Arial';
        ctx.fillText('Game Over', canvas.width / 2 - 70, canvas.height / 2);
      }
    }
    
    // Generate random food position
    function generateFood() {
      food.x = Math.floor(Math.random() * (canvas.width / gridSize)) * gridSize;
      food.y = Math.floor(Math.random() * (canvas.height / gridSize)) * gridSize;
    }
    
    // Check for game over
    function gameOver() {
      // Check for collision with walls
      if (snake[0].x < 0 || snake[0].x >= canvas.width || snake[0].y < 0 || snake[0].y >= canvas.height) {
        return true;
      }
      
      // Check for collision with itself
      for (let i = 1; i < snake.length; i++) {
        if (snake[0].x === snake[i].x && snake[0].y === snake[i].y) {
          return true;
        }
      }
      
      return false;
    }
    
    // Keyboard controls
    document.addEventListener('keydown', e => {
      if (e.key === 'ArrowUp' && dy !== gridSize) {
        dx = 0;
        dy = -gridSize;
      } else if (e.key === 'ArrowDown' && dy !== -gridSize) {
        dx = 0;
        dy = gridSize;
      } else if (e.key === 'ArrowLeft' && dx !== gridSize) {
        dx = -gridSize;
        dy = 0;
      } else if (e.key === 'ArrowRight' && dx !== -gridSize) {
        dx = gridSize;
        dy = 0;
      }
    });
    
    // Start the game
    generateFood();
    const gameLoopInterval = setInterval(gameLoop, 100);
  </script>
</div>
