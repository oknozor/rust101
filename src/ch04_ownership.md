

## Borrow Cheking

On à vu précédement que les règles de propriété pouvaient être très contraignantes, prennons un exemple simple :

```rust
fn main() {
    let raffarinade = String::from("Je vous recommande la positive attitude.");
    let (s2, len) = calculate_string_len(raffarinade);

    println!("Cette raffarinade: \"{}\", contient {} caractèress", s2, len);
}

fn calculate_string_len(s: String) -> (String, usize) {
    let len = s.len();
    (s.clone(), len)
} 
```

Pour effectuer une opération aussi simple que retourner la longueur d'une chaine de caractères on est obligé de retourner un tuple avec une copie de la chaine.
Heureusement on peut s'affranchir de tout ces salamalèques avec les références : 

```rust
fn main() {
    let raffarinade = String::from("La faiblesse de vocabulaire signifie la faiblesse de penser.");
    let len = calculate_string_len(&raffarinade);

    println!("Cette raffarinade: \"{}\", contient {} caractèress", raffarinade, len);
}

fn calculate_string_len(s: &String) -> usize {
    s.len()
} 
```

Comme la propriété, l'emprunt est régi par des règle simple :

- À tout moment, il est possible d'avoir soit *une et une seule* référence mutable ou n'importe quel nombre de référence immutable.
- Une référence doit toujours être valide. 