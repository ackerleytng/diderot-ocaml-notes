# Tree-like Values

+ We can use a binary tree as a representation for databases

```
type database =
  | NoContact
  | DataNode of database * contact * database
```

+ Invariant: a database node DataNode (left, c, right) is well-formed if 
    + Every contact in left is lexicographically smaller than c
    + Every contact in right is lexicographically greater than c

+ Contact lookup

```
let search db name =
  let rec traverse = function
    | NoContact -> Error
    | DataNode (left, contact, right) ->
       if contact.name = name then
         FoundContact contact
       else if name < contact.name then
         traverse left
       else
let insert db contact =
  let rec traverse t = match t with
    | NoContact -> DataNode (NoContact, contact, NoContact)
    | DataNode (left, contact', right) ->
       if contact.name = contact'.name then
         t
       else if contact.name < contact'.name then
         DataNode (traverse left, contact', right)
       else
         DataNode (left, contact', traverse right)
```

+ This way of insertion causes subtrees to be shared between databases


