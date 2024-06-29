# making a gaming engine - im 99% sure im going to regret this
i like graphics. moving things on the screen? yum. love it. i also thought it would be a good break from the web. i also like video games, ive made games(ok fuck you, unfinished miserable projects that barely pass the minimum requirement of what can be considered a game) in unity before. and i also want to do that in the future, but i really want to know how the engine actually works, and also it would allow me to build my own fucking engine whcih can be tailor made for certain types of games. i know its going to be no Unreal Engine but still. also to flex. i really want to show off my own game engine.

## 29 june, 2024:
ok im using OpenGL obviously. but what the fuck is OpenGL? some "people" call it a graphics API others call it a "state machine". as i understand it, OpenGL basically provides you the tools with which you can do shit like loading a window, drawing a triangle and shit like that with the help of graphics libraries. if game engine is the tool with which you build/"run" the game, OpenGL is the tool with which you build the game engine. im following [this tutorial](https://learnopengl.com/) because people call it the best.

it helps to think of OpenGL as a state machine because the things that OpenGL is dependent on its current state/context variables. for instance if we want to OpenGL to draw triangles instead of spheres we change a specifc context variable. most of the shit we do in OpenGL working with state-using functions (draw spheres) and state-switching functions(stop drawing spheres draw triangles). basically a collection of variables determines how it operates thats it.

this segment explains objects in OpenGL way better than i could:
![objectsinopenGL](/images/imagesforopengl/1.png)

so when an object is created, we bind it to the whole OpenGL context, then we set the options (because the object is just a bunch of state variables (which are a subset of the state variables of the whole context)) and then unbind the object. for instance lets say i have a 3d model of twin towers (fly high bro), the object will just act as a container and when we want to draw the 3d model i just bind the object to the context.

opengl is such a bitch. the motherfucker cant create window, define a context or handle user input. we need another library called GLFW that does all that. 

holy fucking shit. bro. it took me 1 hour to setup this whole thing. jesus fucking christ. ive never felt more like a noob, i had to install these binaries and "build" it like wtf, bro these sweaty nerds, why do they do shit like this. after an hour of hating myself, i managed to add all the libraries. AND AFTER THAT i had to fucking add these directories to visual studio, which gave me several cardiac arrests by saying "cannot run" which turned out to be beacuse it was trying to run my project which doesnt have an exe file. after this shitshow i managed to set it all up (i felt like i did molly after it worked (ive never done molly before)). lads, does this horseshit ever get easier??

now i have to create my own window. like a caveman. but its also exciting, its like im playing around with something super fundamental. ok i think i fucked up. i dont know as much c++ as i think i do. so i have to refer to the c++ docs while also doing this. brutal. 

## 30th june, 2024:
I MADE A WINDOW I MADE A WINDOW I MADE A FUCKING WINDOW HAHAHAHAH LETS FUCKING GOOOOOOOOOOOOO. 

![imadeawindow](/images/imagesforopengl/2.png)

the process is actually straight forward?? like wtf. lets run through each line of the code. first we have:

![headers](/images/imagesforopengl/3.png)

these are the header files. we already know that we use GLFW for managing windows and shit. next we have glad, glad maanages function pointers for opengl because the address of the function pointers are OS-specific and opengl is dumby-dumb and doesnt know the address of the function pointers. 

next we have:

![coreshit](/images/imagesforopengl/4.png)

basically telling glfw that the version of opengl is 3. we also set it to core profile which only includes the modern opengl features (no backwards compatibility, womp womp). now we create the window object, like so:

![windowsss](/images/imagesforopengl/5.png)

the window object holds all the data about the, you guessed it, window. i think the comments i added were self explanatory.

now we specify the position and size of the window using this:

![positionandsize](/images/imagesforopengl/6.png)

the window should also change its size and position when the user adjusts it, so we add this lil method:

![updatesizeandpos](/images/imagesforopengl/7.png)

technically rn we have created a window buuut if we call it rn it will just execute once and close, we need to keep it running till the user explcitly closes it, so we create something called a render loop. the render loop keeps "rendering" the window till the user explicitly stops it. 

![renderloop](/images/imagesforopengl/8.png)

The glfwWindowShouldClose function checks at the start of each loop iteration if GLFW has been instructed to close. If so, the function returns true and the render loop stops running, after which we can close the application. the glfwPollEvents checks if there an event was triggered (keyboard input, mouse movement, etc). the swap buffer updates the color buffer of the screen. i also came across this cool snippet of how shit is actually rendered using a double buffer. 

![doublebuffer](/images/imagesforopengl/9.png)

i also added things like changing the color of the screen by changing the color buffer, and i also added user input where you exit the window if you press the escape key. these two things are added part of the render loop, so it is done during each iteration (user input is checked for every iteration and the color is set during every iteration).

that was it. that was actually easier than i thought. glfw made windows like super super simple. 


