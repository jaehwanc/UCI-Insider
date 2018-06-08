# UCI-Insider

UCI have schedule of classes for every quarter and many students use this webpage to choose the course 
they should take. But the web page have very limited query data in a way that students don’t really use 
those query. They just use the department name and see the courses since the queries they have to choose 
is very unfamiliar and very limited. We obtained the idea from this schedule of classes and tried to develop 
our new searching and matching system within the UCI. Especially we added recommendation features to improve 
the quality of search system.

Moreover in every quarter in UCI, a lot of different classes are opened but the students don’t have enough 
time and class units to enroll all of those classes. Also, they might miss the best classes which can perfectly 
fit their interest. In some cases, students need to walk a lot between the two classes so they might late for 
the next class every time. Thus, to mitigate these issues, we tried to present a best matching classes to users 
by ranking classes according to the user personal preferences and other student’s rating records of the class.

Our system is mainly focused on 2 parts: searching for classes and getting suggestion of classes. First we will 
show how our application implemented and showing the data from the start.

a) Log-in:
When the users login to UCI insider, they need to input UCI student ID and password. If fail, then user need to 
re-attempt the login process. UCI Insider server will use the user’s UCI student ID to login to the EEE website, 
and crawl history of classes that the user took before. Such history data will be used to understand which features 
of classes can be the most interesting fact to the user. In addition to login, the server will return the token to 
our system so that the system can verify who is the user if needed.

b) User page:
We show all the class lists that the user is currently taking in this quarter. This lists will be received from our 
server from via HTTP POST connection and get the json user data. Each classes that are listed have it’s own class 
detail page. In the class detail page, the user is able to check information about the course such as professor, 
class time, location, and rating. And, the user can take a picture and tags using Krumbs in class review page. 
Krumbs captures the picture with ratings which shows the degree of the classes based on how much it was helpful to 
students and how hard was to user, and what kinds of information and materials was used for standard grading of the 
course.

c) Searching for classes:
User can search for any classes that opened in this quarter. We provide user-friendly UI to make it notable at one 
glance. The classes that are crawled from the UCI schedule of classes will be used as database for our search system. 
Classes can be searched by using many factors such as keyword, time, and department.

- Keyword: the system supports the user query while searching classes. The keywords can be teacher name or class title 
or class code even building name. Any query will be processed and used as an input to find matching classes.

- Department and time: both are used as filter in our system to improve the search result. There can be many classes 
that are not really related to the results, so the using the big figures such as department, we filter the only 
relevant data. Also in this case, the time could be divided by the days and AM/PM. The system also embrace specific 
time features such as “9:30 AM Monday”. Other than this keyword and filtering, we show the results from the highest 
rate to lowest. 

d) Class suggestion:
At first, our system analyzes the classes that user tok and then calculates the three most-frequent departments of 
classes that user took previously. The system rank the classes and get the recommendation result from the database 
by considering those three departments since the user will have more preferences for those department courses.
