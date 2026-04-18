## 1. Jedinični test (Unit Test)

```java
@Test
public void testCalculateMethod() {
    // Provera funkcionisanja metode Run koja poziva Calculate
    String expression = "10+5*4+3";
    String expected = "33.0";
    String actual = Calculator.Run(expression);
    
    Assert.assertEquals("Metoda ne obrađuje ispravno prioritet operacija.", expected, actual);
}

ID	Naziv testa	Unos	Očekivani rezultat	Stvarni rezultat	Status
01	Prioritet operacija	10+5*4+3	33.0	33.0	- PROLAZ
02	Deljenje nulom	10/0	Poruka o grešci	Infinity	- GREŠKA
03	Prazan unos	(Enter)	Poruka o grešci	Crash (Exception)	- GREŠKA
04	Nevalidni karakteri	10+abc	ERROR	ERROR	- PROLAZ
05	Dupli operatori	5++5	ERROR	Crash (IndexOutOfBounds)	- GREŠKA


Propusti u kodu
 Funkcionalne greške (Bugs)
Problem sa praznim stringom: Program ne proverava da li je unos prazan. Linija 29 expression.charAt(0) uzrokuje prekid rada programa (Crash) ako korisnik odmah pritisne Enter.
Loša obrada deljenja nulom: Program dozvoljava deljenje nulom i prikazuje rezultat Infinity. Ovo je propust u logici jer bi program trebalo da vrati "ERROR".
Greška kod višestrukih operatora: Ako korisnik unese dva operatora zaredom (npr. 5++5), program puca jer lista operacija postaje veća od liste brojeva.
 Arhitektonski nedostaci (Code Smell)
Statičke promenljive: Korišćenje static float finalResult može dovesti do preklapanja rezultata ako više korisnika koristi klasu istovremeno. Rezultat bi trebalo da bude lokalna promenljiva.
Nedostatak validacije: Program se previše oslanja na try-catch blok kod parsiranja, umesto da unapred proveri validnost celokupnog izraza pre nego što započne računanje.
Efikasnost (Start.java): Ponovno instanciranje klase Calculator unutar petlje bespotrebno zauzima memoriju pri svakom krugu rada.

