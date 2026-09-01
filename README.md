# Git & Git Server Guide

En simpel guide til at komme i gang med **Git**, GitHub og en central Git-server.

## Indhold

1. Hvad er Git?
2. Installation
3. Første opsætning
4. De vigtigste kommandoer
5. Clone et repository
6. Opret et repository
7. Normalt workflow
8. Branches
9. GitHub / Git-server
10. SSH-nøgler
11. `.gitignore`
12. Merge conflicts
13. Gode commit-beskeder
14. Cheat sheet

---

## 1. Hvad er Git?

Git er et versionsstyringssystem, som holder styr på ændringer i filer og gør det muligt for flere personer at arbejde på samme projekt.

Det bruges blandt andet til:

- Programmering
- Scripts
- Serverkonfiguration
- Dokumentation
- Websites

---

## 2. Installation

### Windows

```powershell
winget install --id Git.Git -e
```

Kontroller installationen:

```powershell
git --version
```

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install git -y
```

---

## 3. Første opsætning

```bash
git config --global user.name "Dit Navn"
git config --global user.email "din@email.dk"
```

Se konfigurationen:

```bash
git config --list
```

---

## 4. De vigtigste Git-kommandoer

Se status:

```bash
git status
```

Tilføj alle ændringer:

```bash
git add .
```

Lav et commit:

```bash
git commit -m "Beskrivelse af ændringen"
```

Upload commits:

```bash
git push
```

Hent ændringer:

```bash
git pull
```

Se historik:

```bash
git log --oneline
```

---

## 5. Clone et repository

### HTTPS

```bash
git clone https://github.com/organisation/project.git
```

### SSH

```bash
git clone git@github.com:organisation/project.git
```

Gå ind i projektet:

```bash
cd project
```

---

## 6. Opret et nyt lokalt repository

```bash
mkdir my-project
cd my-project
git init
```

Opret en README og lav første commit:

```bash
echo "# My Project" > README.md
git add .
git commit -m "Initial commit"
```

Sæt hovedbranch til `main`:

```bash
git branch -M main
```

Tilføj GitHub som remote:

```bash
git remote add origin git@github.com:organisation/my-project.git
```

Upload:

```bash
git push -u origin main
```

---

## 7. Normalt workflow

Et almindeligt workflow er:

```text
Pull
 ↓
Opret/skift branch
 ↓
Rediger filer
 ↓
Git status
 ↓
Git add
 ↓
Git commit
 ↓
Git push
 ↓
Pull Request
 ↓
Review
 ↓
Merge til main
```

Eksempel:

```bash
git pull
git switch -c feature/min-aendring

# Lav dine ændringer

git status
git add .
git commit -m "Add ny funktion"
git push -u origin feature/min-aendring
```

Opret derefter en **Pull Request** på GitHub.

---

## 8. Branches

Se branches:

```bash
git branch
```

Opret og skift branch:

```bash
git switch -c feature/navn
```

Skift tilbage til main:

```bash
git switch main
```

Hent seneste main:

```bash
git pull
```

Slet en lokal branch efter merge:

```bash
git branch -d feature/navn
```

### Anbefaling på arbejdspladsen

Arbejd normalt ikke direkte på `main`. Brug en branch og en Pull Request, så ændringer kan gennemgås før merge.

---

## 9. GitHub / Git-server

GitHub fungerer som den centrale Git-server.

```text
Developer PC
     |
     | HTTPS / SSH
     v
   GitHub
     |
     +-- main
     +-- feature/*
     +-- bugfix/*
```

Se hvilken remote et projekt bruger:

```bash
git remote -v
```

Skift remote URL:

```bash
git remote set-url origin git@github.com:organisation/project.git
```

---

## 10. SSH-nøgler

Opret en SSH-nøgle:

```bash
ssh-keygen -t ed25519
```

Public key ligger normalt her:

### Windows

```text
C:\Users\DIT_NAVN\.ssh\id_ed25519.pub
```

### Linux

```text
~/.ssh/id_ed25519.pub
```

Vis public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Tilføj public key på GitHub under **Settings → SSH and GPG keys**.

Test forbindelsen:

```bash
ssh -T git@github.com
```

> Del aldrig din private SSH key med andre.

---

## 11. `.gitignore`

`.gitignore` fortæller Git hvilke filer og mapper der ikke skal gemmes i repository'et.

Eksempel:

```gitignore
.env
node_modules/
*.log
.vscode/
.idea/
```

### Vigtigt

Commit aldrig:

- Passwords
- API keys
- Access tokens
- Private SSH keys
- Produktions-secrets
- `.env` filer med følsomme oplysninger

Brug eventuelt en `.env.example` med tomme eksempelværdier.

---

## 12. Merge conflicts

Hvis to personer ændrer samme del af samme fil, kan Git lave en merge conflict.

Eksempel:

```text
<<<<<<< HEAD
Din ændring
=======
Den anden ændring
>>>>>>> origin/main
```

Ret filen manuelt, fjern conflict-markeringerne og kør:

```bash
git add .
git commit -m "Resolve merge conflict"
git push
```

---

## 13. Gode commit-beskeder

Undgå meget uklare commits som:

```text
update
fix
stuff
```

Brug hellere:

```text
Add backup validation
Fix login redirect
Update server documentation
Remove unused configuration
```

Et godt commit bør kort forklare **hvad der blev ændret**.

---

## 14. Nyttige kommandoer

Se ændringer:

```bash
git diff
```

Se staged ændringer:

```bash
git diff --staged
```

Fortryd lokale ændringer i en fil:

```bash
git restore README.md
```

Fjern en fil:

```bash
git rm filename.txt
git commit -m "Remove old file"
```

Omdøb en fil:

```bash
git mv oldname.txt newname.txt
git commit -m "Rename file"
```

---

## 15. Git Cheat Sheet

| Kommando | Funktion |
|---|---|
| `git clone URL` | Download repository |
| `git status` | Se status |
| `git pull` | Hent seneste ændringer |
| `git add .` | Stage alle ændringer |
| `git commit -m "tekst"` | Lav commit |
| `git push` | Upload commits |
| `git log --oneline` | Se kort historik |
| `git diff` | Se lokale ændringer |
| `git branch` | Se branches |
| `git switch BRANCH` | Skift branch |
| `git switch -c BRANCH` | Opret og skift branch |
| `git remote -v` | Se remote server |

---

## Hurtigt workflow

```bash
git pull
git switch -c feature/min-aendring

# Lav ændringer

git status
git add .
git commit -m "Beskriv ændringen"
git push -u origin feature/min-aendring
```

Opret derefter en Pull Request på GitHub og få ændringen reviewed før merge til `main`.

---

## Husk

Før du begynder at arbejde:

```bash
git pull
```

Når dine ændringer er klar:

```bash
git add .
git commit -m "Beskriv ændringen"
git push
```

Og gem aldrig passwords, tokens eller andre secrets direkte i Git.
