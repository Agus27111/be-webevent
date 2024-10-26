# Web Event Application

## Overview

Welcome to the Web Event Application! This project is part of a comprehensive course aimed at building a robust web application with various modern technologies and practices. Through this project, you'll learn about creating a scalable event management system using Express.js, MongoDB, and various other tools and libraries.

## Project Workflow

1. **Review Application Features** : Understand the application requirements and design the ERD (Entity-Relationship Diagram) and flow accordingly.
2. **Prepare Mock Data** : Set up initial mock data for testing and development purposes.
3. **Install the Project** : Initialize the project and install necessary dependencies.
4. **Structure the Folders** : Organize the project directory for maintainability and scalability.
5. **Database Connection** : Connect the application to a MongoDB database using Mongoose.

### Database Connection Example

Create a `config.js` file to bridge with the environment variables and set up the database connection in the `db` folder:

```
const mongoose = require('mongoose');
const { urlDb } = require('../config');main().catch(err => console.log(err));
async function main() {
  await mongoose.connect(urlDb);
}
const db = mongoose.connection;
module.exports = db;
```

6. **Modify bin/www File** : Update the `bin/www` file as we're using Express generator:

```
var app = require('../app');
var debug = require('debug')('server-semina:server');
var http = require('http');
const db = require('../app/db');var port = normalizePort(process.env.PORT || '3000');
app.set('port', port);var server = http.createServer(app);db.on('error', function(err) {
  console.log('connection error: cannot connect to MongoDB');
});db.on('open', function() {
  server.listen(port);
  server.on('error', onError);
  server.on('listening', onListening);
});function normalizePort(val) {
  var port = parseInt(val, 10);
  if (isNaN(port)) return val;
  if (port >= 0) return port;
  return false;
}function onError(error) {
  if (error.syscall !== 'listen') throw error;
  var bind = typeof port === 'string' ? 'Pipe ' + port : 'Port ' + port;
  switch (error.code) {
    case 'EACCES':
      console.error(bind + ' requires elevated privileges');
      process.exit(1);
      break;
    case 'EADDRINUSE':
      console.error(bind + ' is already in use');
      process.exit(1);
      break;
    default:
      throw error;
  }
}function onListening() {
  var addr = server.address();
  var bind = typeof addr === 'string' ? 'pipe ' + addr : 'port ' + addr.port;
  debug('Listening on ' + bind);
}
```

7. **Run the Application** : Start the application to ensure everything is set up correctly.

8. **Create CRUD for Categories** :

**Model** : Define the schema for categories.

**Controller** : Set up the logic for handling CRUD operations.

**Router** : Define the routes and integrate them into `app.js`

9. **Test with Postman** : Ensure all endpoints work correctly using Postman.

## Create CRUD for Each Table

1. **Hash Passwords with bcrypt** :

- Use bcrypt for password hashing during signup and comparison during login.
- Example usage in `participants` and `users` models.

1. **Use JWT for Authentication** :

- Set up JWT in `utils` and use it in `auth` and `participants` services.
- Implement JWT middleware for API security.

1. **File Uploads with multer** :

- Use multer for handling file uploads.
- Example usage in the `Image` model.

1. **Send OTP via Email with nodemailer** :

- Set up nodemailer in `services/mail`.
- Create a `views` folder for HTML email templates.

## Starting the Application

To get started with the application, follow these steps:

1. **Clone the repository** :

   ```
   git clone https://github.com/yourusername/web-event-app.git
   cd web-event-app
   ```

2. **Install dependencies** :

   `npm install`

3. **Run the application** :

   `npm run dev`

## Postman Documentation

For detailed API documentation and testing, refer to the [Postman Documentation](https://documenter.getpostman.com/view/27969319/2sAY4sjQPh).
