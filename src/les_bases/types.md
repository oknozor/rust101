# 1.1 - Système de type

## Statiquement typé

```rust 
let guess: u32 = "42".parse().expect("Not a number!");
```

## Implicite
```rust
# fn main() {
    let x = 1; 
    let y = "hello"; 
    let y = vec!["hello", "world"];
# }
```

## Explicite

```rust
# fn main() {
    let x: i32 = 1; 
    let y: &str = "hello"; 
    let y: Vec<&str> = vec!["hello", "world"];
# }
```

## Type composite 

### Tuple

```rust
# fn main() {
    let tup: (i32, &str) = (32, "carottes"); 
    println!("vous avez {}, {}", tup.0, tup.1);
# }
```

```rust
# fn main() {
    let tup: (i32, &str, f32) = (32, "carottes", 1.6);
    let (nb, genre, poids) = tup; 
    println!("vous avez {}, {} pour un total de {}kg", nb, genre, poids);
# }
```

