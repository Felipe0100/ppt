// Configurações do jogo
var config = {
  type: Phaser.AUTO,
  width: 800,
  height: 600,
  physics: {
    default: 'arcade',
    arcade: {
      gravity: { y: 0 }
    }
  },
  scene: {
    preload: preload,
    create: create,
    update: update
  }
};

// Cria o jogo
var game = new Phaser.Game(config);

// Função de pré-carregamento de assets
function preload() {
  this.load.image('loja', 'assets/loja.png');
  this.load.image('dino', 'assets/dino.png');
  this.load.image('jogador', 'assets/jogador.png');
}

// Função de criação do jogo
function create() {
  // Cria o fundo da loja
  this.add.image(400, 300, 'loja');

  // Cria o jogador
  this.jogador = this.physics.add.sprite(100, 100, 'jogador');
  this.jogador.setCollideWorldBounds(true);

  // Cria o dinossauro de brinquedo
  this.dino = this.physics.add.sprite(700, 500, 'dino');
  this.dino.setCollideWorldBounds(true);
  this.dino.setVelocity(100, 100);

  // Cria a câmera para seguir o jogador
  this.cameras.main.startFollow(this.jogador);
}

// Função de atualização do jogo
function update(time, delta) {
  // Verifica se o jogador colidiu com o dinossauro
  if (this.physics.collide(this.jogador, this.dino)) {
    // Game over!
    this.scene.start('gameOver');
  }

  // Move o dinossauro aleatoriamente
  if (Math.random() < 0.1) {
    this.dino.setVelocity(Math.random() * 200 - 100, Math.random() * 200 - 100);
  }
}

// Cria a cena de game over
function gameOver() {
  this.add.text(400, 300, 'Game Over!');
}
```

*Assets*
- `loja.png`: imagem do fundo da loja
- `dino.png`: imagem do dinossauro de brinquedo
- `jogador.png`: imagem do jogador

*Como jogar*
- Use as setas para mover o jogador
- Evite o dinossauro de brinquedo!

Lembre-se de que esse é apenas um exemplo simples e você pode adicionar mais recursos e complexidade ao jogo. Boa sorte!# ppt