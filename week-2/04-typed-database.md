# Case Study: A small (typed) database

+ Let the database have 3 kinds of queries: `insert`, `delete`, `search`
+ The query is a function of type

```
database -> query -> status * database * contact
```

+ The status is `true` if the query went well

+ A phone number is a sequence of four integers

```
type phone_number = int * int * int * int
```

+ A contact has a name and phone number

```
type contact = {
  name         : string;
  phone_number : phone_number;
}
```

+ A database is a collection of contacts

```
type database = {
  number_of_contacts : int;
  contacts           : contact array;
}
```

+ Filler contact

```
let nobody = { 
  name = "";
  phone_number = (0, 0, 0, 0);
}
```

+ Database construction function

```
let make max_number_of_contacts = {
  number_of_contacts = 0;
  contacts = Array.make max_number_of_contacts nobody
}
```

+ Query is represented by a code and a contact: 
    + 0 = insert
    + 1 = delete
    + 2 = search for contact with the same name

```
type query = {
  code    :int;
  contact : contact;
}
```

```
let search db contact =
  let rec aux idx =
    if idx >= db.number_of_contacts then
      (false, db, nobody)
    else if db.contacts.(idx).name = contact.name then
      (true, db, db.contacts.(idx))
    else
      aux (idx + 1)
  in
  aux 0;
```

```
let insert db contact =
  if db.number_of_contacts >= Array.length db.contacts then
    (false, db, nobody)
  else 
    let (status, db, _) = search db contact in
    if status then (false, db, contact) else
      let cells i =
        if i = db.number_of_contacts then contact
        else db.contacts.(i)
      in
      let db' = {
        number_of_contacts = db.number_of_contacts + 1;
        contacts = Array.init (Array.length db.contacts) cells
      }
    in
    (true, db', contact)
```

```
let delete db contact =
  let (status, db, contact) = search db contact in
  if not status then (false, db, contact)
  else
    let cells i = 
      if db.contacts.(i).name = contact.name then nobody
      else db.contacts.(i) in
      let db' = {
        number_of_contacts = db.number_of_contacts - 1;
        contacts = Array.init (Array.length db.contacts) cells
      }
    in
    (true, db', contact)
```

```
let engine db (code, contact) =
  if code = 0 then insert db contact
  else if code = 1 then delete db contact
  else if code = 2 then search db contact
  else (false, db, nobody)
```

Purely functional database engine

+ A new database is created every time a query is processed
+ Previous versions of the database are still valid
+ Side effects are considered harmful
+ Functional programming encourages a style in which functions produce values instead of modifying memory
+ Evaluation of a function does not depend on the state of the program but only on its arguments
+ Since it does not depend on the state of the machine, functional programs are more composable than imperative ones

Weaknesses of this Implementation

+ Imprecise typing of query results
    + Search queries return a contact while insertion queries return a new database
    + The type of engine forces us to use a single type of query results
    + The type of engine should be the union of query results types
+ Inefficient duplication of databases
    + Each time a contact is inserted, the database is duplicated!
    + We should use a data structure that enables more sharing
