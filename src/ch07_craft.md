# Software Craft

Évoquer le [software craft](http://manifesto.softwarecraftsmanship.org/) ici n'est peut être pas complètement adapté mais il serait difficile de ne pas y référer tant Rust s'éforce d'encourager certaines pratiques qui gravitent autour du craft et des méthodes agiles: TDD, Documentation as code, Doc test, CI-CD ...etc.


## Écrire de la documentation

Une fois de plus, c'est la simplicité et l'efficacité qui prime. En rust pour commenter du code on utilise comme en C deus slash, pour documenter une librairie ou un programme on utilise markdown échappé par `///` en début de ligne. Voilà c'est tout, il n'y a presque rien d'autre à savoir.

La documentation du projet peut ensuite être générer avec `cargo doc` et consultée hors ligne avec `cargo doc --open`.


## TTD & Rust

Pour [écrire des tests en rust](https://doc.rust-lang.org/book/ch11-01-writing-tests.html), rien de plus simple, on utilise l'annotation `#[test]` :

```rust
#[cfg(test)]
mod tests {
    #[test]
    fn should_add_pastis() {
        assert_eq!(51 + 51, 102);
    }
}
```

Si vous avez l'habitude d'écrire des tests, vous allez rapidement remarquer qu'en Rust on écrit bien souvent les tests unitaires directement à côté du code fonctionnel. Cette pratique à l'avantage de documenter le code fonctionnel directement dans le même fichier. Lorsque le programe est compilé les tests sont compilé dans un exécutable séparé et ne viendrons pas polluer notre code de production.


## Benchmarks

En plus des tests rust permet via l'anotation `#bench` de tester les performance d'une section de code, on peut ainsi tracer facilement les régression/amélioration de performance dans une base de code.

## Doc test

En Rust il est possible d'écrire [des tests directement dans la documentation](https://doc.rust-lang.org/rust-by-example/testing/doc_testing.html).
Ces tests vont être exécuté à la compilation et  permettent de s'assurer que notre documentation est toujours à jours avec le code fonctionnel. Merveilleux non ?
