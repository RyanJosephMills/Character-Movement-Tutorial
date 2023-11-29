# Character-Movement-Tutorial

Character movement

The first thing you must do when creating a 2D character is add your character design. To do this, you need to go to the hierarchy section on the left-hand side of your screen and click on the + symbol, click on 2D objects, select sprites and then squares. Then, you will need to create a floor to do this. You do the same thing; however, you must extend the platform to have a platform. Another thing that you need to do is add a box collider to the platform for the player to walk on. After this, you must go back to the player, go over to the interceptor, and add a Rigidbody, which will control the object through the physics position. The next thing that you will need to do is add a collider to your player; however, you don't want to add a box collision to the player because it has very sharp edges on the corners of your box character, and your character could get stuck on objects so instead of doing that you need to select a capsule collider 2D this will be better because it has more rounded edges so your character won't get stuck.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/2caaf1e5-8117-41ef-9137-bbbf920f3339)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/9b30e3c1-ab27-4adb-812d-979a06d7af1c)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/c95925c3-e65c-4933-8b6a-4fc1163248b9)


Now, you will need to create a script. To do this, you must right-click in the assets menu and then click C#, creating a new script. Once you have done that, you will need to call it something that will tell you what code is inside of the script so as we are creating the character movement inside here, once you have done that, you will need to drag and drop the script on top of the player and to check the script is linked to the player you can click on the player inside the hierarchy and then look in the inspector.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/344da644-6511-4abe-8cab-5d2fc7974965)

Once you have done that, you can double-click on the script to open it, which will open up Visual Studio.

The first thing that you will need to do is grab the Rigidbody2D component into the code. This is because we are doing a character movement. The Rigidbody2D controls the physics because we are creating a character physics is what we need to move around, so underneath the Playercontroller, you will need to create a private (which means that only members of this class will have access to it) Rigidbody2D rb2D then you click enter twice to space out the code, and then you will need to create another private variable with a float (which is a decimal number) behind it then moveSpeed; then underneath get a private float jumpForce; then on the line next to it, you will need to get a private bool (which means either true or false) isJumping then underneath that get a float moveHorizontal and this will be used to get the player input to move the character around. The final thing you will need here is a private float moveVertical. 

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/316f1d2c-7638-401e-8b1d-a950ce251681)

The next thing we will need to do is add value to this because Unity doesn't know how high you want the character to jump, and it also doesn't know which way you want each Input to move in. So to do this, you will need to go to the Start section below and put down your moveSpeed and equal that to 3f (f = float); however, you will have to play with the character speed to see which speed suits your character for your game. Then you can get your jumpForce and then equal that to 60f, and this will be how high your character will jump, but again, you will have to see which jump height suits your character for your game, and the last thing to do is get isJumping and equal this to false so that Unity knows that by default the character isn't jumping. Another thing is that you will need to assign something to the Rigidbody2D, as it is empty, so we need to tell the code that there is something with a Rigidbody2D attached to it. To do this, you will need to go back into the start section and get the rd2d and equal that to a gameObject, and if you write this with a lowercase g at the beginning, it will automatically choose the game object that this bit of code is assigned to which is the player then we put . which means what the next thing to grab inside of the code is then we need to grab the component so to we type GetComponent<RigidBody2D>(); and what this does is the Rigidbody2D which was initially empty is now referencing the characters RigidBody2D.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/2d6339d8-2399-4e05-9d5a-5a2434bf85e2)


We can then go to the updates panel now that we have done that. Inside here, we will be coding it so that if the player presses a key, the character will move in a specific direction (for example, D and you move right). So to do that, you must type in moveHorizontal, which is the code you made earlier and equal that to Input.GetAxixRaw(Horizontal) what this will do is it will grab the Input that is on the horizontal axis, so it will grab A and D or the arrow keys left or right, and then you will need to type the same code. However, instead of horizontal, you type vertical for jumping up and down, and it will automatically assign it to W and S and the up and down arrows; however, this isn't doing anything as we have yet to tell Unity what these inputs do.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/95663183-8926-45ce-9396-54de1c179095)


So, to tell the character which direction to move when you press an input, you will need to create a fixed update. It is very similar to normal updates; however, it does its updates on physics just like the character movement. So, inside the fixed update, you need to get an if statement and put (moveHorizontal > 0.1f || moveHorizontal < -0.1f) inside the brackets. So, when the number is greater than 0, it will move to the right. This is because, inside Unity, one means that the character will move to the right, so that means that if the number is less than 0, then that means that it will move to the left because the left is equal to -1 inside of the code.

