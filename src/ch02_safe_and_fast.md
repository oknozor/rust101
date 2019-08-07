# Rapide et sûr
    
Au départ rust est un language de programmation système avec l'ambition de concurrencer C++, il a donc été créé avec les contraintes liées à ce domaine : Sécurité et rapidité. 

Mais qu'est ce qu'on veut dire quand ont parle de language *Memory safe* ? 

D'après wikipdia : 
> *Memory safety is the state of being protected from various software bugs and security vulnerabilities when dealing with memory access, such as buffer overflows and dangling pointers. For example, Java is said to be memory-safe because its runtime error detection checks array bounds and pointer dereferences.*

Les amateurs de C doivent certainement comprendre de quoi on parle ici. 
En C on peut faire a peu près ce qu'on veut, si on introduit un bug ce faisant on aura le droit à une jolie *SegFault* sans plus d'information, il ne nous reste plus que GDB pour nous en sortir, pire on ne verra peut être pas le bug tout de suite. 
C'est ce qui rend C aussi puissant mais également si difficile à maitriser.

En revanche en Java un certain nombre d'erreurs prédéfinies peuvent advenir au runtime et on aura bien souvent une idication précise sur l'origine du problème.

Rust est donc un language dit *Memory safe*, mais il pousse le concept un peu plus loin : l'énorme différence avec ce qu'on connaissait jusque là c'est que les erreurs de mémoires sont vérifiées à la compilation pas au runtime. Comme le dit un vieux proverbe rustaceen :  

> *"The safest program is the program that doesn't compile"*

Pour en arriver là Rust utilise deux concepts qui vous sont probablement étrangés : le *borrow checker*, et les l'*ownership*
