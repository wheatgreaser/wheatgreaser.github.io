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

## july 2, 2024:
to send the vertex data to vertex shader we first need to allocate some memory for it in the GPU. we manage the gpu memory by using vector buffer objects, these basically process the data of the vertices all at once instead of like one at a time. 

![vbos](/images/imagesforopengl/12.png)

we can use different types of buffers but the one they're using in the tutorial is a GL_ARRAY_BUFFER, which allows us to bind several buffers concurrently. now we copy the user data (the triangle vertices) into the currently bound buffer (gpu memory allocation). now we can pass several of these user defined data (datas??) simultaneously for allocation in gpu memory. now im using a GL_SATIC_DRAW argument which means the data is set once and and accessed many times (the data doesnt change). ok now we stored the vertex data in the gpu by using vertex buffer objects. NOW we can make the fucking vertex shader. 

the shaders are written in a "shader language" called GLSL, whcih is like a local language for opengl shader programming. its super similar to C so it shouldnt be that big of a deal. ok so here's the vertex shader:

![vertexshader](/images/imagesforopengl/13.png)

lets break it down (its hammer time (no im not 30 i just like that song)), first we specify the opengl version as 3.3 next we assign the position of the vector in "vec3" input variable (basically a mthematics vector instead of the stupid array masquerading as a vector). we also set the location of the variableas "0". next we assign this data into a vec4 variable with the fourth argument being a bit of a mystery for now. this is called a simplified version because we did 0 preporcessing, the input data was just assumed to be in the normalized range, but in real applications thats not the case. then we compile the shader.

