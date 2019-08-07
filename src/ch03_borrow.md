# Emprunt, propriété et durée de vie 

On commence doucement à entrer dans le vif du sujet. Les concept qu'on va évoquer ici sont propre à Rust et indubidablement difficile à appréhender.

Toute la force de Rust réside dans ces trois concept : 

- L'emprunt (*Borrow checking*)
- La propriété (*Ownership*)
- Les durée de vie (*Lifetimes*)

C'est grâce à eux que rust se passe de Ramasse miette sans pour autant nous contraindre à gérer les allocations mémoire de façon manuelle. 

## Ownership

La propriété est un concept simple à comprendre et pourtant difficile à maitriser en pratique. 
Commençons par énnoncer les trois règles qui régissent ce concept: 

- Toute valeur en Rust a une variable appelé sont possesseur (*owner*).
- Il ne peut y avoir qu'un seul possesseur à la fois pour une variable. 
- Quand le possesseur sort du contexte (*scope*), la valeur est éffacée.

### Heap vs. Stack, Copy vs. Clone

Par défaut les primitives sont stockées sur la pile (*stack*), elle sont peu couteuse en mémoire et donc copié automatiquement lorsque l'ont cré un nouveau binding. 

```rust 
# fn main() {
    let x = 51; 
    let y = x;

    println!("x: {}, y: {}", x, y);
# }
```

Au contraire les structures plus complexes comme `String` ici sont stockées dans le tas (*heap*).
Si on reprend les trois règles de la propriété vu plus haut on peut devienner se qui va se passer ici. 

```rust, does_not_compile, ignore
# #[allow(dead_code)]
# fn main() {
    let s1 = String::from("Arrrrrggh!");
    let s2 = s1; 

    println!("{}", s1);
# }
```

Ça ne compile pas, le compilateur nous apprend que la variable à été déplacé avant usage. 
En effet **une valeur ne peut avoir qu'un possesseur à la fois**, le binding de `s1` à été supprimer avant qu'on l'appelle avec la macro `println`. 

```
error[E0382]: borrow of moved value: `s1`
 --> pouet.rs:6:20
  |
3 |     let s1 = String::from("Arrrrrggh!");
  |         -- move occurs because `s1` has type `std::string::String`, which does not implement the `Copy` trait
4 |     let s2 = s1;
  |              -- value moved here
5 |
6 |     println!("{}", s1);
  |                    ^^ value borrowed here after move
```

Donc, contrairement au primitive, les structures stockées sur le tas ne sont pas copiées automatiquement, voilà comment on peut s'en sortir : 

```rust
# #[allow(dead_code)]
# fn main() {
    let s1 = String::from("Yeah!");
    let s2 = s1.clone(); 

    println!("{}", s1);
# }
```

Ici au lieu de déplacer la référence on fait une copie complète de `s1`, pas seulement de la référence vers les données stocké dans le tas, mais de l'entièreté de la variable. C'est une solution un peu radicale et heureusement il est possible de faire autrement. 