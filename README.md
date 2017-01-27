Frogger

[LIVE] (http://htmlpreview.github.io/?https://github.com/andyl319/frogger/blob/master/index.html)

####Play my version of the classic game frogger!

##Instructions

Users may use the arrow keys to guide their frog across dangerous and busy highways in order to get to the finish line to score points. Each point increases the speed of the cars while 5 points will increase the player's lives by 1.

##List of technology used
Javascript
Canvas

##Implementation
An issue I dealt with was how to deal with frogger death. It was easy to reset the frogger back at its starting position, but there was no time given for the user to realize they had been reset. This led to many walking right into traffic from 'button mashing'. I solved this issue by utilizing asynchronous methods provided by the Javascript library. As the frogger dies I set its died property to true.

```javascript
Frogger.prototype.death = function (){
  this.died = true;
  this.x = 357;
  this.y = 488;
  lives--;
  document.getElementById('lives').innerHTML = `Lives: ${lives}`;
  if(lives === 0){
    frogger.end = true;
  }
};
```  

Then in the main method, before I request an reanimation, I check the frogger's 'died' property for true. If it is, I give an empty HTML element I have designated with the ID 'died' text to post to the screen, then call a setTimeout on the start function which will start the game back up again after a 1 second pause.

```javascript
function main(){
  let thisTime = Date.now();
  let deltaTime = (thisTime - lastTime) / 1000.0;

  update(deltaTime);
  render();

  lastTime = thisTime;
  if(frogger.died === true) {
    frogger.died = false;
    doc.getElementById('died').innerHTML = 'DIED!';
    setTimeout(start, 1000);
  } else if(frogger.end === false){
    wind.requestAnimationFrame(main);
  }  else {
    doc.getElementById('game-over').innerHTML = `GAME OVER`;
  }

}
```
##ToDos
Music with a mute button
Create Frog jump animation and facing different directions
Create a water obstacle with logs and lily pads
