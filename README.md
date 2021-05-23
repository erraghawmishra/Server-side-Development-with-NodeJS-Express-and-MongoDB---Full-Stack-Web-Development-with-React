# Full-Stack-Web-Development-with-React---Server-side-Development-with-NodeJS-Express-and-MongoDB
Full-Stack Web Development with React:- Server-side Development with NodeJS, Express and MongoDB

<h2>Assignment 1: Node Modules, Express and REST API</h2>

In this assignment you will continue the exploration of Node modules, Express and the REST API. You will design two new express routers to support REST API end points for promotions and leadership.

Step-By-Step Assignment Instructions
less 
Assignment Overview

At the end of this assignment, you should have completed the following tasks to update the server:

Created a Node module using Express router to support the routes for the dishes REST API.
Created a Node module using Express router to support the routes for the promotions REST API.
Created a Node module using Express router to support the routes for the leaders REST API.
Assignment Requirements

The REST API for our Angular and Ionic/Cordova application that we built in the previous courses requires us to support the following REST API end points:

http://localhost:3000/dishes/:dishId
http://localhost:3000/promotions and http://localhost:3000/promotions/:promoId
http://localhost:3000/leaders and http://localhost:3000/leaders/:leaderId
We need to support GET, PUT, POST and DELETE operations on each of the endpoints mentioned above, including supporting the use of route parameters to identify a specific promotion and leader. We have already constructed the REST API for the dishes route in the previous exercise.

This assignment requires you to complete the following three tasks. Detailed instructions for each task are given below.

Task 1

In this task you will create a separate Node module implementing an Express router to support the REST API for the dishes. You can reuse all the code that you implemented in the previous exercise. To do this, you need to complete the following:

Update the Node module named dishRouter.js to implements the Express router for the /dishes/:dishId REST API end point.
Task 2

In this task you will create a separate Node module implementing an Express router to support the REST API for the promotions. To do this, you need to complete the following:

Create a Node module named promoRouter.js that implements the Express router for the /promotions and /promotions/:promoId REST API end points.
Require the Node module you create above within your Express application and mount it on the /promotions route.
Task 3

In this task you will create a separate Node module implementing an Express router to support the REST API for the leaders. To do this, you need to complete the following:

Create a Node module named leaderRouter.js that implements the Express router for the /leaders  and /leaders/:leaderId REST API end points.
Require the Node module you create above within your Express application and mount it on the /leaders route.
Review criteria
less 
Upon completion of the assignment, your submission will be reviewed based on the following criteria:

Task 1:

The REST API supports GET, PUT, POST and DELETE operations on /dishes/:dishId end point.
Task 2:

The new Node module, promoRouter is implemented and used within your server to support the /promotions end point.
The REST API supports GET, PUT, POST and DELETE operations on /promotions and GET, PUT, POST and DELETE operations on /promotions/:promoId end points.
Task 3:

The new Node module, leaderRouter is implemented and used within your server to support the /leaders end point.
The REST API supports GET, PUT, POST and DELETE operations on /leadership and GET, PUT, POST and DELETE operations on /leaders/:leaderId end points.

<h2> Assignment 2: MongoDB </h2>

In this assignment, you will continue your journey with MongoDB and Mongoose. You will then create two new schemas for promotions and leadership, and then extend the Express REST API server to support the /promotions and the /leaders REST API end points.

Step-By-Step Assignment Instructions
less 
Assignment Overview

 At the end of this assignment you would have completed the following three tasks:

Implemented the Promotions schema and model
Implement a REST API to support the /promotions endpoint, and the /promotions/:promoId endpoint enabling the interaction with the MongoDB database
Implemented the Leaders schema and model
Implement a REST API to support the /leaders endpoint, and the /leaders/:leaderId endpoint enabling the interaction with the MongoDB database
Assignment Requirements

This assignment consists of the following two tasks:

Task 1

You are given the following example of a promotion document. You will now create the Promotions schema and model to support the document:

9
 {
      "name": "Weekend Grand Buffet",
      "image": "images/buffet.png",
      "label": "New",
      "price": "19.99",
      "description": "Featuring . . .",
      "featured": false
}

