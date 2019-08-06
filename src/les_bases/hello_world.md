# 1.1 - Hello world

```rust
 fn main() {
    println!("Bonjour tout le monde");
 }
```

## Déclarer des variables
```rust
# fn main() {
    let michel = "michel";
    println!("Bonjour {}", michel);
# }
```
## Shadowing
```rust
# fn main() {
    let x = 20;
    let x = x + 1;
    let x = x * 2; 
    println!("The value of x is {}", x);
# }
```

## Mutable vs Imutable
```rust
# fn main() {
    let the_answer = 42;
    the_answer += 1;
    println!("{}", the_answer);
# }
```

```rust
# fn main() {
    let mut the_answer = 42;
    the_answer += 1;
    println!("{}", the_answer);
# }
```
