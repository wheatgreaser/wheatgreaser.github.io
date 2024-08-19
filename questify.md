# turning daily tasks into grandiose quests
so i want to make an app. let's say you have a huge goal. let's say the goal is to publish a massive game that (hopefully) makes you a trillion dollars. let's call that the Grand Quest, the Grand Quest probably involves a Main Questline (making the game, marketing the game, getting sponsors, etc). now the Main Questline probably involves many quests, like making the assets, level design, sound design, etc etc. now the Grand Quest also prbably involves Side Quests that are optional but would enhance the overall Grand Quest. life would be much simpler if you were able to break every huge project and gamify it like this. it would also be cool if you were able to assign a set amount of xp to each quest (therby being able to quantify the importance of a particular quest). you can also classify different parts of the quest into "arcs". the coolest part of this project is the fact that you can breeak down a HUUUUGE goal into like daily tasks. 

small problem. i dont know how to make an android app. 

## 10th August, 2024:
ok so im going to be using kotline, not java, even though i know java better. most of the docs are in kotlin so im just fucked. 

## 11th Auguest, 2024:
ok it took me way more time than id like to admit to make this:

![YOOOOO](/images/imagesforapp/1.png)

but ngl, it looks radical. 

## 12th August, 2024:
you know what would be a good idea? ill build a todo list app and then build on top of that. that would be a good idea. so lets just scrap the main page for now and make a todo list app and build the questline functionality on top of it. this would also teach me the basics of kotlin and android app development. 

## 13th Auguest, 2024:
alright. i made the basic todo list app. you can download it [here](https://github.com/wheatgreaser/greatesttodolistappofalltime). its not a trojan. basically we use something called viewmodel to implement the update to the UI. in essence we basically have an mutable list that contains lists with an id, string and a DateTime variable, we append and delete elements from the list, we create UI components according to the items in the list. we just store this shit in the local memory so if i restart the app everything goes poof. so i need to fix that. we can implement the quest functionality by treating each questline as sa series of tasks which are nothing but mini todo lists. 

for the persistent memory we need some form of database, i would prefer postgresql as ive dealt with that before. 

## 16th August, 2024:
WAIT. THERE'S A BETTER METHOD!!!!!!!! we can use something called a room database to store data. its basically a local database. LETSGOOOOOOOOO. 

## 19th August, 2024:
the basic rundown of the app is as follows, we have an input box and a button when we click the button (we trigger the event) we send the data in the input box to the ViewModel (which keeps track of the UI) then we send that data to a class called TodoManager which has the list into which the input is pushed. the same thing happens in reverse for the output (we send a request to the viewmodel which in turn sends a request to the TodoManager which returns the value to the ViewModel). Now what we wnat to do is to push the data in the TodoManager into the database (roomdb) so that the memory is persistent, i.e, the todolist items dont get deleted everytime i close the app. roomdb provides a layer of abstraction over the SQLite database. what we want to do is we want to replace the TodoManager with a DAO (data access object) the object basically gets all the entities within the db and also persists the changes made (i.e, items added to the list) to the db. now we can basically do CRUD operations on the database. 

AND IT WORKED. DAMN IT WAS THAT EASY. 