Note in particular that the label and price fields should be implemented the same way as you did for the Dishes schema and model. The Promotions schema and model should be defined in a file named promotions.js.

Next, extend the promoRouter.js to enable the interaction with the MongoDB database to fetch, insert, update and delete information.

Task 2

You are given the following example of a leadership document. You will now create the Leaders schema and model to support the document:

9
{
      "name": "Peter Pan",
      "image": "images/alberto.png",
      "designation": "Chief Epicurious Officer",
      "abbr": "CEO",
      "description": "Our CEO, Peter, . . .",
      "featured": false
}

The Leaders schema and model should be defined in a file named leaders.js.

Next, extend the leaderRouter.js to enable the interaction with the MongoDB database to fetch, insert, update and delete information.

Review criteria
less 
Upon completion of the assignment, your submission will be reviewed based on the following criteria:

Task 1

The Promotions schema and model correctly supports all the fields as per the example document given above
The label field is set to an empty string by default
The price schema is be supported with a new SchemaType called Currency.
The REST API endpoints /promotions and /promotions/:promoId are implemented to interact with the MongoDB database
Task 2

The Leaders schema and model correctly supports all the fields as per the example document given above.
The REST API endpoints /leaders and /leaders/:leaderId are implemented to interact with the MongoDB database

<h2>Peer-graded Assignment: User Authentication</h2>

In this assignment you will continue the exploration of user authentication. We have already set up the REST API server to validate an ordinary user. Now, you will extend this to verify an Admin and grant appropriate privileges to an Admin. In addition you will allow only a registered user to update and delete his/her submitted comments. Neither another user, nor an Admin can edit these comments.

Step-By-Step Assignment Instructions
less 
Assignment Overview

At the end of this assignment, you would have completed the following:

Check if a verified ordinary user also has Admin privileges.
Allow any one to perform GET operations
Allow only an Admin to perform POST, PUT and DELETE operations
Allow an Admin to be able to GET all the registered users' information from the database
Allow a registered user to submit comments (already completed), update a submitted comment and delete a submitted comment. The user should be restricted to perform such operations only on his/her own comments. No user or even the Admin can edit or delete the comments submitted by other users.
Assignment Requirements

This assignment is divided into three tasks as detailed below:

Task 1

In this task you will implement a new function named verifyAdmin() in authenticate.js file. This function will check an ordinary user to see if s/he has Admin privileges. In order to perform this check, note that all users have an additional field stored in their records named admin, that is a boolean flag, set to false by default. Furthermore, when the user's token is checked in verifyOrdinaryUser() function, it will load a new property named user to the request object. This will be available to you if the verifyAdmin() follows verifyUser() in the middleware order in Express. From this req object, you can obtain the admin flag of the user's information by using the following expression:

1
     req.user.admin
You can use this to decide if the user is an administrator. The verifyAdmin() function will call next(); if the user is an Admin, otherwise it will return next(err); If an ordinary user performs this operation, you should return an error by calling next(err) with the status of 403, and a message "You are not authorized to perform this operation!".

Note: See the video on how to set up an Admin account

Task2

In this task you will update all the routes in the REST API to ensure that only the Admins can perform POST, PUT and DELETE operations. Update the code for all the routers to support this. These operations should be supported for the following end points:

POST, PUT and DELETE operations on /dishes and /dishes/:dishId
DELETE operation on /dishes/:dishId/comments
POST, PUT and DELETE operations on /promotions and /promotions/:promoId
POST, PUT and DELETE operations on /leaders and /leaders/:leaderId
Task 3

In this task you will now activate the /users REST API end point. When an Admin sends a GET request to http://localhost:3000/users you will return the details of all the users. Ordinary users are forbidden from performing this operation.

Task 4

