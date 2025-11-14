# UPUTSTVO: KREIRANJE NOVOG C# PROJEKTA I OBJAVLJIVANJE NA GITHUB
Ovo uputstvo objašnjava kako da učenici naprave svoj novi C# projekat u Visual Studio-u i postave ga na GitHub bez grešaka.
1. Otvori Visual Studio
• Pokreni Visual Studio 2019 ili 2022.
• Klikni 'Create a new project'.
2. Izaberi tip projekta
• U pretrazi ukucaj 'Console App (.NET Framework)' ili 'Windows Forms App (.NET Framework)'.
• Klikni 'Next'.
3. Podesi naziv i lokaciju
• Project name: npr. DrugiProjekat
• Location: podrazumevana putanja (Documents\Visual Studio 2022\Projects)
• Proveri da je opcija 'Place solution and project in the same directory' ISKLJUČENA.
• Klikni 'Create'.
4. Napravi jednostavan kod
U fajlu Program.cs (ili Form1.cs) unesi sledeći kod:
using System;

namespace DrugiProjekat
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Ovo je moj drugi GitHub projekat!");
            Console.ReadKey();
        }
    }
}
5. Poveži projekat sa Git-om
• U meniju otvori View → Git Changes.
• U donjem levom uglu klikni Add to Source Control → Git.
(Visual Studio će sada napraviti lokalni Git repozitorijum.)
6. Objavi projekat na GitHub
1. U Git Changes panelu klikni 'Publish to GitHub'.
2. Uloguj se na svoj GitHub nalog.
3. U novom prozoru unesi:
   - Repository name: DrugiProjekat
   - Description: (opciono)
   - Visibility: Public
4. Klikni 'Publish'.
7. Proveri projekat na GitHub-u
• Otvori https://github.com
• Na svom profilu pronađi novi repozitorijum 'DrugiProjekat'.
• Otvori ga – trebalo bi da vidiš sve fajlove (.cs, .csproj, README.md...).
8. Ažuriranje projekta (Commit & Push)
Kada izmeniš kod u Visual Studio-u:
1. Otvori 'Git Changes'.
2. Upiši poruku u 'Message' polje (npr. 'Dodata nova funkcija').
3. Klikni 'Commit All', a zatim 'Push'.
Time će se sve promene poslati na GitHub.
1. Otvori 'Git Changes'.
2. Upiši poruku u 'Message' polje (npr. 'Dodata jos jedna funkcija').
3. Klikni 'Commit All', a zatim 'Push'.
4. Otvori View->Git Repository, a zatim klikni na 'Push'.
5. Otvori GitHub.

 

