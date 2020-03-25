# Phaser 3

## Example Code
```
const config = {
    type: Phaser.AUTO,
    width: 800,
    height: 600,
    physics: {
        default: 'arcade',
        arcade: {
            gravity: { y: 300 },
            debug: false
        }
    },
    scene: {
        preload: preload,
        create: create,
        update: update
    }
};

// let platforms; // is this line needed?

const game = new Phaser.Game(config);

function preload ()
{
    this.load.image('sky', 'assets/sky.png');
    this.load.image('ground', 'assets/platform.png');
    this.load.image('star', 'assets/star.png');
    this.load.image('bomb', 'assets/bomb.png');
    this.load.spritesheet('dude',
        'assets/dude.png',
        { frameWidth: 32, frameHeight: 48 }
    );
}

let platforms;

function create ()
{
    this.add.image(400, 300, 'sky');
    this.add.image(400, 300, 'star');

    platforms = this.physics.add.staticGroup();

    platforms.create(400, 568, 'ground').setScale(2).refreshBody();

    platforms.create(600, 400, 'ground');
    platforms.create(50, 250, 'ground');
    platforms.create(750, 220, 'ground');
}
// add image
/* The values 400 and 300 are the x and y coordinates of the image. All Game
Objects are positioned based on their center by default.
Use "this.add.image(0, 0, 'sky').setOrigin(0, 0)" to reset the drawing position of the image to the top-left.
The order in which game objects are displayed matches the order in which you create them.
*/

function update ()
{
}
```

[Back](../../README.md)