In this task you will allow a registered user to update or delete his/her own comment. Recall that the comment already stores the author's ID. When a user performs a PUT or DELETE operation on the /dishes/:dishId/comments/:commentId REST API end point, you will check to ensure that the user performing the operation is the same as the user that submitted the comment. You will allow the operation to be performed only if the user's ID matches the id of the comment's author. Note that the User's ID is available from the req.user property of the req object. Also ObjectIDs behave like Strings, and hence when comparing two ObjectIDs, you should use the Id1.equals(id2) syntax.

Review criteria
less 
Your assignment will be graded based on the following criteria:

Task 1

You have implemented the verifyAdmin() function in authenticate.js.
The verifyAdmin() function will allow you to proceed forward along the normal path of middleware execution if you are an Admin
The verifyAdmin() function will prevent you from proceeding further if you do not have Admin privileges, and will send an error message to you in the reply.
Task 2

Any one is restricted to perform only the GET operation on the resources/REST API end points.
An Admin (who must be first checked to make sure is an ordinary user), can perform the GET, PUT, POST and DELETE operations on any of the resources/ REST API end points.
Task 3

A GET operation on http://localhost:3000/users by an Admin will return the details of the registered users
An ordinary user (without Admin privileges) cannot perform the GET operation on http://localhost:3000/users.
Task 4

A registered user is allowed to update and delete his/her own comments.
Any user or an Admin cannot update or delete the comment posted by other users.

<h2>Peer-graded Assignment: Backend as a Service</h2>

In this assignment, you will be extending the router to support the ability to save and retrieve a list of favorite dishes by each of the registered users. All registered users in the system should have the ability to save any dish as their favorite dish, retrieve all their favorite dishes and remove one or all their favorite dishes.

Step-By-Step Assignment Instructions
less 
Assignment Overview

At the end of this assignment, your should have completed the following:

Allowed users to select a dish as their favorite, and add it to the list of favorites that are saved on the server.
Allowed users to retrieve the list of their favorite dishes from the server
Delete one or all of their favorite dishes from their favorites list on the server.
Assignment Resources

db.json
Assignment Requirements

In this assignment, you will be supporting a new route https://localhost:3443/favorites, where the users can do a GET to retrieve all their favorite dishes, a POST to add a list of dishes to their favorites, and a DELETE to delete the list of their favorites. In addition, you will support the new route  https://localhost:3443/favorites/:dishId where  the users can issue a POST request to add the dish to their list of favorite dishes, and a DELETE request to delete the specific dish from the list of their favorite dishes.

This assignment consists of the following three tasks:

Task 1

In this task you will be implementing a new Mongoose schema named favoriteSchema, and a model named Favorites in the file named favorite.js in the models folder. This schema should take advantage of the mongoose population support to populate the information about the user and the list of dishes when the user does a GET operation.

Task 2

In this task, you will implement the Express router() for the '/favorites' URI such that you support GET, POST and DELETE operations

When the user does a GET operation on '/favorites', you will populate the user information and the dishes information before returning the favorites to the user.
When the user does a POST operation on '/favorites' by including [{"_id":"dish ObjectId"}, . . .,  {"_id":"dish ObjectId"}] in the body of the message, you will (a) create a favorite document if such a document corresponding to this user does not already exist in the system, (b) add the dishes specified in the body of the message to the list of favorite dishes for the user, if the dishes do not already exists in the list of favorites.
When the user performs a DELETE operation on '/favorites', you will delete the list of favorites corresponding to the user, by deleting the favorite document corresponding to this user from the collection.
When the user performs a POST operation on '/favorites/:dishId', then you will add the specified dish to the list of the user's list of favorite dishes, if the dish is not already in the list of favorite dishes.
When the user performs a DELETE operation on '/favorites/:dishId', then you will remove the specified dish from the list of the user's list of favorite dishes.
Task 3

You will update app.js to support the new '/favorites' route.

Review criteria
less 
Your assignment will be graded on the basis of the following review criteria:

A new favoriteSchema and Favorites model has been correctly implemented to take advantage of Mongoose Population support to track the users and the list of favorite dishes using their ObjectIds in the favoriteSchema and Favorites model.
The GET, POST and DELETE operations are well supported as per the specifications above
The app.js has been updated to support the new route.
