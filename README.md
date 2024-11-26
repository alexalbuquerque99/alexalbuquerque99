Alexalbuquerque99/
├── README.md
├── src/
│   ├── index.html
│   ├── style.css
│   ├── script.js
│   └── dino-game/
│       ├── game.html
│       ├── game.css
│       └── game.js
└── .gitignore
# Bem-vindo ao MeuProjeto!

Olá, eu sou **Alex Albuquerque**, estudante do 2º período de Análise e Desenvolvimento de Sistemas na UNINASSAU.

## Sobre Mim
Sou apaixonado por tecnologia e programação. Atualmente, estou desenvolvendo minhas habilidades nas seguintes linguagens e tecnologias:

- **JavaScript**
- **React**
- **HTML5**
- **CSS3**
- **Python**
- **C#**
- **.NET**

Sinta-se à vontade para explorar o repositório e acompanhar meu progresso!

## Projetos
- Mini jogo de dinossauro pulando cactos no deserto (2D)
- Scripts de aprendizado e exercícios práticos de programação

## Contato
Você pode me encontrar em:
- [LinkedIn](https://www.linkedin.com/)
- [GitHub](https://github.com/)

Espero que goste dos projetos! 😊
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Jogo do Dinossauro</title>
    <link rel="stylesheet" href="game.css">
</head>
<body>
    <div class="game-container">
        <div id="dino" class="dino"></div>
        <div id="cactus" class="cactus"></div>
    </div>
    <script src="game.js"></script>
</body>
</html>
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f4e7da;
    font-family: Arial, sans-serif;
}

.game-container {
    position: relative;
    width: 800px;
    height: 200px;
    background-color: #d4a373;
    overflow: hidden;
    border: 2px solid #6b4226;
}

.dino {
    position: absolute;
    bottom: 0;
    width: 50px;
    height: 50px;
    background-color: #3b3a30;
}

.cactus {
    position: absolute;
    bottom: 0;
    right: 0;
    width: 20px;
    height: 50px;
    background-color: #6b4226;
}
const dino = document.getElementById('dino');
const cactus = document.getElementById('cactus');
let isJumping = false;

// Função para o dinossauro pular
function jump() {
    if (isJumping) return;
    isJumping = true;
    let upInterval = setInterval(() => {
        if (parseInt(dino.style.bottom) >= 150) {
            clearInterval(upInterval);
            let downInterval = setInterval(() => {
                if (parseInt(dino.style.bottom) <= 0) {
                    clearInterval(downInterval);
                    isJumping = false;
                }
                dino.style.bottom = parseInt(dino.style.bottom) - 5 + 'px';
            }, 20);
        }
        dino.style.bottom = parseInt(dino.style.bottom) + 5 + 'px';
    }, 20);
}

// Evento de teclado para o pulo
document.addEventListener('keydown', (event) => {
    if (event.code === 'Space') {
        jump();
    }
});

// Movimento do cacto
function moveCactus() {
    cactus.style.right = '0px';
    const cactusInterval = setInterval(() => {
        cactus.style.right = parseInt(cactus.style.right) + 5 + 'px';

        // Verifica colisão
        if (parseInt(cactus.style.right) > 750 && parseInt(dino.style.bottom) < 50) {
            alert('Game Over!');
            clearInterval(cactusInterval);
        }

        if (parseInt(cactus.style.right) > 800) {
            cactus.style.right = '0px';
        }
    }, 20);
}

moveCactus();
node_modules/
dist/
*.log
*.env
git init
git add .
git commit -m "Primeira versão do projeto - apresentação e mini jogo"
git branch -M main
git remote add origin <URL_DO_SEU_REPOSITORIO_GIT>
git push -u origin main
