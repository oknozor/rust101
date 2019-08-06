# Introduction 

## Un peu d'histoire 

Graydon Hoare developpeur sur gcc, swiftc, clang, llvm, commence à travailler sur rust sur son temps libre en 2006. 
En 2009 Mozilla commence à participer au projet et révèle officiellement le language en 2010. En 2011 le compilateur auto-hébergé (précédement en OCaml) est compilé avec succès pour la première fois. La première version stable de Rust est publiée en 2015.

En 2016 les première ligne de Rust son ajoutées à la version 48 de Firefox.

En 2018 un bug vieux de plus de 15 ans est corrigé suite à l'introduction de Rust dans le moteur de Firefox, il aura fallu plus de 10 ans de développement pour en arriver là. 

## Rust pourquoi faire ? 

Le language se définit lui même sur son site officiel en mettant l'accent sur les points suivant :

- Performance : *"fast and memory efficient"* 
- Reliability : *"memory safety and thread safety"* 
- Productivity : *"great documentation, friendly compiler...etc"*

Si on traduit tout ça en bon français voilà ce que ça donne : 

- Des performances comparable à C
- Pas de bug au runtime (dangling pointer, wild pointer, memory leak...etc)
- Pas de situation de competition dans les contextes concurrent/multitache
- Un écosystème à l'état de l'art

## Quelques usage emblématiques

- Firefox 
- Libra 
- Npm 
- Webassambly
- Yelp 
- Sozu
- Xi 
- Redox

Et bientôt Microsoft :) 
