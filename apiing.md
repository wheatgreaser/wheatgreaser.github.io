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

wow this guy made jwts super simple. i thought it was going to be some advanced cryptographyt shit, but it was actually super simple. basically the the user logins in by sending in the email/username and the password and then we hash the given password and compare it with the stored password, if it matches we give him a token. this token basically has three parts: a header, payload and a signature. the header just has information about the algorithm used. the payload is going to have the email, role(normal user or admin/staff), id, etc. the signature is formed by combining the header, payload and a 256 bit sectret (no one except us will know the secret). now we send the token to the user.the user can access his posts/settings/his page that is only supposed to be visible only to him by providing the token in the header of the request. badabing bada boom login complete. the jwt token is accessible to the user, so what if he were to change the id to access someother users account, aha thats waht the signature prevents, if you change the payload the signature will change and the api will reject your request since your token is invalid now that youve changed it.

## 26th june, 2024:
so. its been a while. howdy? i forgot everything about apis. how fun. anywho to exercise my api "muscles" i want to a build a project. ok fuck you yes its a stack exchange clone. you anonymously pose questions(cause i dont know user authentication) then someone anonymously answers it. should be simple. 
things are working?? what the fuck. i setup a virtual environment and i just installed all the shit, i managed to create an endpoint for 2 get requests (getting all the posts and getting one specific post) and end point for a post request(to post a post). all i have to do now is setup postgresql to bring in some database functionality. after that i have to create the "responding to posts" part, which, lets be honest, i dont know batshit about. 

ok the databse part is done. this is so fucking sick. i can add and delete posts. now comes the fucking frontend. gods. WAIT. ive done a similar project before. when i made the scheduler i had to interface frontend, so i can refer to that, fuck yes. 

## 27th june, 2024:
ok here's the thing. I dont fucking know how to add "comments" under a post. if i make a stackexchange clone then I need to add that feature, so how am i going to do that? idk. so we're going to pivot. i'll do this till the front end post part and then ill learn authentication and shit AND after that ill return to this, so hopefully by then (when i learn user auth) i'll have some idea on how to create comments under a specific post.

HOLY FUCKING SHIT I JUST FINISHED DEBUGGING THE CORS AND I FEEL LIKE I TOOK A HUGE SHIT HAHAHA HIMA:KN D. yes. the frontend is done (no css ill get to that later). basically the user can now upload posts using a form and the data will get uploaded into the database. now displaying the posts AND creating speerate html files for posts remains. NOW FINALLY, i can start learning user auth. 

## 28th june, 2024:
so its 12 am and the difference between authentication and authorization has never seemed more clear. authentication is basically verifying the user(username password), and authorization is basically where I allow users to access certain pages. for instance each user should have a unique user profile page, and I have to authorize the user's access to their particular user profile page. I'm following this [doc](https://fastapi.tiangolo.com/tutorial/security/oauth2-jwt/) and this [guide](https://www.youtube.com/watch?v=5GxQ1rLTwaU). apparently fastapi makes things "quick" and "simple" we all know thats code for "get fucked". 

so in broad strokes, here's what we're gonna do. first we authenticate the user (check if the username and password are registered in the database), then we give the user a token. this token will grant the user access to all the api endpoints that require authorization. this token is baiscally a json object encoded into a string, thats ENCODED not ENCRYPTED motherfucker, so the token can be read and all the object data can be read. now this token has an expiry date which we can set, we can set it to 1 month or 4 seconds. this token is signed which means that if we modify a particular information about the object, the signature will change, if the user tries to modify the expiry date, the token will change. ive already explained how the token works before im just rediscovering it. fuck, im dementiating. ok the jist is basically the token is made up of three components header, payload and the signature. the header just contains info about the algorithm used, the payload has information like username, user role (admin or not), expiration date, etc. the signature basically combines these two things to "sign" it. so if we one part of the payload is changed the signature changes and therefore authorization will not be granted. usually a secret key is also thrown into this signature mix for security. easy peasy lemon squeezy. 

ok. the docs are kind of clear. there are no comments, they didnt bother to explain the utility functions but that would have just makde the docs even lengthier. for example:

![access_token](/images/imagesforapipage/5.png)

this snippet creates the jwt access token and i had to puzzle out a lot of shit to figure out what it meant. so basically we get the expiry time and add to to the time rn to get the expiry date. we create the jwt token by combining the user data (username, expiry date, etc) and the secret key which is just a 32 characters long random hexadecimal string. we also specify the algorithm. now we return the encoded jwt token to the user.

