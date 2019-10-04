# Ecosystème

Pour comprendre ce qui fait l'intérêt d'un language de programation, ses qualités techniques ne sont qu'une partie de l'équation. On peut penser à javascript qui dispose d'un écosystème fourni, de nombreux frameworks, une quantité plétorique de librairies et d'outils, plusieurs package managers, des extentions comme flow ou typescripts ...ect.

L'écosystème de Rust, si il manque encore de maturité, à pris une direction intéressante :

- [Une communauté ouverte](https://www.rust-lang.org/community)
- Un gestionnaire de paquet dédié
- Une génération de documentation simplifié

## Communauté

Rust à été créé dans les bureau de Mozilla, venant du monde de l'opensource, le parti pris est de ne pas s'appuyer sur sa communauté plus que sur les entreprises qui supportent le langage. Même si cela peut sembler annecdotique, cette vision est au coeur de Rust et il serait dommage de passer à côté.

Si vous êtes débutant en Rust, il est fortement recommander de jetter un oeil au [code de conduite de rust](https://www.rust-lang.org/policies/code-of-conduct) et d'aller faire un tour sur les différents média de la communauté : discord, gitter, forum, mailing-list ...etc. N'hésiter pas à y poser des questions, même si elle vous semble bêtes, les utilisateurs expérimentés du langage vous répondrons à coup sûr.

En plus de cet accueil chaleureux c'est sur les sites de la communauté que la volonté universaliste de Rust est la plus visible. Si, jusque ici vous pensez toujours que Rust est un langage destiné à la programation système, voici quelque ressources issues de la communauté pour vous convaincre du contraire:

- [Are we web yet?](https://www.arewewebyet.org/)
- [Are we game yet?](http://arewegameyet.com/)
- [Are we (I)DE yet?](https://areweideyet.com/)
- [Are we GUI yet?](https://areweguiyet.com/newsfeed/2019-01-13_rust2019.html)
- [Are we learning yet?](https://www.arewelearningyet.com/)
- [Are we async yet?](https://areweasyncyet.rs)
- [Are we audio yet?](https://areweaudioyet.com/)
- Un peu moins sérieux : [The Rust Evangelism Strike Force](https://www.reddit.com/r/rustjerk/)

Comme vous pouvez le constater la communauté des Rustacées est en marche pour conquérir tout les domaines de la programmation.  

## Package manager

Dans la plupart des autres écosystèmes les gestionnaires de paquets sont découplés du langage en lui même. On peut penser à l'antagonisme entre Maven et Graddle pour les javaiste, Npm et Yarn pour javascript.

Rust n'a (pour l'instant) qu'un seul gestionnaire de paquet et c'est un outil officiel : [Cargo](https://doc.rust-lang.org/cargo/).
Pour décrire les dépendances d'un projet, Cargo utilise [Toml](https://github.com/toml-lang/toml) : Tom's Obvious, Minimal Language.

Ce petit language simple et efficace permet de configurer un projet rapidement et il est peu probable que vous rencontrier jamais de [conflits de dépendance](https://stephencoakley.com/2019/04/24/how-rust-solved-dependency-hell).

Pour vous procurer ou uploader des librairies et consulter leur documentation (appellées crate en rust) rendez vous sur [crate.io](https://www.crates.io/) il est également possible d'utiliser un simple dépôt git comme source d'une dépendance. Depuis peut cargo permet d'utiliser des [registres privée](https://blog.cloudsmith.io/2019/05/01/worlds-first-private-cargo-registry/).


## Documentation

Quand on s'attèle à l'apprentissage d'un nouveau language, on se procure un ouvrage de référence, on consulte des articles de blog sur tel ou tel point que l'ont souhaite approfondir. Hé bien si vous avez décidez de vous y mettre, inutile de sortir votre portefeuille pour l'instant. Le site officiel du langage contient tout ce dont vous aurez besoin our vous y mettre.

Si vous ête amateur de théorie et que vous aimez aller au fond des choses [The Rust Programming Language](https://doc.rust-lang.org/book/index.html) est l'ouvrage de référence, si au contraire vous préférez apprendre en pratiquant [Rust by example](https://doc.rust-lang.org/stable/rust-by-example/) est fait pour vous. De manière général les ressources listées sur le [site officiel](https://www.rust-lang.org/learn) du langage sont de très bonne qualité