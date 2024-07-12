# quest to make a 2d game using my custom game engine
so i learnt a bit of opengl and my ego is super inflated. so i want to make a 2d game to really test my skills.

# july 7, 2024:
so im going to make an rpg. yeah. no im not a masochist. yes rpgs are harder than a simple platformer. but this should give me new ideas and a fresh perspective. just kidding i dont give a fuck about "new ideas and perspective" i just think rpgs are fucking wicked. 

ok so we're going to sdl2, ITS JSUT A FRAMEWORK NOT A GAME ENGINE SHUT UP. ok. it simplifies things a lot, yes. fuck you. im not being a little bitch. i dont want to spend 10 hours practicing the fun hobby that we call "suicidal ideation". sdl2 builds on top of opengl so there's that. it simplifies the redundant bullshit we find ourselves doing in opengl, while i think opengl is fun for learning shit like VAOs and how things get allocated in the memory, i dont think it will be fun to muck around system memory. i also want to finish making a game within this decade.

man. sdl2 makes things super easy. setting it up in visual studio was a breeze (i think its because i went through this whole schtick when i learnt opengl). creating a window is so trivial. look at this:

![easywindows](/images/imagesforrpg/1.png)

we initialize the subsystems (video, audio blah blah) and then we create a window object and pass it as an argument in to the renderer object. then we set the color of the renderer by passing it as an argument in to the SDL_SetRenderDrawColor(); method. then we clear the screen in the beginning (itll just be black) and we just display the renderer. thats it. thats the whole fucking thing. where the fuck is viewport? where the fuck is the frame_buffer method thing we used for updating the window when the user shifts the position. this is absolutely mental.

i decided to call the game Vunderbar Wizards which i think is a pretty sick name. here's the [repo](https://github.com/wheatgreaser/vunderbarwizards).

# july 9, 2024:
the game loop is the same as the render loop that we did during opengl, it keeps checking for user input and updates the positions, sizes, etc of all the objects and renderes them to the screen. continuously. so in the tutorial they are following "good programming practices" so they're creating a seperate class and seperate ehader files instead of mixing them all in one unholy concoction. also a lot of error handling. so here's the header that we've created that provides a skeleton for what we'll be implementing in the game loop:

![headerclasssperatefile](/images/imagesforrpg/2.png)

yes. also coming from a java perspective the concept of a deconstructor is so alien.

# july 10, 2024:
event handling is like the same difficulty as event handling in unity/c# if you can believe that. i mean look at this silly little goober:

![easyeventhandling](/images/imagesforrpg/3.png)

all that work and we've got ourselves this:

![goofy ahh](/images/imagesforrpg/4.png)

so. i made a window. same as last time BUT this time i made a whole new class and a whole new header file so that the game loop in the main file looks clean af. omg omg omg omg in the next tutorial they're going to show me how to render sprites and images. that's insane. this is actually like super easy (if we forget about the part where there was a conflict between the main file and the main file of sdl and i spent half an hour slowly dying inside).

# july 11, 2024:
okaaaaaaaaaay. you can just load fucking sprites into SDL2, you dont need to make a vertex shader and a fragment shader, you dont have to deal with VBO and VAO and the representation of them in the memroy, you dont need to do- yes you need to do texture mapping but its super simple, you basically just have two rectangles the source rectangle and the destination rectangle, and you select the part of the source recatngle you want to render onto the destination rectangle. you can set the height and width of the destination rectangle (therby resizing the image) and you can also set the x and y coordinates of the destination rectangle (thery by choosing the position of the image/sprite). i made a silly little sprite in paint3D because normal paint doesn't support transperant background. how fucking sad? fuck you billy gates (or microsoft in general). i also made the sprite move by using a regular ass update function and sleep, it was sort of like unity, BUT in unity we use time.deltaTime to make sure the object moves in the same speed in all the systems but here i didnt do that, coincidentally thats the next lesson in the tutorial. there's a lot of abstraction in SDL2. i can also find my c++ knowledge increasing, i now know (sort of) how to write header files and improt from other classes. soo, here's the result:

![yo yo yo](/images/imagesforrpg/5.gif)

did you edge to that? i feel like the offspring of micheaelangelo and davinci with a little bit of botticelli mixed in (yes i read dan brown how did you know?). but the "art" turned out to be way better than i expected. im quite the artistic genius/prodigy/virtuoso. 
