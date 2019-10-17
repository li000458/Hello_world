# Hello_world


<!DOCTYPE html>
<html lang="en">
<head>
   <title>Space Invaders in UMC</title>
   <link rel="stylesheet" href="style.css"> </>
</head>
<body>
    <script> //JavaScript
       
      // var change = function (sel) {
      //   document.body.backgroundImage = sel.value;
      // }
	   var squirrels = {
	       top: 700,
		   left: 550
	   };// define the left and top of squirrels position 
	   
	   var pinecones = [];// define the pinecones array
	   
	   var bugs = [
	     {left: 200, top: 100 },
		 {left: 300, top: 100 },
		 {left: 400, top: 100 },
		 {left: 500, top: 100 },
		 {left: 600, top: 100 },
		 {left: 700, top: 100 },
		 {left: 800, top: 100 },
		 {left: 900, top: 100 },
		 {left: 200, top: 175 },
		 {left: 300, top: 175 },
		 {left: 400, top: 175 },
		 {left: 500, top: 175 },
		 {left: 600, top: 175 },
		 {left: 700, top: 175 },
		 {left: 800, top: 175 },
		 {left: 900, top: 175 },
	   ];
	       
	   
	   document.onkeydown = function(e){
	       console.log(e.keyCode);
	       if(e.keyCode == 37 ){
		         console.log("LEFT");
				 squirrels.left = squirrels.left - 10; 
				 moveSquirrels();
		   }
		   else if(e.keyCode == 39){
		         console.log("RIGHT");
				 squirrels.left = squirrels.left + 10;
				 moveSquirrels(); 
		   }
		   else if(e.keyCode == 32){
		         console.log("Fire");
				 pinecones.push({
				    left: squirrels.left + 10,
				    top: squirrels.top
				 });// push into the pinecones array the position of pincones
				 launchPinecones();
		   }// when user click the "space" key, the squirrels will launch the pincone.
		}// when user keep keydown "left" or "right", the point of squirrels left position will change.



		// This function changes the position of squirrels on the screen.
		function moveSquirrels(){
		   document.getElementById('squirrels').style.left=squirrels.left +"px";
		}
	    
		function launchPinecones(){
		   document.getElementById('pinecones').innerHTML ="";   
		   // The loop will create the pinecone object when user click the "space" key.
		   for( var i = 0; i < pinecones.length; i = i + 1){
		         document.getElementById('pinecones').innerHTML += 
				 `<div class='pinecone' style='top:${pinecones[i].top}px; left:${pinecones
				                            [i].left}px;'></div>`;
		   }   
		} 
		
		// the top of each pinecone position reduce 5
		function movePinecones(){
		    for(var j = 0; j < pinecones.length; j = j + 1){
			    pinecones[j].top = pinecones[j].top - 5;
			}
		}
		
		
		function displayBugs(){
		   document.getElementById('bugs').innerHTML =""; 
          // The loop will create the bug object	   
		   for( var i = 0; i < bugs.length; i = i + 1){
		         document.getElementById('bugs').innerHTML += 
				 `<div class='bug' style='top:${bugs[i].top}px; left:${bugs
				                            [i].left}px;'></div>`;
		   }   
		} 
		
		
		
		//give the game loop every 10 milliseconds and the pinecones print again every 10 milliseconds
		function gameLoop(){
		    setTimeout(gameLoop,10); 
			// The setTimeout() method calls a function or evaluates an expression after a specified number of milliseconds.
			movePinecones(); //execution movePinecones function 
			launchPinecones(); //the pinecones print again
			displayBugs()// display the bugs
		} 
		gameLoop();// execution gameloop function 
		
    </script>
   
     <!--<select onchange="change(this)">
        <option value="image/level1.jpg">level1</option>
        <option value="image/level2.jpg">level2</option>
    </select>choose level-->
	
    <div id="background">
	       <div id="squirrels"></div>
		   <!--<div class="bug"></div>-->
		   <div id="pinecones"></div>
		   <div id="bugs"></div>
	   </div> <!--background content-->  

</body>
</html>
