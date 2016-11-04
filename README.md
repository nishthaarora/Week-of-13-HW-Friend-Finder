#Week of 13 HW: Friend Finder - Node and Express Servers
<hr>
<br>
##Overview
<hr>
In this activity, i have built a compatibility-based "FriendFinder" application -- basically a dating app. This full-stack site will take in results from users' surveys, then compare their answers with those from other users. The app will then display the name and picture of the user with the best overall match.

I have used Express to handle routing. This app is also available on Heroku.

<hr>
<br>
##Usage
<hr>

This app has 10 questions. Each answer has a scale of 1 to 5 based on how much the user agrees or disagrees with a question.

**Server.js** file require the basic npm packages express, body-parser and path.

**html-routes.js** file has two routes:

1. A GET Route to /survey which should display the survey page.
2. A default USE route that leads to home.html which displays the home page.

**api-routes.js** file contains two routes:

1. A GET route with the url /api/friends. This will be used to display a JSON of all possible friends.

2. A POST routes /api/friends. This is used to handle incoming survey results. This route is also used to handle the compatibility logic.

All the data is stored in an array in the **data** folder in **friends.js** file.

#####User compatibility logic
1. Converting each user's results into a simple array of numbers (ex: [5, 1, 4, 4, 5, 1, 2, 5, 4, 1]).

2. With that done, comparing the difference between current user's scores against those from other users, question by question. Adding up the differences to calculate the totalDifference.

3. Example:
User 1: [5, 1, 4, 4, 5, 1, 2, 5, 4, 1]
User 2: [3, 2, 6, 4, 5, 1, 2, 5, 4, 1]
Total Difference: 2 + 1 + 2 = 5

4. Using the absolute value of the differences. Putting it in another way: no negatives! Both 5-3 and 3-5 are calculated as 2, and so on.

5. The closest match will be the user with the least amount of difference.

6. Once the match is found the current user's most compatible friend, displaying the result as a modal pop-up.
The modal displays both the name and picture of the closest match.

