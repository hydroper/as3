# Package

The `Package` type kind represents a package as consisting of a name string (excluding dots), an optional parent package, a properties `Names` object, a collection of wildcard package exports (`export q.*;`), a collection of direct subpackages, a set of reserved namespaces (`public`, `internal`), and an optional ASDoc comment.

## Supported methods

### `is_package()`

Returns true.

### `name_string()`

The name string of the package. This is a single identifier; therefore it does not contain the dot character. For example, it returns `y` for a package `x.y`.

The package:

```as3
package x.y {}
```

Produces:

```rust
xy.name_string() == "y"
xy.to_string() == "x.y"
```

### `parent()`

The parent package of the package, or `None`.

### `properties()`

The properties of the package as a `Names` object.

### `wildcard_package_exports()`

A collection of wildcard package exports, as a vector of `Package` types. A wildcard package export is contributed from an `export` directive that exports a wildcard (`*`) item, such as in:

```as3
export q.*;
```

### `add_wildcard_package_export()`

Adds a wildcard package export. This method is used by the `export` directive.

### `subpackages()`

A collection of direct subpackages. For example:

```as3
package x {}
package x.y {}
package x.y.z {}
```

The `x` package has `x.y` as a direct subpackage.

### `asdoc()`

An optional ASDoc comment applying to the package.

### `set_asdoc()`

A setter for the `asdoc()` property.

### `get_or_create_package()`

Lookups a package given an array of name strings, or creates it if it does not exist, returning a `Package` type.

```rust
// Lookups a subpackage "x", then a subpackage "y" from the "x" package,
// and finally a "z" subpackage from the "x.y" package.
// If any of the segments does not exist as a subpackage, a new subpackage
// is created from the previous segment.
let xyz: Option<Package> = type_host.global_package().get_or_create_package(["x", "y", "z"]);
```

### `get_package()`

Lookups a package given an array of name strings.

```rust
// Lookups a subpackage "x", then a subpackage "y" from the "x" package,
// and finally a "z" subpackage from the "x.y" package.
let xyz: Option<Package> = type_host.global_package().get_package(["x", "y", "z"]);
```

### `get_packages_deep()`

Returns a vector containing the package and all of its subpackages recursively.

### `public_namespace()`

The `public` namespace of the package.

### `internal_namespace()`

The `internal` namespace of the package.

## Supported traits

### `ToString`

The `to_string()` method returns the fully-qualified name of the package using the dot delimiter.

The following package:

```as3
package x.y.z {}
```

Produces:

```rust
xyz.to_string() == "x.y.z"
xyz.name_string() == "z"
```