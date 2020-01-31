# Useful Commands for Realtime App Development

  

## MongoDB Commands:

  

**Repair MongoDB:**

  

    sudo rm /data/db/mongod.lock
    
    sudo mongod --dbpath /data/db --repair
    
    sudo mongod --dbpath /data/db

  

**Dump MongoDB from remote database:**

 - Dump complete remote database into local machine.

**Syntax:** `mongodump --uri "mongodb://USERNAME:PASSWORD@HOST:PORT/DATABASE_NAME?ssl=true" --out "directory path where the collections will be dumped"`


**Eg:** `mongodump --uri "mongodb://admin:admin@localhost:27017/EMPLOYEE?ssl=true" --out "/Users/Rajesh/data"`

 - Dump specific collection from remote database into local machine.
 
**Syntax:** `mongodump --uri "mongodb://USERNAME:PASSWORD@HOST:PORT/DATABASE_NAME?ssl=true" --collection COLLECTION_NAME --out "directory path where the collection will be dumped"`

**Eg:** `mongodump --uri "mongodb://admin:admin@localhost:27017/EMPLOYEE?ssl=true" -- collection employeeinfo --out "/Users/Rajesh/data"`
  

**Restore MongoDB data:**

Import all the json files into specified `DATABASE_NAME` in local machine.

  

**Syntax:** `mongorestore -d DATABASE_NAME <location where json files are saved>`

  

**Eg:** `mongorestore -d EMPLOYEE /Users/Rajesh/data`

  

**Import JSON file to MongoDB:**

**Syntax:** `mongoimport --db DATABASE_NAME --collection COLLECTION_NAME --file FILE.json`

(or)

  

    mongoimport --db DATABASE_NAME --collection COLLECTION_NAME --file FILE.json --jsonArray

  

  

**Eg:** `mongoimport --db EMPLOYEE --collection employeedata --file employeedata.json`

  

**Percent(%) Encoding :** MongoDB URI should be % encoded, if it contains special characters like %,@, etc.

https://www.url-encode-decode.com/

  

## Docker commands:

  

**Login to the running container:**

**Syntax:** `docker exec -it CONTAINER_ID /bin/bash`

**Eg:** `docker exec -it 10b79ff5e010 /bin/bash`

  

**Fix Docker Host issue in local machine:** `export DOCKER_HOST=unix:///var/run/docker.sock`

  

## Mac commands:

  

**List running processes on a particular port on Mac:**

  

**Syntax:** `lsof -i :PORT_NUMBER`

  

**Eg:** `lsof -i :8080`

  

**Kill a running process on a particular port on Mac:**

  

**Syntax:** `kill -9 PROCESS_ID`

  

**Eg:** `kill -9 8080`

  

**How to reset Mac default shell:**

`chsh -s /bin/bash`

  

http://osxdaily.com/2012/03/21/change-shell-mac-os-x/

  

## Spring Framework:

How to configure `application.yml` file to read the values from Environment variables?

    spring:
    	data:
    	    mongoDB:
    			uri: ${DATABASE_URI:mongodb://localhost:27017/EMPLOYEE}
