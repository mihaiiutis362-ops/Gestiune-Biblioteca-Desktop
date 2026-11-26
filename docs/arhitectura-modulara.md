# Arhitectura Modulară a Aplicației „Gestiune Bibliotecă Desktop”

Aplicația desktop este structurată pe o arhitectură stratificată (**3-Tier / Layered Architecture**), care separă clar interfața grafică de logica de business și de gestionarea datelor. Această separare facilitează mentenanța, testarea și extinderea ulterioară a sistemului.

## Schema Arhitecturii Modulare




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
|    - Validare date introduse de utilizator            |
|    - Gestionare reguli împrumut / disponibilitate     |
|    - Filtrare și sortare dinamică a fondului de carte |
+-------------------------------------------------------+
|
v
+-------------------------------------------------------+
|         3. Nivelul de Date (Data Access Layer)        |
|    - Operații CRUD (Create, Read, Update, Delete)     |
|    - Persistența datelor (Bază de date / Fișiere)     |
+-------------------------------------------------------+

## Descrierea Modulelor

### 1. Modulul Interfeței Grafice (Presentation / UI Layer)
* **Responsabilitate:** Gestionează interacțiunea directă cu utilizatorul (bibliotecarul) și afișarea informațiilor.
* **Componente:**
  * *Ecranul Principal (Catalog):* Afișează lista cărților, bara de căutare și filtrele după categorie/disponibilitate.
  * *Modal Adăugare Carte:* Formular pentru introducerea titlului, autorului, ISBN-ului și numărului de exemplare.
  * *Modal Împrumut/Retur:* Interfață pentru asocierea unei cărți unui cititor sau marcarea returnării acesteia.

### 2. Modulul Logicii Aplicației (Business Logic Layer)
* **Responsabilitate:** Procesează cererile venite din interfață și aplică regulile de funcționare ale bibliotecii.
* **Funcționalități:**
  * Verifică dacă o carte mai are exemplare disponibile înainte de a permite un împrumut.
  * Validează completarea corectă a câmpurilor obligatorii la înregistrarea unei cărți noi.
  * Actualizează automat stocul de exemplare la fiecare operațiune de împrumut sau retur.

### 3. Modulul Stratului de Date (Data Access Layer)
* **Responsabilitate:** Asigură salvarea, actualizarea și extragerea permanentă a datelor.
* **Funcționalități:**
  * Execută operațiile de bază (**CRUD**) asupra entităților `Carte`, `Cititor` și `Împrumut`.
  * Izolează modul de stocare a datelor de restul aplicației, astfel încât modificarea bazei de date să nu afecteze interfața grafică.
