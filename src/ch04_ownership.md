# Borrow Cheking

## Les références 

On à vu précédement que les règles de propriété pouvaient être très contraignantes, prennons un exemple simple :

```rust
fn main() {
    let raffarinade = String::from("Je vous recommande la positive attitude.");
    let (s2, len) = calculate_string_len(raffarinade);

    println!("Cette raffarinade: \"{}\", contient {} caractères", s2, len);
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

    println!("Cette raffarinade: \"{}\", contient {} caractères", raffarinade, len);
}

fn calculate_string_len(s: &String) -> usize {
    s.len()
} 
```



## Lecteur/écrivains

En fait l'usage des références nous permet de manipuler une variable sans en acquérir la propriété. Mais que ce passe il si on veut modifier le contenue d'une référence ? 

```rust, does_not_compile, ignore
fn main() {
    let mut s = String::from("Jean");

    change(&mut s);
}

fn change(some_string: &String) {
    some_string.push_str("-Michel");
}
```

Pour manipuler le contenue de la référence il faut pouvoir le *déréférencer*, et pour cela il faut avoir la permission d'en acquérir la propriété. 

```
error[E0596]: cannot borrow `*some_string` as mutable, as it is behind a `&` reference
 --> src/main.rs:8:5
  |
7 | fn change(some_string: &String) {
  |                        ------- help: consider changing this to be a mutable reference: `&mut std::string::String`
8 |     some_string.push_str("-Michel");
  |     ^^^^^^^^^^^ `some_string` is a `&` reference, so the data it refers to cannot be borrowed as mutable
```

Si on suis les indications du compilateur voilà ce que ça donne :

```rust
fn main() {
    let mut s = String::from("Jean");

    change(&mut s);
    println!("{}", s);
}

fn change(some_string: &mut String) {
    some_string.push_str("-Michel");
}
```

Il nous reste une dernière règle à comprendre pour saisir l'entièreté du concept. Comme dans un contexte de programmation concurente, Rust nous force en permanence à appliquer la politique lecteur/écrivains : 

```rust, does_not_compile, ignore
let mut s = String::from("Damnit!");

let r1 = &mut s;
let r2 = &mut s;

println!("{}, {}", r1, r2);
```
```
   Compiling playground v0.0.1 (/playground)
error[E0499]: cannot borrow `s` as mutable more than once at a time
 --> src/main.rs:7:10
  |
6 | let r1 = &mut s;
  |          ------ first mutable borrow occurs here
7 | let r2 = &mut s;
  |          ^^^^^^ second mutable borrow occurs here
8 | 
9 | println!("{}, {}", r1, r2);
  |                    -- first borrow later used here
```

Comme pour les bases de données et la synchronisation de ressources dans un contexte de programmation concurrente Rust force l'utilisation du modèle lecteur/écrivaint. Il est donc possible d'avoir autant de référence immutable vers une valeur qu'on le souhaite mais une et une seule référence mutable.

## Validité 
``` rust, does_not_compile, ignore
fn main() {
    let reference_to_nothing = dangle();
}

fn dangle() -> &String {
    let s = String::from("hello");

    &s
}
```

Ici on voit bien que la variable `s` va être supprimée par le *borrow checker* après l'éxécution de `dangle()`. La référence `&s` n'est donc pas valide, ça ne compile pas.

```
error[E0106]: missing lifetime specifier
 --> src/main.rs:5:16
  |
5 | fn dangle() -> &String {
  |                ^ help: consider giving it a 'static lifetime: `&'static`
  |
  = help: this function's return type contains a borrowed value, but there is no value for it to be borrowed from
```

On ne va pas s'attarder sur le concept de de validité pour l'instant, sachez simplement qu'il est possible d'indiquer au compilateur de façon explicite la durée de validité d'une référence avec les *lifetime*.

## Résumé

Comme la propriété, l'emprunt est régi par des règle simples :

- À tout moment, il est possible d'avoir soit *une et une seule* référence mutable ou n'importe quel nombre de référence immutable.
- Une référence doit toujours être valide.
