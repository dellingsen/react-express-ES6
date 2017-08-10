#How to create a React and/or Express.js app and run together

## React Setup

https://github.com/facebookincubator/create-react-app#getting-started
npm install -g create-react-app
create-react-app my-app
cd my-app

npm start (Uses react-scripts start to start local dev React web container)
http://localhost:3000

npm run build
Builds the app for production to the build folder.
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.
By default, it also includes a service worker so that your app loads from local cache on future visits.
The build folder is ready to be deployed.
You may serve it with a static server:
npm install -g serve
serve -s build

Alternatively, will can also copy the contents of the build folder to the root
public directory in the node project to have Node serve the minified React content (next step).

## Express setup

https://expressjs.com/en/starter/generator.html
npm install -g express-generator
express --view=jade my-app
cd my-app

npm install
npm start

When we created our Express app we gave it the 'jade' default view engine which just means that
our Express server will serve up the .jade pages in the 'views' directory and will set the view
engine in the Express server (app.js) like this:

app.set('views', path.join(__dirname, 'views'));

app.set('view engine', 'jade');


For our purposes (not using jade), we will remove those 2 lines from the app.js server, 
and add a default index.html file to the 'public' directory so we can treat the 'public' 
directory as the source of our client code that the Express server will serve up.

This line in our app.js file makes that connection (to serve files from the public directory):
app.use(express.static(path.join(__dirname, 'public')));


Now, as mentioned above, we can take the contents of our built/minified react app (inside the build directory)
and copy them to the public folder, and boom, Express is now serving up your React application.