Then, inside the curly brackets, you will need to grab the rb2d, which is the character's physics, and then put. AddForce(new vector2) A vector2 in this code is an X and Y Axis (moveHorizontal * moveSpeed, 0f), so the moveSpeed is the bit of code we made earlier, which we assigned a number to it, so now we put it hear because if it weren't it would be set to a default of 1 or -1 and that isn't very fast so this bit of code will speed the character up. Finally, the 0f is just the Y axis, and it is set to zero because we don't want the character to jump as we move from left to right, ForceMode2D.impulse), and ForceMode2D is used to apply a specific type of force to a 2D Rigidbody. Once you have done that code, you can go into Unity and click play, and you will be able to move left and right(don't worry about the box falling over)

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/dea1e312-7e40-4b5b-ae7c-17381b970114)


So now you have added the character movement, you can code it so the player has a jump. To do this, you will again need to go into the fixed update and find some space. Once you have done that, the code you will do for the jump is very similar, so you need to get another if statement, and inside the normal brackets, you will need to moveVertical instead of horizontal and keep it > 0.1f. Then you will need to type the same thing inside curly brackets; however, again, instead of moveHorizontal, you put moveVertical and also change the moveSpeed to jumpForce once you have done this, you can then go back into unity, click play and hold down W you will fly up into the air this is because the code is constantly jumping us, so what we need to do is code it so that the character checks to see if we are on the ground so that we can jump once.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/e94a8fe5-7fea-4a79-a1e8-f24786e5470a)


To do this, you need to go to Unity and select the player, then add a box collider 2D to the player. Once you have gotten that, you must ensure the trigger is turned on to tell us if the player is hitting the ground. The next thing that you will need to do is re-size the box and move it so that it is just hanging at the bottom of the player so that way it can make contact with the ground without having to make the player go through the ground another problem that we have not solved yet is the fact that the box falls over when you move around so to fix this problem inside your player go to the RigidBody2D and under constraints you need to freeze the Z axis so that it won't fall over. Now, head back into your code, and underneath fixed updates, you will need to get another built-in method called OnTriggerEnter2D(collider2D collision). Then, inside the curly brackets, get an if statement, and inside the brackets, type collision.gameObject.tag == "platform" This will remain red underneath the code because we don't have anything inside our game called platform; however, in the curly brackets, we get isJumping and equal that to false.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/58b1240a-294a-48c1-bfe5-97c8a7222f47)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/9f2ce490-66be-4a05-9f18-c16f4dfe0f00)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/c2a7e57c-4f3e-4072-b44f-096ae2473a86)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/8aa68431-fa41-4ad8-b36f-117adace8624)




So, to fix the platform problem, we need to go back into Unity and select the player, and right at the top, you will see something that says tag. You must click on that, add a new tag, and call that platform. Then, we must click on the ground and change the tag inside to the platform we just made.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/0abda5ef-5147-470e-96ea-4ded5f65705a)
![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/0c34b2f6-13d9-4ffc-a814-ff975c870d6a)


So now the code registers as when the player is touching the ground, he is touching the ground; however, we haven't coded it so that when he jumps, he's not touching the ground, so to do this underneath the code you just made, you will need to get something called OnTriggerExit2D (collider2D collision) then you can copy and paste the same bit as code you made earlier however instead of putting false you put true.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/5153c575-2c64-4243-9dab-94ba8ed35f60)


Now that we have done that, we need to ensure that our isJumping has an effect when you click the jumping button. So, to do this, we need to go back into the Fixed update in the moveVertical if statement. We need to check to see isJumping is false. So in front of moveVertical, you will need to put !isJumping and two && so what this does is the ! checks if the player is on the ground or not. Now that you have done that, you can save it and go back into Unity, and you should be able to jump like a normal character in-game.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/6a4437a8-f8d2-4ad8-a9c1-8003a4cd2743)


The final thing we will be improving is how the jump looks. To do this, you go to the player and inside or RigidBody2D, you can change the linear drag to 5, and this will give you a bit more air resistance so your character won't just fly up into the air then you can change the gravity to 10 and finally change the collision detections to continuous and what this will do is sometimes if you are going to fast your character will go through the wall so if you have this switched on it will prevent that as it is running constantly.

![image](https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/ea6b069e-a0c2-4a22-8f38-de3fb4531244)

https://github.com/RyanJosephMills/Character-Movement-Tutorial/assets/146854317/04cd705a-04c1-448b-9518-5bab3506e0a7

