# 🧠 UPUTSTVO: Moj prvi C# projekat na GitHub-u
## 🎯 Cilj:
Naučiti kako da napraviš novi projekat u Visual Studio-u i postaviš ga na svoj GitHub nalog.
### 🧩 1. Priprema
#### ✅ Potrebno je da imaš:
- GitHub nalog (već napravljen)
- Instaliran Visual Studio 2019 ili 2022
- Instaliran dodatak Git for Windows (automatski ide uz VS)
### 🚀 2. Napravi novi C# projekat

1. Pokreni Visual Studio  
2. Izaberi Create a new project  
3. Odaberi šablon: Console App (.NET Framework) ili Windows Forms App (.NET Framework)  
4. Klikni Next  
5. Upiši ime projekta (npr. MojPrviProjekat)  
6. Izaberi folder gde će biti sačuvan  
7. Klikni Create

### 🌳 3. Dodaj projekat pod Git kontrolu

1. Otvori meni View → Git Changes  
2. Klikni na dugme Add to Source Control → Git  
3. Sada Visual Studio pravi Git repozitorijum u tvom projektu (lokalno).

### 🔗 4. Poveži Visual Studio sa svojim GitHub nalogom

1. U Git Changes prozoru klikni na Publish to GitHub  
2. Ako ti traži prijavljivanje, uloguj se na svoj GitHub nalog (tvoj, ne organizacioni).  
3. Kada se otvori dijalog:
   - Repository name: (npr. MojPrviCSharpProjekat)
   - Opis: (npr. "Moj prvi Visual Studio projekat na GitHub-u")
   - Visibility: Public  
4. Klikni Publish  

⚠️ Važno: Visual Studio automatski koristi granu main, zato ne pravi dodatne grane kao “master”. Samo koristi main i ništa ne menjaš ručno.

### ☁️ 5. Proveri da je projekat otišao na GitHub

1. Otvori svoj GitHub profil (npr. https://github.com/tvojeime)  
2. Videćeš novi repozitorijum (npr. MojPrviCSharpProjekat)  
3. Klikni na njega i proveri da su svi tvoji fajlovi tu:
   - Program.cs  
   - .sln fajl  
   - .csproj  
   - Properties, bin, obj, itd.

### 🔄 6. Kako da pošalješ izmene (commit i push)

Kad god nešto izmeniš u projektu:

1. Otvori View → Git Changes  
2. Upiši poruku (npr. “Dodat pozdrav u programu”)  
3. Klikni Commit All  
4. Klikni Push (strelica nagore)

### 🎁 7. Proveri svoj kod na GitHub-u

1. Otvori svoj repozitorijum ponovo  
2. Klikni na Code  
3. Pogledaj da li su fajlovi ažurirani – ako jesu, sve je uspešno urađeno ✅

#### 💡 Kratak rezime

| Korak | Akcija | Lokacija |
|-------|--------|-----------|
| 1 | Kreiraj novi projekat | Visual Studio |
| 2 | Add to Source Control → Git | Visual Studio |
| 3 | Publish to GitHub | Visual Studio |
| 4 | Proveri repozitorijum | GitHub sajt |
| 5 | Commit + Push svake promene | Visual Studio |

#### ⚠️ Najčešće greške koje treba izbeći

❌ Ne biraj ručno “master” granu — koristi main (Visual Studio to sam uradi).  
❌ Ne pokušavaj da praviš repozitorijum na GitHub-u pre nego što klikneš Publish iz VS.  
✅ Sve počinje iz Visual Studio-a.  
✅ Tek kada se projekat objavi, možeš dalje da menjaš fajlove i šalješ izmene.


