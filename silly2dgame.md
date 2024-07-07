# quest to make a 2d game using my custom game engine
so i learnt a bit of opengl and my ego is super inflated. so i want to make a 2d game to really test my skills.

# july 7, 2024:
so im going to make an rpg. yeah. no im not a masochist. yes rpgs are harder than a simple platformer. but this should give me new ideas and a fresh perspective. just kidding i dont give a fuck about "new ideas and perspective" i just think rpgs are fucking wicked. 

ok so we're going to sdl2, ITS JSUT A FRAMEWORK NOT A GAME ENGINE SHUT UP. ok. it simplifies things a lot, yes. fuck you. im not being a little bitch. i dont want to spend 10 hours practicing the fun hobby that we call "suicidal ideation". sdl2 builds on top of opengl so there's that. it simplifies the redundant bullshit we find ourselves doing in opengl, while i think opengl is fun for learning shit like VAOs and how things get allocated in the memory, i dont think it will be fun to muck around system memory. i also want to finish making a game within this decade.

man. sdl2 makes things super easy. setting it up in visual studio was a breeze (i think its because i went through this whole schtick when i learnt opengl). creating a window is so trivial. look at this:

![easywindows](/images/imagesforrpg/1.png)

we initialize the subsystems (video, audio blah blah) and then we create a window object and pass it as an argument in to the renderer object. then we set the color of the renderer by passing it as an argument in to the SDL_SetRenderDrawColor(); method. then we clear the screen in the beginning (itll just be black) and we just display the renderer. thats it. thats the whole fucking thing. where the fuck is viewport? where the fuck is the frame_buffer method thing we used for updating the window when the user shifts the position. this is absolutely mental.

i decided to call the game Vunderbar Wizards which i think is a pretty sick name. here's the repo [vunderbarwizards](https://github.com/wheatgreaser/vunderbarwizards).