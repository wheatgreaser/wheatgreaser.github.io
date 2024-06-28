# I can SSH into your mom
ssh is the coolest fucking thing. like ever. i really wanted to learn how ssh works so i can run servers and shit from remote and i thought it would "cool" and "interesting" to ssh into my android phone, you know, "cool". its so surreal, i can fucking access my phone from my pc and its freaking me the fuck out. 

ssh is super simple. basically you add a lock to your message (encrypt it once) then you send it to that guy (he does not have your key so he cant unlock it) then he locks it and sends it back to you now you unlock your lock and send it to him then he unlocks his lock, badabing badaboom the message is unlocked and in the entire process the the message remained encrypted. 

ssh tunneling is so sneaky. basically if your network admin is blocking a port, lets say the port to remotely connect to a windows desktop (port 3389). now what we do is we take the data from the port 3389 and "smuggle" it through the port 22 (ssh port), and from there we can send it to the port 3389 of the windows desktop. fucking mental. this is called local port forwarding.

lets say your company has install a web filter on port 80 to stop us from watching youtube while at work, we can just use an ssh tunnel to smuggle info in and out of the server by an ssh tunnel using a socks proxy. 

i just sshed into my android phone and its fucking trippy like wtf, i can just transfer files and shit. 

i found [this](https://www.youtube.com/watch?v=dPAw4opzN9g) amazing video on how SSH keys work. there are two keys: the public key and private key. anyone can have the public key, but the private key is yours and yours alone. so you calculate the public key from your private key (vice versa is not possible) and then the server takes a random string and encrypts it using the public key (the encrytpion can only be broken by the private key), then we decrypt it using the private key, and we send the proof that we decrypted it back to the server (not the decrypted text itself). once this is both get symmetric keys which is used to encrypt the data during transmission (as i explained before).