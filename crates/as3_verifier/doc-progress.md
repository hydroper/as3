Type kinds:

- [x] Name
- [x] Package
- [ ] Namespace
- [ ] Namespace set
- [ ] Any type
- [ ] Undefined type
- [ ] Void type (equivalent to undefined type, but literally spelled differentt)
- [ ] Never type
- [ ] Class type
- [ ] Interface type
- [ ] Enum type
- [ ] Function type
- [ ] Union type
- [ ] Complement type
- [ ] Tuple type
- [ ] Record type
- [ ] Nullable type
- [ ] Non-nullable type
- [ ] Type with arguments
- [ ] String literal type 
- [ ] Number literal type
- [ ] Variable property
  - [ ] Read only
- [ ] Virtual property
- [ ] Function property
- [ ] Alias
  - [ ] The `Alias` type kind represents an alias to a type or property.
- [ ] Frame
  - [ ] The `Frame` type kind represents a lexical scope. A `Frame` contains an optional reference to a parent frame, a collection of wildcard package imports, recursive package imports and a `Names` object.
- [ ] Value
  - [ ] The `Value` type kind represents a value with a static type and various variations.
- [ ] Delegate

Names:

- [ ] The `Names` object represents a mapping from `Name` kind to `Type` and a collection of wildcard package exports.

Miscellaneous:

- [ ] `SimpleTypedName` (`a: T` as used in a function type)