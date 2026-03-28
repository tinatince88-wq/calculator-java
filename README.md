**Ukupan LOC (Lines of Code):** 214

## Statička analiza koda (Izveštaj)


| Fajl | Broj linije koda | Zapažanje |
| :--- | :--- | :--- |
| Calculator.java | 19 | Metoda `calculate` je predugačka i sadrži previše ugnježdenih `if-else` naredbi (Code Smell: Long Method). |
| Calculator.java | 23 | Koristi se `Double.valueOf(expression)` bez provere da li je unos zaista broj (može izazvati `NumberFormatException`). |
| Calculator.java | 102 | Deljenje sa nulom nije eksplicitno obrađeno porukom za korisnika, već će vratiti `Infinity`. |
| Start.java | 11 | Promenljiva `calc` je instancirana unutar petlje, što je nepotrebno trošenje memorije. |
| Start.java | 18 | Program se oslanja na `Scanner.nextLine()` bez provere da li je unos prazan pre dalje obrade. |
