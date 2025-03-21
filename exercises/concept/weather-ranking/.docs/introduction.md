# Introduction

## Constants

Constants in Gleam are a way to give names to values. They are defined using the `const` keyword.

```gleam
pub const pi: Float = 3.14159

pub fn circle_area(radius: Float) -> Float {
  radius *. radius *. pi
}
```

When defined with the `pub` keyword module constants can be accessed from other modules, otherwise they can only be accessed from within the module they are defined in.

## Orders

The `gleam/order` module in Gleam's standard library contains the `Order` type, which is used to compare values.

The definition of `Order` looks like this:

```gleam
pub type Order {
  Gt
  Eq
  Lt
}
```

The type has three variants, each used to represent the relationship between value and another value:

- `Gt` - the value is _greater than_ the other value.
- `Eq` - the value is _equal_ to the other value.
- `Lt` - the value is _lower than_ the other value.

If a data type can be compared by size it is common for the module to define a `compare` function which returns an `Order` value. For example, `gleam/float` and `gleam/int` define `compare` functions that operate on floats and ints respectively.

```gleam
int.compare(1, 2)
// -> Lt

int.compare(2, 2)
// -> Eq

float.compare(1.0, 2.0)
// -> Lt
```

Sorting functions such as `list.sort` commonly take a function that returns an `Order` value, allowing the caller to define how the list should be sorted.

```gleam
list.sort([3, 7, 3, 1], by: int.compare)
// -> [1, 3, 3, 7]
```
