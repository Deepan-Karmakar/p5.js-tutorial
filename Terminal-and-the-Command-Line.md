
let sprite_sheet;
let spaceShip;
let sprite_sheet2;
let enemyShip;
const enemies = [];
const number_of_boxes_in_column = 3;
const number_of_boxes_in_row = 16;
const box_width = 55;
const box_height =  45;
function setup() {
    createCanvas(1350,825);
        for(let i = 0; i < number_of_boxes_in_row ; i++){
           enemies.push(i*75+75)
        }
    }
function preload() {
  sprite_sheet = loadImage('Space Ship clone-1.png');
  sprite_sheet2 = loadImage('Enemy Ship clone.png');
}

 let x = 675;
 let y = 775;
 let velocity = 0;
 let bulletX= x;
 let bulletY= y;
 function draw() {
     
    background("white")
    
    if (keyIsDown(LEFT_ARROW)) {
        x -= 10;
    }
    if (keyIsDown(RIGHT_ARROW)) {
        x += 10;
    }
    fill("black")
    ellipse(bulletX + 15, bulletY, 15,15)
    image(sprite_sheet, x - 83, y - 110, 200, 200);

    if (x < 0) {
        x= -x
    } else if (x > 1315) {
        x = -x
    }

    bulletY -= velocity

    if (velocity === 0) {
        bulletX = x
    }
    if(bulletY <=0) {
        bulletY = y;
        velocity = 0;
        bulletX = x   
    }

    for(let j = 0; j < enemies.length; j++) {
        image(sprite_sheet2, 0, 0, 200, 200);
        fill("black");
        rect(enemies[j],50, box_width, 20)
     }
}
function keyPressed() {
    if (keyCode === 32)
    {
        velocity = 50
    }
}