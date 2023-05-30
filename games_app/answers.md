Task
Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process. If you're not sure what's happening when - console.log all the things in all the places!

Questions
What is responsible for defining the routes of the games resource?
  In the helpers folder, the create_router.js file has all the routing code for express in it. There are http get requests, also post, put and delete requests, which connect to the database and interact with the collection parameter that is passed into the createRouter function at the top.

What do you notice about the folder structure? Whats the client responsible for? Whats the server responsible for?

  The client seems to be responsible for all the game's logic, like holding the states and the new game inputs from the form. Also responsible for rendering all the React components, the grid and the css for them all. There is an image in the assets folder which contains the delete icon for each GameCard.js.

  There is also a GamesService.js file which appears to fetch from the api (on port 9000) and post to it as well. So createGame in the GamesContainer, relates to the postGame(payload) in the GamesService. The postGame function is setting up a POST request with the request body that came from newGame in GamesContainer. It can seemingly json-ify this body information so that the api can accept it. Then is calls a for a response.
  GamesService can also get all the games info in the API and delete a specific id game from it too.

  The server is responsible for the database code, which holds the seed data and the create-router.js file, which creates the routes. These routes, inside the createRouter function, use the express code to talk to the database (MongoDB) by creating the routes that match the API routes.


What are the the responsibilities of server.js?

  Server.js actually sets up the database on MongoDB. It connects to MongoDB via an IP address, checks for errors then creates a database called games-hub. Then adds the collection of games which comes from the seeds.js file. Then uses the createRouter file to set up the routes for communication  back and forth, setting the route of "/api/games". Finally it listens on  port 9000 for any requests.


What are the responsibilities of the gamesRouter?
  ?? missed this one.


What process does the the client (front-end) use to communicate with the server?
  The front end client uses React inputs from the form to create new games. These inputs are are then transfered to the GameService file which translates them into http requests. If the newGame data is sent (via a Post request) then the GameService function postGame can translate the newgame into json too.


What optional second argument does the fetch method take? And what is it used for in this application? Hint: See Using Fetch on the MDN docs
  In GameService the fetch function can take in post or delete methods in the second argument. These can contain the information needed to either add a new game or delete one by it's id.


Which of the games API routes does the front-end application consume (i.e. make requests to)?
  baseURL = 'http://localhost:9000/api/games/' in GamesService.

What are we using the MongoDB Driver for?
  We use the driver to be able to talk to the javascript elements and also save our data via an API.
