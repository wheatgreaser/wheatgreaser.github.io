# Its aping time
im going to api it out. if youve been in the valley(i've never been to silicon valley) for as long as i have you have to learn apis its jsut the rules, its in the fuckjing constitution.  
so im going to learn to api.  
ceo of google moment (im skillmaxxing, based and faangpilled).

## 28 januray, 2024:
i just got the virtual enivironments all setup. i got all the packages(package haha) installed. lets fucking do this. 

## 29 january, 2024:
do you even schema bro? i just learnt what schemas are. its so intuititive this [video](https://www.youtube.com/watch?v=0sOvCWFmrtA&t) is great.
the thing i cant begin to comprehend is, why am i learning how to build apis? i dont even like web development but this is fun, i dont know why.
pydantic and postman are so useful. this is actually fun what the fuck?

## 30 januray, 2024:
CRUD is beginning to sound like a racial slur. it really does. BUT, i made a (sort of) fully functioning CR application (local memory , its just an array, not a database).
i hope i'll recieve my fields' medal once i complete the UD part. the part is till dont get is how this is going to be integrated into the front end.
how do you actually update the body of a POST request in front end, how do you actually display a GET request, HOW? i understand how it works with postman,
i also sort of get the backend part as to how the database might be implemented instead of an array in the local memory, but the frontend part is still a mystery,
i have faith that they will cover it later in [this video](https://www.youtube.com/watch?v=0sOvCWFmrtA&t)

## 31 january, 2024:
THE CRUD IS COMPLETE. i actually did the UD part. the turing award is mine. the next part involves databases. im excited but i want to actually process, the stuff i learnt, so
im going on a side quest. new side project: library api. yes. you can add books and retrieve books (CR come on i dont wanna do the whole thing again, im not a masochist). if i do this side project i'll actually be
able to use what i learnt: schema, path parameters and exception handling. 
ok here's the repo for the [library api](https://github.com/wheatgreaser/library_api). 
i wanna build this api up (in the future) wiht frontend stuff(plain js and html). i also found out how frontend is integrated, we use something called FETCH api for javascript with that we can make
http requests. for making asynchronous requests (i'll find out what that means later) there is something called ajax. so yeah i wanna integrate frontend too. i want to make an actual completed website using apis and databases. it'll be great. 

## 1 february, 2024:
potgressqling begins. so i have a plan. im going to follow [this video](https://www.youtube.com/watch?v=0sOvCWFmrtA&t) till the 5 and half hour mark (till the end of ORMs), then im gonna work on my project.
then ill return to it later if im interested. 

## 4th february, 2024:
postgress. it was easy. BUT I FUCKIGN FORGOT MY PASSWORD IN THE BEGINNING. i was sad. then i fixed it by deleting and reinstalling it. yes. this segment was actually really easy (i watched the tut in 2x speed) because i already knew SQL i learnt it like a year and a half ago so it was like a recap. after this part we're actually going to connect python with postgress HOW FUCKING INSANE IS THAT, if know how to do this part im practically a programming wizard. see, i already know html, css and vanilla js so using some random ass module i could make a HTTP request (lets say GET) then this is processed by FastAPI(which i already know the basics of), so now i could use python to get all the rows from the postgress server and return it, now the js recieves it in the json format, now i take that and display it, using html, css and basic js. BOOM. FULLSTACK BABY. IM SO FUCKING SMART. I SAFPJN FSKaf. i love computer science. im currently at the 4 hour mark (3 hours 50 mins to be exact), only about an hour and a half from my goal that i outlines in 31 jan. AFTER DOING THAT, i plan to return to this video and complete it tilllll the 7 and half hour mark. yes (they cover authentication and shit, ill probably get a new disrutpive idea by then). 
the parts after that, i dont think it will be useful for me as i stand right now, they cover deplyoment and migration WHICH IS SUPER IMPORTANT but not my primary focus right now. 

## 5th february, 2024:
I DID CR (CREATING AND READING) OPERATIONS WITH PYTHON AND DID SQL AND ADDED SOMETHING TO THE DATABASE. BRO. I AM THE FUCKING BEST. IT ACTUALLY GOT ADDED?! WHAT THE FUCK. i am using raw sql using the psycogpg2 module. IF I JUST COMPLETE THE UD PART, CRUD IN PYTHON. this is so cool.![databased](/images/imagesforapipage/image.png)

## 6th february, 2024:
CRUDing is done. I FINISHED IT. you can look it up [here](https://github.com/wheatgreaser/library_api). so i plan to return to this again, but i know how to build a basic api and connect a database to it and shit like that , so im going to build a project. yes. 

## 15th february, 2024:
we're sooo back. whats good my rizzlers. ok i made the pico-project. its a scheduling app(not a todo list fuck off), i wrote about it [here](scheduleboy.md). 
ORMs. it took me so long to set it up. it took me so fuckjing long because the default port was 5432 but i set postgres to 5433 because the liveserver in vscode uses 5432 which i had used to make 
shcedule boy and now its fixed. there is so much shit you have to do, but its just standard ctrl c ctrl v stuff, just like basic setup shit, like connecting to the database, open a session for each request, close the session after each request, import all these fucking libraries. AFTER DOING ALL OF THAT i created a seperate file for having the models, to create the table. this tutorial is very helpful tho. i wish the guy just stuck to rawsql but its alrgith. i wanna know both. thats how we do things in google.

## 16th february, 2024:  
i dont like orms, i mean i got it to work, but theres so much shit you have to do just to do have the quesries and responses as python objects. i am not building a multi trillion dollar enterprise, i dont need this much shit. using raw sql i just created a cursor object using the database driver then i used that execute sql statements and commit that to the databse. with this sqlalachemy shit i have to get a dependecy and create a session (for which a method was written during the setup, it just closes and opens sessions for each http request) after that i have to run a query on the models table whose reference is in another file, for making a post i use pydantic (as usual) to reference the schema and then afer i get the post i add it to the table stored in the models file, i dont like this. I liked the raw sql better. i like a single file. why are there so many fucking files.  

the main source of my fucjing confusion was the two models, the pydantic model and the sqlalchemy model. the pydantic model dictates the structure of the post request, the sql alchemy model dictates the structure of the columns of the postgres table. THIS IS SO IDIOTIC. why dont we just stick to the one postgres table and interact with it using SQL. why the fuck do you want the model of a second table and interact with it using pyhton. its nuts. asdfljnsf. anywho. i converted all the crud operations into the orm way. look at the difference:  

![alsume](/images/imagesforapipage/2.png)

raw sql is much better. BUT NOW FINALLY. i can get into user authentication and user authorization. THIS IS WHAT IVE BEEN FUCKING WAITING AGES FOR.

## 17th february, 2024:
pydanitc is the only thing that is keeping me sane. god bless pydantic. it validates the the input AND the output(respone). what the hell? what an amazing module. i also finally figured out what some of the "black box" stuff was. depends is apparently a dependency injection (i dont know what it means but it sounds very smart). i like python unpacking operator. its nice. automatically unpacks the dict for you. intially i hated how it looked (weird asterix looking mf) but it is useful. i dont have to go like models.PostData(posttitle = post.title, postcontent = post.contnent, ...) isntead i can just do models.PostData(**post.dict()) yeah. ima a progamer.  

ok the password part is over. hashing baby. its a one way street. in the tutorial they use bcrypt algorithm, so i used the same thing. blowfish. what a goofy little goober. fucking blowfish is protecting your account data in case of a database leak. thank him/her.  

![arkhamalsume](/images/imagesforapipage/3.jpg)

so now that the password part is over. we've come to the part ive waited so long for. loading a user specific profile page. this is so fucking cool. but before that we have to do routing. routing asnn dffns . PLEASE I JUZT WANT TO AUTHORIZRE USERSD DSLJND SJND S I DONT CARE IF MY CODE IS CLUTTEREDSF KNSD. ok. ill do routing. thats what we do in big tech comapnies. we route shit. you know? thaats what i did in amazon. ok. the router part is over. to be fair. it was worth it. my api looks so clean now. LOOK AT THE FUCKING DOCUMENTATION (its so pristine):

![hehehehaw](/images/imagesforapipage/4.png)

ok. FINALLY. I REACHED THE JWT PART. LETS FUCKING GO. FINALNDJNSDJN, SHITTING AND PISSING RIGHT NOW.
