# BotBuilder-MongoDB
Bot builder with Mongo Db(custom storage )


Require Module 
  1)sudo npm install azure-storage
  2)sudo npm install mongodb --save
  
MongoDb connection Ip and Port Can modify in lib/connection.js

Mention collection name in (lib/IStorageClient.js) var conversational_collname ="collection name here"



I implemented IStorageClient(lib/IStorageClient.js) interface which internally use replaceDot(lib/replaceDot.js).

I am  replacing dot with @ in each key during insertion time,because Mongo Db doesn't support "." in key.

Same Code using to change @ to . After MongoDB document fetch.It will not effect to futionality


//Store session and context into mnongodb

var docDbClient = new istorage.IStorageClient();  //here is our logic to store data into mongo db  

var tableStorage = new azure.AzureBotStorage({ gzipData: false },docDbClient); //passing object to here

var bot = new builder.UniversalBot(connector).set('storage', tableStorage);//set your storage here



Reference Link:

https://github.com/Microsoft/BotBuilder/issues/1943
http://stackoverflow.com/questions/43153824/how-to-store-session-data-into-custom-storage-in-bot-builder