## july 3, 2024:
now we need to write the fragment shader which is the shader that determines the final value of the pixel on the screen(by taking the whole game scene(lightning, visual effects, shadows, etc) into account (but in this "game" there is no game scene so we're just going to be giving the fragements solid color), also technically the final final color is determined by the blending stage because obviously if an object is in front of it itll get clipped). now we're noobs so we're just going to be rendering a constant orange pixel for our triangle. 

now we need to link all the shaders together. its like putting together different lego pieces. we do this by creating a shader program object and then linking them together, opengl basically links the output of one shader to the input of the next shader. damn i never though id say this but, opengl really makes things easy for us. i mean, look at this shit:

![linking shaders](/images/imagesforopengl/14.png)

and we can start the process by using glUseProgram(shaderProgram). fucking easy. we finally delete the shader objects (i dont exactly know why).

we have our shaders and the vertex data but opengl still doesnt know how to connect the vertex data to the vertex shader attributes. our vertex buffer data is stored in the gpu like this [credit](https://learnopengl.com/Getting-started/Hello-Triangle). 

![vertex buffer format](/images/imagesforopengl/15.png)

we have to take the vertex input (from the gpu memory, which we assigned to it with the help of a vertex buffer object) and take the first value and assign it to x and then the next to y and the next to z of the vertex shader vec3 thing we wrote. atleast thats how i understand it, the website skims over this part so dont blame me if i got it wrong.

now to summarize:

![summary](/images/imagesforopengl/16.png)

we take the vertex data assign it to gpu using a vertex buffer objects then we take it out of the memory and assign the attributes to the shader, then we start the graphics pipeline where the output of the first step is the input of the second step and then we draw the object by using some method.

now we need to make a vertex array object. i know, i know im getting sick of the vertex too but we're almost there. i hope. im not sure what this fucking thing does. im banging my fucking head but the explanation given is so vague and cryptic. so as i understand it (take it with a pound of salt) the vertex array object just has these vertex attributes "on hand" so they can be easily assigned. maybe i'll understand this better when i go through more advanced shit.

![imcrying](/images/imagesforopengl/17.png)

I MADE A TRIANGLE I MADE A FUCKING TRIANGLEN HAHAHAHAH LETS FUCKING GOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO. but i still feel a bit icky because i dont understand the VAO part.

## july 4, 2024:
i think i understand how VAOs work. they basically store the intial vertex data, it allows us to basically pass in all the data as one, for instance the color, position, etc are all combined into one object and sent in. this basically allows us to work with multiple vertex buffers easily(remember the vertex buffer object allocates the vertex data to the gpu so it needs to allocate the postion data to a part and the color data to another part, by doing this we make the allocation process easier for us).

now we NEED to make a square. since youre a fucking idiot you might be thinking that you could just create two triangles and join them, but you absolute fool there are now two duplicate vertices, did you consider that you moron?? what if i wanted to make complex model, will they all just overlapped, are we doomed to make duplicate vertices forever? no. thats where the element buffer objects come in, they use something called indexed drawing where you just specify the vertices and the order of the index in which they are to be generated. for example:

![element buffer objects](/images/imagesforopengl/18.png)

the rest of the shit remains the same.

ok so in the tutorial im following they give shit like "assignments" and im a nerd ass loser, so im going to do it. the first one seems easy: make two triangles adjacent to each eachother, this is super easy(but my method involves duplication). in the second one i have to color one triangle orange and the other one yellow. this one also seems easy because we just part one set of vertices down one pipeline with the fragment shader outputing orange color and the other set down another pipeline which contains the shader which outputs yellow color.

holy fucking shit. i accidentally corrupted the project file. I FUCKING MANAGED TO RECOVER IT USING GIT HAHA. wowoowowow. version control seems mundane till you desperately need it.

ok so the tutorial is diving deep into shaders. which i think is cool because i dont really understand glsl, the language you use for scripting shaders (its sort of like C).

the input variable in the context of the vertex shader is called a vertex attribute, this is the "vertices[]" array we pass in the beginning of the graphics pipeline.

in glsl a vector is a component conatainer for instance vec3 has 3 components: x, y, and z. we also use another container called rgba for storing colors, if you recall these different things represent each pixel (position, color) and these get passed into the VAO which allocates the vec3 to a particular VBO and that assigns the first value to x the second to y and so on. there's this cool feature in glsl called swizzling. this is where you play around with the vector components, and honestly its super intuitive.

![swizzling](/images/imagesforopengl/19.png)

we specify the location of the position vector (in the gpu memory) using layout location = 0 which sets the starting index of the "array" which represents the memory to be 0.

![location layout](/images/imagesforopengl/20.png)

for example in this snippet the "input" is referenced as the aPos vector. we basically copy the vertex data into the aPos vector by referencing the 0th index of the gpu memory and adding 4 (because integer is four bytes) for each successive component. so 0 - 3 will be X coordinate, 4 - 7 will be the y coordinate and so on. 

 the fragment shader also requires a vec4 output so that we can decide the output color. 

uniforms are a way to pass in data. uniforms are global so they can be accessed by any part in the pipeline. 

now using uniforms i made this (ok not me i followed the tutorial) sick animation where the green value of the output of the fragment shader changes according to a sine wave (so the green color changes periodically). its nuts. lets break down the code.

![uniform sine green](/images/imagesforopengl/21.png)

right. so we basically set the green value as a function of time using the glfw library. then we store the location(memory address) of the uniform ourColor (which contains the output color data of the fragment shader) into a variable.then we invoke the glUniform4f function which we use to set change the color at the memory address of the ourColor uniform.

you might have noticed in the last entry we just set the output as a particular color we did not recieve it as an input. i also mentioned how the VAO deals with the pos, color, etc to send them to the relevant vertex buffer object which in turns assigns them to the gpu memory. well, now we set the set the color data as an input.

## july 5, 2024:
so now we specify the location of the color data using layout location = 1 (we gave location = 0 for the position data). so the memory representation looks a bit like:

![memory rep](/images/imagesforopengl/22.png)

now we also modify the fragment shader to let it take the color data as an input. now we get the final output as:

![fragment interpolation](/images/imagesforopengl/23.png)

now we dont expect this output, we specified three colours so how did we get this weird ass blend. this is because of soemthing called fragment interpolation. bacially during the rasterization stage the vectors get mapped to pixels and during that process many fragments are created (not just 3) if you remember a fragment contains all the data about a pixel. now the rasterizer does something clever, it determinses the color of the fragment by taking the position of the pixel into account. for example if a pixel is in the bottom left it should be more green-y.

i just wasted 2 hours trying to configure neovim. fuck me. windows is just so ass for this type of shit. i should switch to a better OS. fuck windows. fuck this shit. 2 whole hours gone down the fucking toilet.

alright. now we need to deal with textures.

