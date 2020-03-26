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

let player;
let stars;
let bombs;
let platforms;
let cursors;
let score = 0;
let gameOver = false;
let scoreText;

const game = new Phaser.Game(config);

function preload () {
    this.load.image('sky', 'assets/sky.png');
    this.load.image('ground', 'assets/platform.png');
    this.load.image('star', 'assets/star.png');
    this.load.image('bomb', 'assets/bomb.png');
    this.load.spritesheet('dude',
        'assets/dude.png',
        { frameWidth: 32, frameHeight: 48 }
    );
}

function create () {
    this.add.image(400, 300, 'sky');
    this.add.image(400, 300, 'star');

    platforms = this.physics.add.staticGroup();

    platforms.create(400, 568, 'ground').setScale(2).refreshBody();

    platforms.create(600, 400, 'ground');
    platforms.create(50, 250, 'ground');
    platforms.create(750, 220, 'ground');

    player = this.physics.add.sprite(100, 450, 'dude');

    player.setBounce(0.2);
    player.setCollideWorldBounds(true);

    this.anims.create({
        key: 'left',
        frames: this.anims.generateFrameNumbers('dude', { start: 0, end: 3 }),
        frameRate: 10,
        repeat: -1
    });

    this.anims.create({
        key: 'turn',
        frames: [ { key: 'dude', frame: 4 } ],
        frameRate: 20
    });

    this.anims.create({
        key: 'right',
        frames: this.anims.generateFrameNumbers('dude', { start: 5, end: 8 }),
        frameRate: 10,
        repeat: -1
    });

    cursors = this.input.keyboard.createCursorKeys();

    stars = this.physics.add.group({
        key: 'star',
        repeat: 11, // add one automatically created, total 12 stars
        setXY: { x: 12, y: 0, stepX: 70 } // separted by 70px apart
    });

    stars.children.iterate(function (child) {
        child.setBounceY(Phaser.Math.FloatBetween(0.4, 0.8));
    });

    bombs = this.physics.add.group();

    scoreText = this.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' }); // 16 x 16 is the coordinate

    this.physics.add.collider(player, platforms);
    this.physics.add.collider(stars, platforms);
    this.physics.add.collider(bombs, platforms);

    this.physics.add.overlap(player, stars, collectStar, null, this); // collectStar is a callback

    this.physics.add.collider(player, bombs, hitBomb, null, this);
}

function update () {
    if (gameOver) {
        return;
    }

    if (cursors.left.isDown) {
        player.setVelocityX(-160);
        player.anims.play('left', true);
    } else if (cursors.right.isDown) {
        player.setVelocityX(160);
        player.anims.play('right', true);
    } else {
        player.setVelocityX(0);
        player.anims.play('turn');
    }

    if (cursors.up.isDown && player.body.touching.down) {
        player.setVelocityY(-330);
    }
}

function collectStar (player, star) {
    star.disableBody(true, true);

    score += 10;
    scoreText.setText('Score: ' + score);

    if (stars.countActive(true) === 0) {
    //  A new batch of stars to collect
    stars.children.iterate(function (child) {
        child.enableBody(true, child.x, 0, true, true);
    });

    const x = (player.x < 400) ? Phaser.Math.Between(400, 800) : Phaser.Math.Between(0, 400);

    const bomb = bombs.create(x, 16, 'bomb');
    bomb.setBounce(1);
    bomb.setCollideWorldBounds(true);
    bomb.setVelocity(Phaser.Math.Between(-200, 200), 20);
    bomb.allowGravity = false;
    }
}

function hitBomb (player, bomb) {
    this.physics.pause();
    player.setTint(0xff0000);
    player.anims.play('turn');
    gameOver = true;
}
```

## Add Image

The values 400 and 300 are the x and y coordinates of the image. All Game
Objects are positioned based on their center by default.

Use `this.add.image(0, 0, 'sky').setOrigin(0, 0)` to reset the drawing position of the image to the top-left.

The order in which game objects are displayed matches the order in which you create them.

Note that  the image can be added outside the visual region (0x0 to 800x600 in this case), it will exist "off screen".

The Scene itself has no fixed size and extends infinitely in all directions. The Camera system controls your view into the Scene and you can move and zoom the active camera as required. You can also create new cameras for other views into the Scene.

## Physics

`platforms = this.physics.add.staticGroup();` creates a staic physics group and assigns it to the local variable `platforms`.

Two types of phsics bodies:
- Dynamic: can move around via forces, can have velocity or acceleration.
- Static: only have a position and a size, no movement.

A group is a way for you to group together similar objects and control them all as one single unit.

To expand the platform and prevent the player from dropping off the sides, use `setScale(num)`. `refreshBody()` is also needed when calling `setScale()` because the platform is static.

## Player

### Physics Sprite

The following code creates the sprite:
```
player = this.physics.add.sprite(100, 450, 'dude');

player.setBounce(0.2);
player.setCollideWorldBounds(true);
```

`setBounce(0.2)` means when the sprite lands after jumping it will bounce ever so slightly.

`setCollideWorldBounds(true)` means thplayer won't be able to run outside the game dimension (800 x 600 in this case).

### Animation

```
this.anims.create({
    key: 'left',
    frames: this.anims.generateFrameNumbers('dude', { start: 0, end: 3 }),
    frameRate: 10,
    repeat: -1
});
```
`start` and `end` tells you the animation will use frames 0 to 3.

`repeat: -1` tells the animation to loop.

## Physics

When a Physics Sprite is created it is given a body property, which is a reference to its Physics Body.

To simulate the effects of gravity on a sprite, use:
`player.body.setGravityY(300)`
The higher the value, the heavier your object feels and the quicker it falls.

In order to allow the player to collide with the platforms we can create a Collider object. This object monitors two physics objects (which can include Groups) and checks for collisions or overlap between them. If that occurs it can then optionally invoke your own callback.
`this.physics.add.collider(player, platforms)`

## Controls

`cursors = this.input.keyboard.createCursorKeys()`
This populates the cursors object with four properties: up, down, left, right, that are all instances of Key objects.

[Back](../../README.md)
