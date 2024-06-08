<div align="center">

# <span style="color: #555;">Developing Artificial Intelligence Through Data Science</span>

[AI Guide](https://guide.repleteai.com/)
  <div class="snake-container">
    <div class="snake">
      <div class="snake-body"></div>
      <div class="snake-body"></div>
      <div class="snake-body"></div>
      <div class="snake-body"></div>
      <div class="snake-body"></div>
    </div>
  </div>
  
  <style>
    .snake-container {
      width: 400px;
      height: 200px;
      background-color: #f0f0f0;
      position: relative;
    }
    
    .snake {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      display: flex;
    }
    
    .snake-body {
      width: 20px;
      height: 20px;
      background-color: #000;
      margin: 0 5px;
      animation: snakeMove 1s infinite;
    }
    
    @keyframes snakeMove {
      0% {
        transform: translateX(0);
      }
      50% {
        transform: translateX(20px);
      }
      100% {
        transform: translateX(0);
      }
    }
  </style>
</div>
