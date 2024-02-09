# scheduleboy - for professional workaholics
if you want to become the next jeffrey geezos you need to put in the work. put in the hours. but if you put in a lot of work, 13 - 16 hours for example you end up wasting a lot of time due to poor planning. unacceptable. prepostrous. so to study for longer durations of time i invented the next big thing.
i made this ""FuLl - sTaCk" application to solve it. i recently learnt FastAPI so i want to put my skills to the test.

[final result](https://github.com/wheatgreaser/scheduleboy)

## 7th of februruaaury (i really cant spell february):
i completed the fastapi, postgres, sql(very very very small amount of sqp, but if you list a lot of things people think youre a wizard so deal with it sucker) and the js for fetching the data from the api. the fastapi and database took me 20 mins. WHAT THE FUCK.
IT WAS SO TRIVIAL. i made like 3 http requests, one post, one get, one delete, THATS ALL. the postgress database setup is also super trivial. THE JS PART THO. OMFG. it was sos shit. apparently this thing called access control origin which is diabled by default.
it took me so long (40 mins) to fix. I THOUGHT THIS FRONTEND js was supposed to be easy?? i thought backend was hard?? but i did it. now i used Fetch API to make the http requests and made it into a js object. the part i have to do next is, get properties of the object and display it in html.
and also to make a form to post data. it should be easy. it sounds easy. it feels easy. but for some reason i feel fear. so heres what im going to do, im going to take the js object lets call it task object, its going to contain all the tasks (who are objects themselves),
now im going to loop through the task oject and display individual tasks(time alloted for the task, title of the task, content (brief desc.)) in like 5 html elements, now im going to set upper bound to 5 (5 tasks max) but im going to terminate the loop before that
if size of the task object is reached. now once a task is completed i should be able to delete it. simple enough. i want to make it look pretty. so probably css. and call it a day. thats how we do things at google.

## 8th feb (heh):
i hate css. what hte fuck is this thing. i hate frontend. it took me more time to go from this 

![image](/images/imagesforscheduleboy/1.png) 
to this 

![image](/images/imagesforscheduleboy/2.png) 

than it took me to program the 
entire backend. this is fucking nuts.  

### later - same day:
holy shit i did it.
holy fucking shittity fuck. bro. this is so fucking insane. I GOT IT TO WORK. I SPENT AN HOUR DEBUGGING A DAMN BUTTON THIS FUCKING BUTTON WOULDNT ACTIVATE THE FUCKING EVENT LISTENER BUT WHEN I PUT THE SCRIPT IN
THE INDEX FILE IT WOULD. I FUCKING DONT KNOW. I AM NOT A PROFESSIONAL JAVASCRIPT DEVELOPER (or really a professional any developer for that matter). BUT FINALLY IT WORKED. ITS SO SEAMLESS THOUGH. like i http get
request the output and limit it to 5 and there are 5 tags to place the output, since i order it by id descending only the latest 5 will be present at any given time. so if i add a task and there are already 5 tasks, the top task would get replaced. ITS SO COOL, OMFG. here's the [repo](https://github.com/wheatgreaser/scheduleboy)

here's screenshot of the final result:

![image](/images/imagesforscheduleboy/3.png)

im actually super stoked UHASDKJH. im going to become zuccy. smell ya later shiteaters (that rhymed in my head).
