# 💻 Uputstvo za instalaciju Git for Windows i povezivanje sa Visual Studio-om
## 🎯 Cilj
Da učenici mogu da koriste Git i GitHub direktno iz Visual Studio-a, za čuvanje i deljenje projekata.
### 🧩 1️⃣ Provera da li je Git već instaliran
1. Otvorite Command Prompt (CMD) ili PowerShell
2. Ukucajte sledeću komandu i pritisnite Enter:
git --version
3. Ako dobijete odgovor kao: git version 2.46.0.windows.1 — Git je već instaliran.
4. Ako dobijete poruku: 'git' is not recognized as an internal or external command — Git nije instaliran.
###🧩 2️⃣ Instalacija Git for Windows
1. Otvorite link: https://git-scm.com/download/win
2. Preuzimanje će početi automatski – fajl će izgledati ovako: Git-2.xx.x-64-bit.exe
3. Pokrenite preuzeti fajl.
4. Na svim koracima birajte Next dok ne dođete do opcije 'Adjusting your PATH environment'.
5. Izaberite opciju: Git from the command line and also from 3rd-party software.
6. Nastavite sa Next dok ne završite instalaciju i kliknite Finish.
### 🧩 3️⃣ Proverite da li Visual Studio vidi Git
1. Otvorite Visual Studio
2. Izaberite Tools → Options → Source Control → Plug-in Selection
3. Izaberite opciju: Git
4. Kliknite OK
Ako vidite 'Add to Source Control' u donjem desnom uglu, sve radi ispravno.
### 🧩 4️⃣ Povezivanje Visual Studio-a sa GitHub nalogom
1. U Visual Studio-u otvorite View → Team Explorer
2. Kliknite na Manage Connections → Connect to GitHub
3. Ulogujte se sa vašim GitHub nalogom
4. Nakon prijave možete kreirati novi repo, klonirati postojeći i raditi commit/push/pull direktno iz VS-a.
### ✅ 5️⃣ Test – proverite da li sve radi
1. Napravite novi projekat u Visual Studio-u (npr. TestGitProjekt)
2. Kliknite 'Add to Source Control → Git'
3. U Team Explorer kliknite 'Publish to GitHub'
4. Kada se pojavi vaš GitHub nalog, kliknite Publish
5. Otvorite GitHub – videćete svoj novi repozitorijum! 🎉

