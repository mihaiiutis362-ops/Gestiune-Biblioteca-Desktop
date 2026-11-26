# Gestiune Bibliotecă Desktop

## Descrierea Proiectului
Aplicație desktop destinată evidenței fondului de carte și a împrumuturilor dintr-o bibliotecă. Interfața permite vizualizarea și filtrarea catalogului de cărți, înregistrarea titlurilor noi în sistem și gestionarea rapidă a operațiunilor de împrumut și retur.

## Prototip Interactiv (Figma)
* **Accesează prototipul interactiv:** [Deschide prototipul în Figma](https://www.figma.com/design/MBN47wHgSQuEzmFZk2rQ4Q/Gestionarea-unei-biblioteci?node-id=0-1&t=z1SPti1r6BCdDfnm-1)
* Capturile/exporturile ecranelor se regăsesc în directorul [`prototype/`](prototype/).

## Arhitectura Modulară
Aplicația este structurată pe 3 niveluri independente (detalii complete în [`docs/arhitectura-modulara.md`](docs/arhitectura-modulara.md)):

Folosește codul cu precauție.
+-------------------------------------------------------+
|          1. Nivelul de Prezentare (UI Layer)          |
|    - Catalog principal cărți (căutare & filtrare)     |
|    - Fereastră modală: Înregistrare carte nouă        |
|    - Fereastră modală: Înregistrare împrumut / retur  |
+-------------------------------------------------------+
|
v
+-------------------------------------------------------+
|      2. Nivelul Logicii Aplicației (Logic Layer)      |
|    - Validare date & reguli împrumut/disponibilitate  |
+-------------------------------------------------------+
|
v
+-------------------------------------------------------+
|         3. Nivelul de Date (Data Access Layer)        |
|    - Operații CRUD & persistența datelor              |
+-------------------------------------------------------+

## Diagrama UML (Use Case)
![Diagrama UML Use Case](diagrams/use-case.png)
