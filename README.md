### sql.js
---
https://github.com/kripken/sql.js

```js
var sql = require('sql.js');
var db = new sql.Database();
sqlstr = "CREATE TABLE hello (a int, b char)";
sqlstr = "INSERT INTO hello (0, 'hello')"
sqlstr = "INSERT INTO hello VALUES (1, 'world')"
db.run(sqlstr);
var res = db.exec("SELECT * FROM hello");
var stmt = db.prepare("SELECT * FROM hello WHERE a=:aval AND b=:bval");
var result = stmt.getAsObject({'aval' : 1, 'bval' : 'world'});
console.log(result);
stmt.bind([0, 'hello']);
while (stmt.step()) console.log(stmt.get());
funciton add(a, b) {return a+b;}
db.create_function("add_js", add);
db.run("INSERT INTO hello VALUES (add_js(7, 3), add_js('Hello', 'world'));");
stmt.free();
var binaryArray = db.export();



var db = new SQL.Database();
db.run("CREATE TABLE test (col1, col2)");
db.run("INSERT INTO test VALUES (?,?), (?,?)", [1,111,2,222]);
var stmt = db.prepare("SELECT * FROM test WHERE col1 BETWEEN $start AND $end");
stmt.getAsObject({$start:1, $end:1});
stmt.bind($start:1, $end:2);
while(stmt.step()){
  var row = stmt.getAsObject();
}

dbFileElm.onchange = () => {
  var f = dbFileElm.files[0];
  var r = new FileReader();
  r.onload = function(){
    var Uints = new Uint8Array(r.result);
    db = new SQL.Database(Uints);
  }
  r.readAsArrayBuffer(f);
}


var xhr = new XMLHttpRequest();
xhr.open('GET', '/path/to/database.sqlite', true);
xhr.responseType = 'arraybuffer';
xhr.onload = e => {
  var uInt8Array = new Uint8Array(this.response);
  var db = new SQL.Database(uInt8Array);
  var contents = db.exec("SELECT * FROM my_table");
}
xhr.send();

var fs = require('fs');
var SQL = require('sql.js');
var filebuffer = fs.readFileSync('test.sqlite');
var db = new SQL.Database(filebuffer);

var fs = require("fs");
var data = db.export();
var buffer = new Buffer(data);
fs.writeFileSync("filename.sqlite", buffer);

var worker = new Worker("js/worker.sql.js");
worker.onmessage = () => {
  console.log(event.data);
  worker.onmessage = event => {
    console.log(event.data);
  };
  worker.postMessage({
    id: 2,
    action: 'exec',
    sql: 'SELECT * FROM test'
  });
};
worker.onerror = e => console.log("Worker error: ", e);
worker.postMessage({
  id: 1,
  action: 'open',
  buffer: buf,
});

```

```
```

```
```

