# Git Guide – CMD og GitHub Desktop

En enkel guide til hvordan man bruger **Git og GitHub** på en arbejdsplads.

Guiden viser det samme normale workflow på to måder:

- **CMD / Terminal**
- **GitHub Desktop**

> Git er versionsstyringen på din computer. GitHub er den centrale tjeneste, hvor repositories, branches og Pull Requests ligger.

---

## Hurtigt overblik

Det normale workflow er:

```text
Hent seneste ændringer
        ↓
Opret en branch
        ↓
Lav dine ændringer
        ↓
Commit
        ↓
Push til GitHub
        ↓
Opret Pull Request
        ↓
Review
        ↓
Merge til main
```

### CMD

```bash
git switch main
git pull
git switch -c feature/min-aendring

# Lav dine ændringer

git status
git add .
git commit -m "Add min ændring"
git push -u origin feature/min-aendring
```

Derefter opretter du en **Pull Request** på GitHub.

### GitHub Desktop

1. Vælg `main` som Current Branch.
2. Klik **Fetch origin** og derefter **Pull origin**, hvis der er nye ændringer.
3. Klik **Current Branch → New Branch**.
4. Giv branchen et navn, fx `feature/min-aendring`.
5. Lav dine ændringer i projektet.
6. Gå tilbage til GitHub Desktop og gennemgå ændringerne under **Changes**.
7. Skriv en commit-besked.
8. Klik **Commit to feature/min-aendring**.
9. Klik **Publish branch** eller **Push origin**.
10. Klik **Create Pull Request**.
11. Gennemgå Pull Request på GitHub og merge efter review.

---

# 1. Hvad er Git og GitHub?

## Git

Git holder styr på ændringer i filer.

Det giver blandt andet mulighed for at:

- se hvem der har ændret hvad
- gå tilbage til tidligere versioner
- arbejde på forskellige branches
- arbejde flere personer på samme projekt

## GitHub

GitHub fungerer som den centrale placering for projektet.

```text
Din computer
     |
     | Git push / pull
     v
   GitHub
     |
     +-- main
     +-- feature/*
     +-- bugfix/*
```

GitHub bruges også til blandt andet:

- Pull Requests
- Code Review
- Issues
- GitHub Actions
- adgangsstyring

---

# 2. Installation

## Git til CMD / Terminal

### Windows

Installer Git med Winget:

```powershell
winget install --id Git.Git -e
```

Kontroller installationen:

```powershell
git --version
```

Git kan også installeres fra:

https://git-scm.com/

## GitHub Desktop

Download GitHub Desktop fra:

https://desktop.github.com/

Log derefter ind med den GitHub-konto, som har adgang til virksomhedens repositories.

---

# 3. Første opsætning i CMD

Sæt navn:

```bash
git config --global user.name "Dit Navn"
```

Sæt e-mail:

```bash
git config --global user.email "din@arbejdsmail.dk"
```

Se konfigurationen:

```bash
git config --global --list
```

Det er en god idé at bruge den e-mailadresse, som er tilknyttet din GitHub-konto eller virksomhedens GitHub-organisation.

---

# 4. Clone et eksisterende repository

Hvis projektet allerede findes på GitHub, skal det normalt **clones**.

## CMD – HTTPS

```bash
git clone https://github.com/ORGANISATION/PROJECT.git
```

Eksempel:

```bash
git clone https://github.com/example-company/website.git
```

Gå ind i projektmappen:

```bash
cd website
```

## CMD – SSH

```bash
git clone git@github.com:ORGANISATION/PROJECT.git
```

Eksempel:

```bash
git clone git@github.com:example-company/website.git
```

## GitHub Desktop

1. Åbn GitHub Desktop.
2. Klik **File → Clone Repository**.
3. Vælg fanen **GitHub.com**.
4. Find virksomhedens repository.
5. Vælg hvor projektet skal ligge under **Local Path**.
6. Klik **Clone**.

---

# 5. Hent de nyeste ændringer

Det er en god vane at opdatere `main`, før du starter nyt arbejde.

## CMD

```bash
git switch main
git pull
```

## GitHub Desktop

1. Vælg **Current Branch → main**.
2. Klik **Fetch origin**.
3. Hvis GitHub Desktop viser nye commits, klik **Pull origin**.

### Forskel på Fetch og Pull

**Fetch** kontrollerer om der findes nye ændringer på GitHub.

**Pull** henter ændringerne ned til din lokale branch.

---

# 6. Opret en branch

På en arbejdsplads bør man normalt ikke arbejde direkte på `main`.

Opret i stedet en branch til opgaven.

Eksempler:

```text
feature/login-page
feature/add-backup
bugfix/login-error
docs/update-readme
```

## CMD

```bash
git switch -c feature/min-aendring
```

Se hvilken branch du står på:

```bash
git branch
```

Den aktive branch har `*` foran navnet.

## GitHub Desktop

1. Klik **Current Branch**.
2. Klik **New Branch**.
3. Skriv fx:

```text
feature/min-aendring
```

4. Kontroller at branchen oprettes fra `main`.
5. Klik **Create Branch**.

---

