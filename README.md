# xiaolintangyuan/node-informixdb 
## Fork Notice
This is a fork of [OpenInformix/node-informixdb](https://github.com/OpenInformix/node-informixdb).

I made a fork of this repository as I need to continue using informix drivers in my projects with "onsoctcp" protocol while updating them to the latest Node versions. The official ibm nodejs driver project [ibmdb/node-ibm_db](https://github.com/ibmdb/node-ibm_db) does not support the "onsoctcp" protocol and [I don't think they plan to ever support it](https://github.com/ibmdb/node-ibm_db/issues/506). Therefore it would only make sense for me to fork this repository and update it to support the latest node versions.

**If you use `drsoctcp` protocol, I strongly suggest that you use the official project instead.**

To use this library, you MUST have Informix CSDK installed and CSDK_HOME environment variables set as the library will build the node bindings during install. Otherwise, the library should behave exactly the same. I have done some housekeeping to remove unused dependencies.

No warranty or support provided. Please use this project as-is. Issues / PRs are not monitored and not entertained. Use at your own risk.

# Informix native node.js driver - node-informixdb:
Informix native node.js driver is a high performance driver with asynchronous/synchronous interface suitable for highly scalable enterprise applications and lightweight enough for Internet of things (IoT) solutions working with Informix database.

## Quick Example

```javascript
const informix = require('informixdb');

informix.open("SERVER=dbServerName;DATABASE=dbName;HOST=hostName;SERVICE=port;UID=userID;PWD=password;", function (err,conn) {
  if (err) return console.log(err);
  
  conn.query('select 1 from table(set{1})', function (err, data) {
    if (err) console.log(err);
    else console.log(data);

    conn.close(function () {
      console.log('done');
    });
  });
});
```

## How to get an informixdb instance?

The simple api is based on the instances of `Database` class. You may get an 
instance by one of the following ways:

```javascript
require("informixdb").open(connectionString, function (err, conn){
  //conn is already open now if err is falsy
});
```

or by using the helper function:

```javascript
const informix = require("informixdb")();
``` 

or by creating an instance with the constructor function:

```javascript
const Database = require("informixdb").Database
  , informix = new Database();
```

## Debug

If you would like to enable debugging messages to be displayed you can add the 
flag `DEBUG` to the defines section of the `binding.gyp` file and then execute 
`node-gyp rebuild`.

```javascript
<snip>
'defines' : [
  "DEBUG"
],
<snip>
```

## Un-Install

To uninstall informixdb from your system, just delete the node-informixdb or informixdb directory.


## For AIX install issue

If `npm install informixdb` aborts with "Out Of Memory" error on AIX, first run `ulimit -d unlimited` and then `npm install informixdb`.


## Need Help?

The development activities of the driver are powered by passion, dedication and independent thinking. You may send pull request, together we grow as an open community. Relevant discussion and queries are answered by community through Stack Overflow. 
http://stackoverflow.com/questions/tagged/informix
   
If no solution found, you can open a new issue on GitHub.


## Contributors

* xiaolintangyuan (this fork)
* Rohit Pandey (rht.uimworld@gmail.com)
* Anjali Pancholi
* Sathyanesh Krishnan (msatyan@gmail.com)
* Javier Sagrera
* Dan VerWeire (dverweire@gmail.com)
* Lee Smith (notwink@gmail.com)
* IBM

## Contributing to the xiaolintangyuan/node-informixdb

This fork does not support PR requests. However, you can always fork it if you want and do whatever you want with it.

## License
The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.