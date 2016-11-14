# Mutable Record Fields

Selected field records can be declared as `mutable`

```
type some_type_identifier =
  { field_name_1: some_type_1;
    ...;
    mutable field_name_i: some_type_i;
    ...;
    field_name_n: some_type_n
  }
```

Use the `<-` to modify the fields
