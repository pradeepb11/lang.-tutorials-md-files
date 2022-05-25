# How to Cache your Node.js application with Redis

# What is caching?
  Caching is the process of storing copies of files in a cache
  Temporary storage location so that they can be accessed more quickly.
  The goal of caching is speeding up data access operations better than a database or remote server could allow
# What is Redis?
  Redis is an open-source (BSD licensed), in-memory data structure store used as a database, cache, and message broker.
  You can think of it as a No-SQL database, which stores data as a key-value pair in the system memory. 
  If needed, Redis supports disk-persistent data storage too.
  
# Install Redis:
  npm init -y
  
  npm install redis --save
  npm install redis@3.1.2 --save
  ***Note: redis some working on redis @3.2.1. if latest not working then use @3.2.1***
  
  npm install node-fetch --save or 
  npm install axios --save
  ***Note:both node-fetch and axios are fetch url api fetch***
  
  npm install connect-redis --save
  npm install express-session --save
  
  ***Imp Note: Install Redis Server using acces***
 # redis-server install 
  sudo apt install redis-server
  
  # start With Using Redis 
  
  server.js file
  
  const express = require('express');
  
  const bodyParser = require('body-parser');
  
  const cors = require('cors');
  
  const redis = require('redis');
  
  const axios = require('axios');
  
  const app = express();
  
  app.use(cors());
  
  // request of content type application json
  app.use(bodyParser.json());
  
  // request of content  type aapplication/x-www-form-urlcoded
  app.use(bodyParser.urlencoded({ extended: true }))
  
  // make a connection to the local instance of redis
  const client = redis.createClient({
  host: '127.0.0.1',
  port: '6379'
  });
  
  client.on('error', function(err) {
    console.log('Could not establish a connection with redis. ' + err);
  });
  
  
  client.on('connect', function(err) {
    console.log('Connected to redis successfully');
  });
  
  
  app.get('/:searchtext', async(req, res) => {
    try {
        console.log('Fetching Data...');
        const searchtext = req.params.searchtext;
        // console.log(searchtext)
        
        // data from cache
        client.get(searchtext, async(err, data) => {
            if (data) {
                return res.status(200).send({
                    error: false,
                    message: `Data for ${searchtext} from the cache`,
                    data: JSON.parse(data)
                })
            } else {
                // data from Server
                const recipe = await axios.get(`https://jsonplaceholder.typicode.com/${searchtext}`);
                client.setex(searchtext, 60, JSON.stringify(recipe.data));
                return res.status(200).send({
                    error: false,
                    message: `Data for ${searchtext} from the server`,
                    data: recipe.data
                });
            }
        })

    } catch (error) {
        console.log(error)
    }
})


    // cors 
    app.use(function(req, res, next) {
      res.header("Access-Control-Allow-Origin", "*");
      res.header('Access-Control-Allow-Methods', 'POST, GET, PUT, DELETE, OPTIONS');
      res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
      res.header("Access-Control-Allow-Headers", "Content-Type");
      next();
    });


    const db = require('./app/model');


    const userRoute = require('./app/router/user.router');
    const roleRoute = require('./app/router/role.router');
    const merchantRoute = require('./app/router/merchant.router');



    // router 
    app.use('/api/v1/users', userRoute);

    // set port listing for request
    const PORT = process.env.APP_PORT || 3003;


    app.listen(PORT, () => {
      console.log(`server is running on port ${PORT}`);
    })
  
    
