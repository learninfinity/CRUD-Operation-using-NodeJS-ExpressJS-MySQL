
--------------------------------------------------------------------------
|             CRUD Operation using NodeJS / ExpressJS / MySQL            |
--------------------------------------------------------------------------

Step 1 : install nodejs in your system and run follwoing comment 
			npm init
		
Step 2 : Install Requred packages using NPM
			npm install --save express mysql body-parser ejs
			npm install -g nodemon (optional - used to run app.js automatically while any file content changes)
		
Step 3 : Add follwoing code in app.js
		
			const path = require('path');
			const express = require('express');
			const ejs = require('ejs');
			const bodyParser = require('body-parser');
			const mysql = require('mysql');
			const app = express();

			// Server Listening
			app.listen(3000, () => {
				console.log('Server is running at port 3000');
			});
			
			nodemon app (OR) npm start
		
Step 4 : Create Database Connection 
			const mysql=require('mysql');
			
			const connection=mysql.createConnection({
			  host:'localhost',
			  user:'root',
			  password:'',
			  database:'node_crud'
			});
			
			connection.connect(function(error){
			  if(!!error) console.log(error);
			  else console.log('Database Connected!');
			}); 

Setp 5 : Define view engin with ejs / public path / view files path / bodyParser
			//set views file
			app.set('views',path.join(__dirname,'views'));
			
			//set view engine
			app.set('view engine', 'ejs');
			app.use(bodyParser.json());
			app.use(bodyParser.urlencoded({ extended: false }));

Setp 6 : Define index path with '/' and HTML file
			
			//route for user index page
			app.get('/',(req, res) => {
				res.render('user_index', {
					title: 'CRUD Operation using NodeJS / ExpressJS / MySQL '
				});
			});

Setp 7 : Run a server and check with Browser
			npm start (OR) nodemon app

			http://localhost:3000/
			
Step 8 : Get value from database and show in HTML table using ExpressJS / MySQL