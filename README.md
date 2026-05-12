<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Lâmpada</title>
</head>
<body>
    <header>
        <h1>VANILLA JS</h1>
    </header>
    <main>
        <div>
            <img src="./img/desligada.jpg" alt="Lâmpada" id='lamp'>
        </div>
        <div>
            <button id='turnOn'>Ligar</button>
            <button id='turnOff'>Desligar</button>
            <button id="fixBtn" style="display: none;">Consertar</button>
        </div>
    </main>
    <script src="./script.js"></script>
</body>
</html>

=========================

// atribuição das variaveis de botões e do src da imagem.
const turnOn = document.getElementById('turnOn');
const turnOff = document.getElementById('turnOff');
const lamp = document.getElementById('lamp');
const fixBtn = document.getElementById('fixBtn');


//função para checar se a lampada esta quebrada
function isLampBroken() {
    return lamp.src.indexOf('quebrada') > -1;
}

//função para ligar a lampada caso a funçao nao retorne -1
function lampOn() {
    if (!isLampBroken()) {
        lamp.src = './img/ligada.jpg';
    }
}

// função para desligar a lampada
function lampOff() {
    if (!isLampBroken()) {
        lamp.src = './img/desligada.jpg';
    }
}

//função para quebrar a lampada
function lampBroken() {
    lamp.src = './img/quebrada.jpg';
    fixBtn.style.display = 'inline-block';
}

// Conserta a lâmpada e some com o botao de consertar
function lampFix() {
        lamp.src = './img/desligada.jpg';     // Volta para a imagem desligada
        fixBtn.style.display = 'none';        // Esconde o botão de consertar
    }

// Associa cada função ao seu evento correspondente
turnOn.addEventListener('click', lampOn);       // Clique em "Ligar" → liga
turnOff.addEventListener('click', lampOff);     // Clique em "Desligar" → desliga
lamp.addEventListener('mouseenter',lampOn);     // mouse em cima da lampada liga ela
lamp.addEventListener('mouseleave',lampOff);    // quando o mouse sai a lampada desliga
lamp.addEventListener('dblclick', lampBroken);  // Duplo clique na lâmpada → quebra
fixBtn.addEventListener('click', lampFix);      // Clique em "Consertar" → conserta

=====================

header, main {
    display: flex;
    flex-direction: column;
    align-items: center;
}
button {
    width: 80px;
}
