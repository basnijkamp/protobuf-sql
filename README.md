# sql-protobuf

Convert a SQL CREATE TABLE statement into a protobuf schema.

[![NPM](https://nodei.co/npm/sql-protobuf.png)](https://nodei.co/npm/sql-protobuf/)

Parsing SQL with regex has been called 'almost impossible' -- but I like to think we can cover over 90% of the cases. There might be bugs. If this has trouble with a functioning SQL CREATE TABLE statement, let's try to fix it.

```
$ npm install -g protobuf-sql
```

### CLI usage

```
$ protobuf-sql [input-file]
<...sql output...>
```

### Example

```
$ sql-protobuf schema.proto > schema.sql
```

schema.proto
```
syntax = "proto2";

message pluto {
  optional string boroughtext = 1;
  optional int32 block = 2;
  optional int64 lot = 3;
  required string cd = 4;
 }
```

schema.sql
```
CREATE TABLE "pluto" (
  "boroughtext" text,
  "block" integer,
  "lot" bigint,
  "cd" date NOT NULL,
);
```

### JS usage
```
var convert = require('protobuf-sql')
var file = fs.readFileSync('schema.proto').toString()
console.log(convert(file))
```
