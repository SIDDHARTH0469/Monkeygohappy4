var monkey = createSprite(50,350,50,50);
monkey.setAnimation("monkey");
monkey.scale = 0.2;
var ground  = createSprite(0,380,400,10);
var gameState = "Menu";
var bg = createSprite(200,200,20,20);
bg.setAnimation("forest.jpeg_1");
bg.scale = 3;
bg.x = bg.width/2;
bg.velocityX = -12;
var play = createSprite(200,200,20,20);
play.setAnimation("play");
play.scale = 0.4;
var bananaGroup = createGroup();
var stoneGroup = createGroup();
var Back = createSprite(50,50,50,50);
Back.setAnimation("back_1");
Back.scale = 0.2;
var b2 = createSprite(200,200,20,20);
b2.setAnimation("Won");
b2.scale = 0.5;
var survivalTime = 0;

function draw() {
 
  if(gameState == "Menu"){
    Back.visible = false;
    bg.visible = false;
    monkey.visible = false;
    b2.visible = false;
    background(0,255,64);
    play.display();
    play.visible = true;
    if(mousePressedOver(play)){
      gameState = "Game";
      survivalTime= 0;
      monkey.visible = true;
      monkey.y = 350;
    }
    
    fill(World.mouseX,World.mouseY,155);
    stroke(0);
    strokeWeight(5);
    textSize(50);
    text("MONKEY GO",50,50);
    text("HAPPY - 1",85,100);
    
  }
  
  if(gameState == "Game"){
    
    play.visible = false;
    ground.visible = false;
    b2.visible = false;
    Back.visible = true;
    bg.visible = true;
    monkey.visible = true;
    monkey.depth = monkey.depth + 5;
    monkey.collide(ground);
    monkey.velocityY = monkey.velocityY + 0.8;
    drawSprites();
    
    survivalTime = survivalTime + 1;
    fill("yellow");
    stroke(0);
    strokeWeight(6);
    textSize(30);
    text("Survival Time :" + survivalTime,150,59);
    

    if(bg.x < 0){
      bg.x = bg.width/2;
    }
    
    banana();
    Rocks();
    
    if(keyDown("space") && monkey.y > 250){
      monkey.velocityY = -12;
    }
    
    if(stoneGroup.isTouching(monkey)){
      gameState = "Lose";
      playSound("sound://category_alerts/playful_quirky_negative_game_cue_2.mp3");
    }
    
    if(mousePressedOver(Back)){
      gameState = "Menu";
    }
  }
  
  if(gameState == "Lose"){
    background(255);
    b2.display();
    b2.visible = true;
    Back.display();
    Back.visible = true;
    if(mousePressedOver(Back)){
      gameState = "Menu";
    }
  }
}


function banana (){
  
  if(World.frameCount%30 === 0){
    var Banana = createSprite(400,randomNumber(120,200),20,20);
    Banana.setAnimation("Banana");
    Banana.velocityX = -4;
    Banana.scale = 0.05;
    bananaGroup.add(Banana);
    banana.lifetime = 100;
    if(bananaGroup.isTouching(monkey)){
      bananaGroup.setAnimationEach("Banana_copy_1");
      playSound("sound://category_alerts/airy_bell_notification.mp3");
    }
  }
}

function Rocks (){
  
  if(World.frameCount%100 === 0){
    var rock = createSprite(400,350,20,20);
    rock.setAnimation("Stone");
    rock.scale = 0.2;
    rock.velocityX = -8;
    rock.setCollider("circle",0,0,150);
    stoneGroup.add(rock);
    rock.lifetime = 200;
  }
}  
