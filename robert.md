# its rossing time

ros is not an OS. its a lie. ROS is basically a set of libraries that you use to build complex robotic systems (nerd shit). 

a ros system is made up of these little things called nodes, now these nodes are kind of similar to godot nodes, they perform a specific function (sort of mini programs) and they can even talk to eachother (signals in godot omg) in ros the communication is done in the form of topics and messages. basically you publish a message to a topic and other nodes can read from the topic, the nodes which publish are called publishers (who would have thought) and the nodes which read from the topic are called subscribers (because why the fuck not). 

anyone can read from a topic (any node that is), but services are different. services are between two nodes only, they maybe the result of a calculation or indication that a request has been recieved whatever. 

nodes have the ability to have parameters, bascially i can change the behavior of a node by changing the parameter (like chanigng the serial port in which the communication occurs or whatever). 

remapping allows us to change the name of the topic. its as simple as that, its mostly used to avoid naming conflicts. 

we can modify a config file called the launch file to modify the ndoes with commonly used parameters and remappings. at the time of launch. 

a package is used to group together a set of related nodes , their config files and their launch files.

each ros project goes into its own workspace where we keep all of our packages in. when we use colcon to build our workspace it takes all the source files from a src directory, build them into a build directory and install them in to an install directory (fun i know, people always love it when i talk about building a workspace in the robert(its robert shutup) operating system).

QoS allows us to set certain rules on the messages sent between publishers and subscribers. 

### ok so wtf is a gazebo?
ok good question, its sort of like a 3d sim software, no scratch that it is a 3d sim software, basically i can test out all the features (say teleop) on gazebo before i send it out to the bot. 