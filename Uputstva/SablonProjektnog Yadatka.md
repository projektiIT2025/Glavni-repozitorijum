PROJEKTNI MODEL ZA C# WINDOWS FORMS APLIKACIJU
Tema projekta
Napraviti desktop aplikaciju u C# Windows Forms koja koristi:
•	slojevitu arhitekturu
•	rad sa SQL bazom
•	validaciju podataka
•	prikaz podataka u tabeli
•	korisničke uloge i dozvole
•	jasnu podelu odgovornosti u projektu
________________________________________
1. OSNOVNA IDEJA
Kada pravimo veći projekat u Windows Forms aplikaciji, nije dobro da sve pišemo u formi.
Forma treba da služi samo za:
•	unos podataka
•	prikaz podataka
•	reagovanje na klik dugmeta
Zato projekat delimo na 4 dela:
1.	Model – klase sa podacima
2.	Repository – rad sa SQL bazom
3.	Service – pravila i poslovna logika
4.	UI (Forme) – komunikacija sa korisnikom
________________________________________
2. MODEL – PODACI
Model su klase koje predstavljaju podatke sistema.
Na primer:
•	Korisnik
•	Ucenik
•	Predmet
•	Ocena
Model sadrži:
•	svojstva
•	konstruktore
•	eventualno jednostavne metode vezane za sam objekat
Model:
•	ne sme da čita bazu
•	ne sme da zna ništa o formi
•	ne sme da prikazuje poruke korisniku
Model samo predstavlja podatke.
________________________________________
3. REPOSITORY – RAD SA SQL BAZOM
Repository služi za komunikaciju sa bazom.
Njegov posao je:
•	učitavanje podataka iz baze
•	dodavanje podataka u bazu
•	izmena podataka u bazi
•	brisanje podataka iz baze
U ovom sloju pišu se:
•	SQL upiti
•	konekcija ka bazi
•	komande za rad sa bazom
Repository:
•	zna kako da radi sa bazom
•	ne proverava poslovna pravila
•	ne zna ništa o formama
Sav rad sa bazom ide ovde.
________________________________________
4. SERVICE – POSLOVNA LOGIKA
Service je najvažniji deo aplikacije.
On služi za:
•	validaciju podataka
•	proveru pravila sistema
•	proveru dozvola korisnika
•	dodavanje, izmenu i brisanje
•	pretragu i sortiranje
Forma poziva Service, a Service koristi Repository.
Service:
•	proverava da li su podaci ispravni
•	proverava da li je akcija dozvoljena
•	odlučuje da li nešto može da se izvrši
Service:
•	ne čita podatke direktno iz TextBox-a
•	ne prikazuje kontrole forme
•	ne sme da sadrži kod za DataGridView
Service je mozak aplikacije.
________________________________________
5. UI – FORME
Forma je deo koji korisnik vidi.
Njena uloga je da:
•	uzme unos iz kontrola
•	proveri osnovni format unosa
•	pozove odgovarajuću metodu iz Service sloja
•	prikaže podatke u tabeli
•	prikaže poruku korisniku
Forma:
•	ne radi direktno sa bazom
•	ne proverava poslovna pravila
•	ne odlučuje o dozvolama korisnika
Forma služi za unos i prikaz.
________________________________________
6. KAKO SLOJEVI SARADJUJU
Tok rada u aplikaciji treba da izgleda ovako:
Korisnik klikne dugme
↓
Forma pročita unos
↓
Forma proveri osnovni format
↓
Forma pozove Service
↓
Service proveri pravila i dozvole
↓
Service pozove Repository
↓
Repository izvrši rad sa bazom
↓
Forma osveži prikaz podataka
To je pravilan tok rada.
________________________________________
7. PODELA ODGOVORNOSTI
Forma proverava:
•	da li je broj pravilno unet
•	da li unos može da se parsira
•	osnovne greške u unosu pre slanja u Service
Na primer:
•	int.TryParse(...)
•	double.TryParse(...)
Service proverava:
•	da li je unos logički ispravan
•	da li su sva obavezna polja popunjena
•	da li je vrednost u dozvoljenom opsegu
•	da li podatak već postoji u bazi
•	da li korisnik ima pravo da izvrši akciju
________________________________________
8. PRIMER PROVERE KOD DODAVANJA
Ako forma dodaje učenika:
Forma proverava:
•	da li je Id broj
•	da li je Prosek broj
Service proverava:
•	da li je ime prazno
•	da li je prosek između 1 i 5
•	da li učenik sa tim ID već postoji u bazi
Znači:
Provera	Gde ide
da li je ID broj	Forma
da li je prosek broj	Forma
da li je ime prazno	Service
da li je prosek u opsegu	Service
da li podatak već postoji u bazi	Service
________________________________________
9. ULOGE KORISNIKA I DOZVOLE
Aplikacija može imati korisnike sa različitim ulogama, na primer:
•	Gost
•	Korisnik
•	Administrator
Svaka uloga ima određene dozvole.
Primer:
Akcija	Gost	Korisnik	Administrator
Pregled	Da	Da	Da
Dodavanje	Ne	Da	Da
Izmena	Ne	Da	Da
Brisanje	Ne	Ne	Da
Izveštaj	Ne	Da	Da
Važno pravilo:
Forma ne proverava ko je korisnik.
Service proverava dozvole.
Dakle, nije dobro:
if (uloga == "Administrator")
{
    // obrisi
}
Bolje je:
service.Obrisi(id, korisnik);
A Service odlučuje da li to sme.
________________________________________
10. MODEL KORISNIKA I DOZVOLA
U projektu se koristi sledeći OOP model:
•	Dozvola → enum sa svim akcijama sistema
•	IDozvola → interfejs za proveru dozvole
•	Korisnik → apstraktna klasa
•	Gost, KorisnikSistema, Administrator → izvedene klase
Na taj način učenici primenjuju:
•	apstraktnu klasu
•	nasleđivanje
•	interfejs
•	enum
•	polimorfizam
________________________________________
11. ŠTA TREBA ZAPAMTITI
Model
Predstavlja podatke.
Repository
Radi sa SQL bazom.
Service
Proverava pravila i dozvole.
Forma
Uzima unos i prikazuje podatke.
________________________________________
12. NAJVAŽNIJE PRAVILO
Forma proverava format, Service proverava pravila, Repository radi sa bazom, Model predstavlja podatke.
________________________________________
13. CILJ PROJEKTA
Kroz ovaj projekat učenici treba da nauče:
•	kako se pravi uredna Windows Forms aplikacija
•	kako da forma ne bude pretrpana kodom
•	kako da razdvoje unos, logiku i rad sa bazom
•	kako izgleda struktura ozbiljnijeg softverskog projekta
•	kako se koriste apstraktne klase, interfejsi i nasleđivanje u praksi
________________________________________
14. PREDLOG FOLDERA U PROJEKTU
SkolskaEvidencija
│
├── Models
│   ├── Korisnik.cs
│   ├── Gost.cs
│   ├── KorisnikSistema.cs
│   ├── Administrator.cs
│   ├── IDozvola.cs
│   ├── Dozvola.cs
│   └── Ucenik.cs
│
├── Repositories
│   ├── IRepository.cs
│   └── UcenikSqlRepository.cs
│
├── Services
│   ├── UcenikService.cs
│   └── AuthService.cs
│
├── Helpers
│   └── DbSettings.cs
│
├── Forms
│   ├── LoginForm.cs
│   ├── LoginForm.Designer.cs
│   ├── MainForm.cs
│   └── MainForm.Designer.cs
│
├── Program.cs
└── App.config
________________________________________
15. OBJAŠNJENJE FOLDERA
Models
Klase koje predstavljaju podatke i OOP model.
Repositories
Klase koje rade sa SQL bazom.
Services
Klase koje sadrže poslovnu logiku i proveru dozvola.
Helpers
Pomoćne klase, na primer za konekcioni string.
Forms
Sve forme aplikacije.
________________________________________
16. JEDNOSTAVNA VERZIJA ZA PAMĆENJE
•	Model = podaci
•	Repository = baza
•	Service = pravila
•	Forma = unos i prikaz
I još:
•	TryParse ide u formu
•	provera duplikata i pravila ide u Service



