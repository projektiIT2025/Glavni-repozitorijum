# 🖥️ Projektni model za C# Windows Forms aplikaciju

## 🎯 Tema projekta

Napraviti **desktop aplikaciju u C# Windows Forms** koja koristi:

- 🧱 slojevitu arhitekturu  
- 🗄️ rad sa SQL bazom  
- ✔️ validaciju podataka  
- 📊 prikaz podataka u tabeli  
- 👤 korisničke uloge i dozvole  
- 🧩 jasnu podelu odgovornosti u projektu  

---

# 💡 Osnovna ideja

Kod većih Windows Forms aplikacija **nije dobro da sav kod bude u formi**.

Forma treba da služi samo za:

- unos podataka
- prikaz podataka
- reagovanje na klik dugmeta

Zbog toga aplikaciju delimo na **4 sloja**:

| Sloj | Opis |
|-----|-----|
| **Model** | klase sa podacima |
| **Repository** | rad sa SQL bazom |
| **Service** | poslovna logika i pravila |
| **UI (Forms)** | komunikacija sa korisnikom |

---

# 📦 Model – podaci

Model su klase koje predstavljaju podatke sistema.

Primer modela:

- `Korisnik`
- `Ucenik`
- `Predmet`
- `Ocena`

Model sadrži:

- svojstva
- konstruktore
- jednostavne metode vezane za objekat

⚠️ Model **ne sme**:

- da čita bazu
- da zna nešto o formama
- da prikazuje poruke korisniku

Model **predstavlja samo podatke**.

---

# 🗄️ Repository – rad sa SQL bazom

Repository je sloj koji komunicira sa bazom.

Njegov posao je:

- učitavanje podataka
- dodavanje podataka
- izmena podataka
- brisanje podataka

Ovde se pišu:

- SQL upiti
- konekcija ka bazi
- komande za rad sa bazom

Repository:

✔ zna kako da radi sa bazom  
❌ ne proverava poslovna pravila  
❌ ne zna ništa o formama  

---

# 🧠 Service – poslovna logika

Service je **najvažniji deo aplikacije**.

On je zadužen za:

- validaciju podataka
- proveru pravila sistema
- proveru dozvola korisnika
- dodavanje, izmenu i brisanje
- pretragu i sortiranje

Tok rada:Forma → Service → Repository → Baza

Service:

✔ proverava da li su podaci ispravni  
✔ proverava da li je akcija dozvoljena  

❌ ne koristi TextBox  
❌ ne koristi DataGridView  
❌ ne prikazuje UI kontrole  

👉 Service je **mozak aplikacije**.

---

# 🖼️ UI – Forme

Forma je deo koji **korisnik vidi**.

Njena uloga je:

- uzimanje unosa iz kontrola
- osnovna validacija formata
- pozivanje Service metoda
- prikaz podataka u tabeli
- prikaz poruka korisniku

Forma:

❌ ne radi direktno sa bazom  
❌ ne proverava poslovna pravila  
❌ ne proverava dozvole  

Forma služi za **unos i prikaz**.

---

# 🔄 Kako slojevi sarađuju

Tok rada aplikacije:

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

# ⚖️ Podela odgovornosti

## Forma proverava

- da li je broj pravilno unet
- da li unos može da se parsira
- osnovne greške u unosu

Primer:

```csharp
int.TryParse(txtId.Text, out int id);
double.TryParse(txtProsek.Text, out double prosek);



