# making a gaming engine - im 99% sure im going to regret this
i like graphics. moving things on the screen? yum. love it. i also thought it would be a good break from the web. i also like video games, ive made games(ok fuck you, unfinished miserable projects that barely pass the minimum requirement of what can be considered a game) in unity before. and i also want to do that in the future, but i really want to know how the engine actually works, and also it would allow me to build my own fucking engine whcih can be tailor made for certain types of games. i know its going to be no Unreal Engine but still. also to flex. i really want to show off my own game engine.

you can find the repo [here](https://github.com/wheatgreaser/learningopengl)

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

### graphics pipeline:
the graphics pipline takes 3d coordinates and displays it as 2d colored pixels on the screen, easy right? wrong. fuck you. the graphics pipline basically has a bunch of steps linked with eachother such that the input of the current step is the output of the previous step. we can run these "steps" in parallel. each step runs a small piece of code we call them shaders. the gpus leverage the parallelness and squeeze out maximum efficiency. if you are a fucking nerd (which i assume you are because you are reading this) then you can customize the shaders, theres this language called opengl shading language with which you can customize them. ok so here's the graphics pipeline ([source](https://learnopengl.com/Getting-started/Hello-Triangle)):

![graphicspipeline](/images/imagesforopengl/10.png)

ok lets break it down.
1. vertex shader: takes the 3d coordinates (which are in the form of a vertex(vectors)) and transforms them into a different set of 3d coordinates we can work with. the vertex just consists of the 3d coordinates and color.
2. geometry shader (optional): basically we add other vertices to more vertices to modify the primitive shape, in the image given they added another vertex to create 2 triangles. 
3. primitive assembly: takes the geometry shader/vertex shader output and joins it to make a shape (2 triangles). 
4. rasterization stage: we map the primitives to pixels on the screen (this is the exciting part imo) resulting in fragments. fragment is all the data required by opengl to to render a single pixel(color, position, etc). we also perform clipping where we hide things out of our view to save up on resources. we then pass these fragments to the fragment shader.
5. fragment shader: fragment shader finds the final color of the pixel by taking all the objects in the 3d space into account (shadows, lighting, etc).
6. blending stage/alpha test: we check if the fragment is behind or in front of other objects and we have to discard the data accordingly. 
modern opengl is such a dick. we need to define our own vertex AND fragment shader. 

the 3d coordinate input that we give opengl is in a range b/w -1.0 and 1.0 we call this the normalized device coordinates range, any coordinates that lie out of these coordinates get clipped. the vertex data is just this:

![vertex data](/images/imagesforopengl/11.png)


to send the vertex data to vertex shader we first need to allocate some memory for it in the GPU. we manage the gpu memory by using vector buffer objects, this basically process the data of the vertices all at once instead of like one at a time. 

![vbos](/images/imagesforopengl/12.png)

glBufferData is a function specifically targeted to copy user-defined data into the currently bound buffer. Its first argument is the type of the buffer we want to copy data into: the vertex buffer object currently bound to the GL_ARRAY_BUFFER target. The second argument specifies the size of the data (in bytes) we want to pass to the buffer; a simple sizeof of the vertex data suffices. The third parameter is the actual data we want to send. the fourth parameter specifies how we want the graphics card to manage the given data. since the position of the triangle does not change with time we use GL_STATIC_DRAW. if we GL_DYNAMIC_DRAW we allocate memory that allows faster writes. now we have placed the vertex data inside the gpu memory by using a vertex buffer object (gods i sound like a fucking nerd), now we can make a vertex shader that can process this data.



