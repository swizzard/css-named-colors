# CSS Named Colors

Basically what it says on the tin. Conversion to/from names, hex codes, and rgb triples.  
No dependencies, no allocations, mostly `const`.

```rust
// parsing
let color = NamedColor::from_name("rebeccapurple").expect("invalid name");
// conversion
assert_eq!("#663399", &color.hex());
assert_eq!(Some((102, 51, 153)), &color.rgb());

// `transparent` is handled reasonably
assert_eq!("transparent", NamedColor::TRANSPARENT.hex());
assert!(NamedColor::TRANSPARENT.rgb().is_none());

// aliases/collisions are handled alphabetically
assert_eq!(NamedColor::AQUA.hex(), NamedColor::CYAN.hex());
assert_eq!(NamedColor::from_hex("#00ffff").unwrap(), NamedColor::AQUA); // _not_ CYAN
```