# 7. Se hvad du har ændret

## CMD

Se hvilke filer der er ændret:

```bash
git status
```

Se selve ændringerne:

```bash
git diff
```

## GitHub Desktop

GitHub Desktop viser automatisk ændrede filer under **Changes**.

Klik på en fil for at se:

- linjer der er tilføjet
- linjer der er fjernet
- præcis hvad der bliver committed

Du kan fjerne fluebenet ved en fil, hvis den ikke skal med i det næste commit.

---

# 8. Stage ændringer

I CMD skal filer normalt stages, før de kan committes.

## CMD – alle ændringer

```bash
git add .
```

## CMD – kun én fil

```bash
git add README.md
```

Se staged filer:

```bash
git status
```

## GitHub Desktop

GitHub Desktop har ikke et separat `git add`-trin på samme måde i brugerfladen.

Filer med flueben under **Changes** bliver inkluderet i dit næste commit.

---

# 9. Commit ændringer

Et commit gemmer et punkt i Git-historikken.

## CMD

```bash
git commit -m "Add login validation"
```

## GitHub Desktop

1. Gennemgå filerne under **Changes**.
2. Skriv en kort besked i **Summary**.
3. Tilføj eventuelt en længere forklaring i **Description**.
4. Klik **Commit to BRANCH-NAVN**.

## Gode commit-beskeder

Godt:

```text
Add login validation
Fix broken navigation link
Update backup documentation
Remove unused configuration
```

Mindre godt:

```text
update
fix
stuff
changes
```

Commit-beskeden bør kort forklare **hvad ændringen gør**.

---

# 10. Push ændringer til GitHub

Et commit ligger først kun på din computer.

For at sende det til GitHub skal du lave et **push**.

## CMD – første push af en ny branch

```bash
git push -u origin feature/min-aendring
```

Efter første push kan du normalt bruge:

```bash
git push
```

## GitHub Desktop

På en ny branch:

Klik **Publish branch**.

Efterfølgende commits:

Klik **Push origin**.

---

# 11. Opret en Pull Request

Når branchen er pushed til GitHub, kan du oprette en Pull Request.

En Pull Request foreslår at ændringerne bliver merged ind i eksempelvis `main`.

## CMD

Selve Git-kommandoen `git push` opretter ikke automatisk en Pull Request.

Efter push åbner du GitHub i browseren og opretter en Pull Request fra din branch til `main`.

Hvis virksomheden bruger GitHub CLI, kan man også bruge:

```bash
gh pr create
```

Det kræver, at GitHub CLI er installeret og logget ind.

## GitHub Desktop

1. Commit dine ændringer.
2. Klik **Push origin** eller **Publish branch**.
3. Klik **Create Pull Request**.
4. GitHub åbnes i browseren.
5. Kontroller:

```text
base: main
compare: feature/min-aendring
```

6. Skriv en titel og beskrivelse.
7. Klik **Create Pull Request**.

---

# 12. Review og Merge

En typisk Pull Request kan se sådan ud:

```text
feature/min-aendring
       |
       v
Pull Request
       |
       +-- Code Review
       +-- Tests / GitHub Actions
       |
       v
     main
```

Følg virksomhedens regler for review og merge.

På nogle arbejdspladser må udvikleren selv merge efter godkendelse.

Andre steder skal en anden medarbejder godkende og merge.

---

# 13. Efter en Pull Request er merged

Når din branch er merged til `main`, skal du opdatere din lokale kopi.

## CMD

```bash
git switch main
git pull
git branch -d feature/min-aendring
```

`git branch -d` sletter kun din **lokale** branch.

Hvis remote-branchen ikke blev slettet automatisk på GitHub, kan den slettes med:

```bash
git push origin --delete feature/min-aendring
```

## GitHub Desktop

1. Skift til **main** under **Current Branch**.
2. Klik **Fetch origin**.
3. Klik **Pull origin**, hvis der er nye ændringer.
4. Vælg den gamle branch under **Current Branch**.
5. Højreklik på branchen og vælg **Delete** hvis den ikke længere skal bruges.

---

# 14. Hvis andre har ændret samme branch

Hvis GitHub har commits, som du ikke har lokalt, kan et push blive afvist.

## CMD

Start med:

```bash
git pull
```

Hvis Git melder om konflikter, skal de løses før du kan push igen.

## GitHub Desktop

GitHub Desktop viser normalt **Pull origin**, hvis remote-branchen har nye commits.

Klik **Pull origin** før du fortsætter.

---

# 15. Merge conflicts

En merge conflict opstår typisk, når to personer har ændret samme del af samme fil.

Git kan vise noget i denne stil:

```text
<<<<<<< HEAD
Din ændring
=======
Den anden ændring
>>>>>>> branch-navn
```

Du skal vælge den rigtige version og fjerne conflict-markeringerne.

## CMD

Når konflikten er rettet:

```bash
git add .
git commit
```

Hvis konflikten opstod under en normal merge, afslutter det merge-committen.

Derefter:

```bash
git push
```

> Brug ikke automatisk `git commit -m "Resolve merge conflict"` uden først at kontrollere hvad der faktisk blev resolved.

