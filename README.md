# Glavni-repozitorijum

Projekti iz programiranja BLOK praksa 2025 odeljenje IT42
Dobrodošli na GitHub organizaciju za projektnu nastavu!
Ovde ćete raditi projekte, učiti kako se koristi GitHub i predavati radove.
# 🧠 Projektni model za C# Windows Forms aplikaciju

## 🎯 Tema projekta

Napraviti **desktop aplikaciju u C# Windows Forms** koja koristi:

- slojevitu arhitekturu  
- rad sa **SQL bazom podataka**  
- **validaciju podataka**  
- prikaz podataka u tabeli (`DataGridView`)  
- **korisničke uloge i dozvole**  
- jasnu **podelu odgovornosti u projektu**

---

# 🏗️ Osnovna ideja

Kod većih aplikacija **nije dobro da se sva logika nalazi u formi**.

Forma treba da služi samo za:

- unos podataka
- prikaz podataka
- reagovanje na klik dugmeta

Zato projekat delimo na **4 sloja**:

| Sloj | Opis |
|-----|-----|
| **Model** | klase koje predstavljaju podatke |
| **Repository** | komunikacija sa bazom |
| **Service** | poslovna logika |
| **UI (Forms)** | komunikacija sa korisnikom |

---

# 📦 1. Model – Podaci

Model su klase koje predstavljaju **podatke sistema**.

Primeri:

- `Korisnik`
- `Ucenik`
- `Predmet`
- `Ocena`

Model sadrži:

- svojstva
- konstruktore
- eventualno jednostavne metode

### ⚠️ Važna pravila

Model:

- ❌ ne sme da čita bazu
- ❌ ne sme da zna ništa o formama
- ❌ ne sme da prikazuje poruke korisniku

✔ Model samo predstavlja **podatke**.

---

# 🗄️ 2. Repository – Rad sa SQL bazom

Repository služi za **komunikaciju sa bazom podataka**.

Njegov posao je:

- učitavanje podataka
- dodavanje podataka
- izmena podataka
- brisanje podataka

U ovom sloju se nalaze:

- SQL upiti
- konekcija ka bazi
- komande za rad sa bazom

### Primer

### Pravila

Repository:

✔ zna kako da radi sa bazom  
❌ ne proverava poslovna pravila  
❌ ne zna ništa o formama

---

# ⚙️ 3. Service – Poslovna logika

Service je **najvažniji deo aplikacije**.

On služi za:

- validaciju podataka
- proveru pravila sistema
- proveru dozvola korisnika
- dodavanje, izmenu i brisanje
- pretragu i sortiranje

### Tok rada

Service:

✔ proverava da li su podaci ispravni  
✔ proverava dozvole  
✔ odlučuje da li akcija može da se izvrši  

### Service ne sme:

- ❌ da čita podatke iz `TextBox`
- ❌ da koristi `DataGridView`
- ❌ da pristupa kontrolama forme

Service je **mozak aplikacije**.

---

# 🖥️ 4. UI – Forme

Forma je deo aplikacije koji **korisnik vidi**.

Njena uloga:

- uzima unos iz kontrola
- proverava osnovni format
- poziva Service
- prikazuje podatke u tabeli
- prikazuje poruke korisniku

Forma:

❌ ne radi direktno sa bazom  
❌ ne proverava poslovna pravila  
❌ ne odlučuje o dozvolama  

Forma služi samo za **unos i prikaz**.

---

# 🔄 Kako slojevi sarađuju

Pravilan tok rada u aplikaciji:

---

# 🧩 Podela odgovornosti

| Provera | Gde ide |
|------|------|
| da li je broj pravilno unet | Forma |
| da li unos može da se parsira | Forma |
| da li je ime prazno | Service |
| da li je vrednost u opsegu | Service |
| da li podatak već postoji u bazi | Service |

Primer:

```csharp
int.TryParse(txtId.Text, out int id);
