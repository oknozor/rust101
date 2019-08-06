# Rust, un language mutli-paradigme

Un des gros avantages du language et également un des point les plus déroutant pour les nouveaux arrivant est le caractère multi-paradigme de Rust. 

Mais qu'est ce qu'on veut dire par là au juste ? 

En fait Rust s'inspire des géants qui ont fait leurs preuves, de ce fait il offre une large pallette de style de programmation : 


## Programation Fonctionnelle

Rust permet de s'adonner au joies des monads et des closures ...etc

```rust
# fn main() {
let a = [1, 2, 3];

let double: Vec<i32> = a.iter()
    .map(|&x| x * 2)
    .collect();

println!("{:?}", double);
# }
```
## Pattern matching

Pour les développeurs qui connaissent Haskell, le concept sera relativement facile à aborder. Pour les autres c'est l'occasion de découvrir une des features les plus intéressante de Rust.

```rust
# fn main() {
    let michel = "Michel";

    match michel {
        "Michel"    => println!("Salut Michel"),
        "Georgette" => println!("Salut Georgette"),
        _           => panic!("Erreur prénom inconnu")
    }
# }
```

## Inférence de type

En rust les types sont statiques mais optionnel lorsque le compilateur parvient à les inférerers. 

```rust
# fn main() {
    let x = 42; 
    let y = x + 9;
    let message: &str = "bienvenue dans la zone";

    println!("{} {}", message, y);
# }
```

## Orienté objet 

Dans une certaine mesure Rust permet de faire de la POO, attention cependant les concepts sont totalement différent de ce dont vous avez probablement l'habitude avec Java. 
Impossible en rust de mélanger data et comportement, il n'y a donc pas d'héritage possible mais un système de trait (comparable au interface Java). 
Déroutant au premier abord on en découvre vite l'énorme potentiel.  

```rust 
# fn main() {
    #[derive(Debug, PartialEq)]
    struct TabletteChocolat {
        type_choco: TypeChoco, 
    }

    #[derive(Debug, PartialEq)]
    enum TypeChoco {
        Noir,
        Blanc,
        Lait,
    }

    impl TabletteChocolat {
        fn new(type_choco: TypeChoco) -> Self {
            TabletteChocolat {
                type_choco,
            }
        }
    }

    let choco_de_mamie = TabletteChocolat::new(TypeChoco::Noir);
    let choco_de_kevin = TabletteChocolat::new(TypeChoco::Lait);

    assert_eq!(choco_de_kevin, choco_de_kevin); 
# println!("Ok!");
# }
```
## Zero cost abstraction

Tout ce sucre syntaxique est absolument gratuit en terme de performance, c'est la toute la beauté de Rust: Une expression lambda et son équivalent en boucle procédurale seront optimisé de la même façon en bout de compilation. 

*exemple : https://lib.rs/crates/cargo-inspect* //TODO: exemple avec simple boucle for + closure 

Grâce au système de *lifetime* et au *borrow checker* sur lesquels on reviendra plus tard, Rust n'a pas besoin de GC.