## GitHub Desktop

GitHub Desktop viser hvilke filer der har konflikter.

1. Åbn filen i din editor.
2. Ret konflikten.
3. Gem filen.
4. Marker konflikten som løst, hvis GitHub Desktop beder om det.
5. Commit merge-resultatet.
6. Klik **Push origin**.

---

# 16. `.gitignore`

`.gitignore` bestemmer hvilke filer Git ikke skal tracke.

Eksempel:

```gitignore
.env
node_modules/
*.log
.idea/
.vscode/
```

## Commit aldrig secrets

Undgå at committe:

- passwords
- API keys
- access tokens
- private SSH keys
- produktions-secrets
- `.env` filer med rigtige credentials

Eksempel på en sikker skabelon:

```text
.env.example
```

Med fx:

```text
DATABASE_HOST=
DATABASE_USER=
DATABASE_PASSWORD=
```

### Vigtigt

Hvis en secret først er blevet committed, er det **ikke nok** bare at slette den i næste commit.

Den kan stadig eksistere i Git-historikken.

Credentialen bør derfor roteres eller ugyldiggøres, og historikken kan efter behov skulle renses.

---

# 17. SSH til GitHub

Hvis arbejdspladsen bruger SSH i stedet for HTTPS, kan du oprette en SSH-nøgle.

## Opret nøgle

```bash
ssh-keygen -t ed25519 -C "din@arbejdsmail.dk"
```

Public key ligger normalt her på Windows:

```text
C:\Users\DIT_NAVN\.ssh\id_ed25519.pub
```

Vis den i CMD:

```cmd
type %USERPROFILE%\.ssh\id_ed25519.pub
```

I PowerShell:

```powershell
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub
```

Tilføj **public key** på GitHub under:

```text
Settings → SSH and GPG keys → New SSH key
```

Test forbindelsen:

```bash
ssh -T git@github.com
```

> Del aldrig filen `id_ed25519`. Det er din private nøgle.

---

# 18. HTTPS eller SSH?

Begge dele kan bruges med GitHub.

| Metode | Fordel |
|---|---|
| HTTPS | Nem at komme i gang med og fungerer godt med Git Credential Manager |
| SSH | Praktisk til terminalbrug, automatisering og faste udviklingsmaskiner |
| GitHub Desktop | Håndterer GitHub-login gennem Desktop og bruger HTTPS til GitHub |

Brug den metode virksomheden har valgt som standard.

---

# 19. Nyttige CMD-kommandoer

## Se status

```bash
git status
```

## Se historik

```bash
git log --oneline
```

## Se branches

```bash
git branch
```

## Se remote repository

```bash
git remote -v
```

## Se ændringer

```bash
git diff
```

## Se staged ændringer

```bash
git diff --staged
```

## Skift branch

```bash
git switch branch-navn
```

## Opret branch

```bash
git switch -c branch-navn
```

## Fortryd ikke-committede ændringer i én fil

```bash
git restore filnavn.txt
```

> Denne kommando kan slette lokale ændringer. Brug den kun hvis du er sikker på, at ændringerne ikke skal gemmes.

---

# 20. CMD Cheat Sheet

| Det du vil gøre | Kommando |
|---|---|
| Clone repository | `git clone URL` |
| Se status | `git status` |
| Hent ændringer | `git pull` |
| Se ændringer | `git diff` |
| Stage alt | `git add .` |
| Commit | `git commit -m "besked"` |
| Push | `git push` |
| Se branches | `git branch` |
| Opret branch | `git switch -c navn` |
| Skift branch | `git switch navn` |
| Se historik | `git log --oneline` |
| Se remote | `git remote -v` |

---

# 21. GitHub Desktop Cheat Sheet

| Det du vil gøre | GitHub Desktop |
|---|---|
| Clone repository | **File → Clone Repository** |
| Skift branch | **Current Branch** |
| Opret branch | **Current Branch → New Branch** |
| Se ændringer | **Changes** |
| Commit | Skriv **Summary** → **Commit to ...** |
| Se nye remote ændringer | **Fetch origin** |
| Hent ændringer | **Pull origin** |
| Upload branch første gang | **Publish branch** |
| Upload nye commits | **Push origin** |
| Opret Pull Request | **Create Pull Request** |
| Åbn repository på GitHub | **Repository → View on GitHub** |

---

# 22. Det vigtigste at huske

Hvis du bruger **CMD**:

```bash
git switch main
git pull
git switch -c feature/min-aendring

# Lav ændringer

git status
git add .
git commit -m "Beskriv ændringen"
git push -u origin feature/min-aendring
```

Hvis du bruger **GitHub Desktop**:

```text
main
 ↓
Fetch / Pull origin
 ↓
New Branch
 ↓
Lav ændringer
 ↓
Changes
 ↓
Commit
 ↓
Publish branch / Push origin
 ↓
Create Pull Request
```

## Arbejdsregel

**Arbejd som udgangspunkt ikke direkte på `main`.**

Brug:

```text
Branch → Commit → Push → Pull Request → Review → Merge
```

medmindre virksomhedens egne Git-regler siger noget andet.
