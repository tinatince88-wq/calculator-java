**Metoda:** `Calculator.Run(String expression)`
**Scenario:** Provera složenog izraza sa prioritetom operacija `10+5*4+3`.
**Očekivano:** "33.0"
**Rezultat:** PROLAZ

| ID | Scenario | Unos | Očekivani rezultat | Stvarni rezultat | Status |
|:---|:---|:---|:---|:---|:---|
| 01 | Prioritet operacija | `10+5*4+3` | `33.0` | `33.0` | ✅ PROLAZ |
| 02 | Deljenje nulom | `10/0` | "ERROR" ili poruka | `Infinity` | ❌ PAD |
| 03 | Slova u izrazu | `10+abc` | "ERROR" | "ERROR" | ✅ PROLAZ |
| 04 | Prazan unos | (Samo Enter) | Poruka o grešci | StringIndexOutOfBounds | ❌ PAD |
| 05 | Višestruki operatori | `5++5` | "ERROR" | Crash/Neočekivano | ❌ PAD |

1. **Rukovanje izuzecima (Crash):** Program puca ako je prvi karakter prazan prostor ili ako se unese prazan string (greška u `expression.charAt(0)`).
2. **Logički propust (Deljenje nulom):** Program vraća `Infinity` umesto da detektuje deljenje nulom kao grešku.
3. **Validacija operatora:** Kalkulator ne proverava da li postoje dva operatora jedan do drugog (npr. `5++5`), što dovodi do pogrešnog mapiranja listi brojeva i operacija.
4. **Upotreba memorije:** `static` polje `finalResult` čuva prethodni rezultat, što može dovesti do problema ako metoda `Calculate` ne uspe da se završi pravilno.
