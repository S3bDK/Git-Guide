# Git i CMD / Terminal

Denne guide viser det normale Git-workflow med kommandoer.

## 1. Første opsætning

Tjek at Git er installeret:

```bash
git --version
```

Sæt navn og e-mail:

```bash
git config --global user.name "Dit Navn"
git config --global user.email "din@email.dk"
```

---

## 2. Clone et repository

HTTPS:

```bash
git clone https://github.com/organisation/project.git
```

SSH:

```bash
git clone git@github.com:organisation/project.git
```

Gå ind i mappen:

```bash
cd project
```

---

## 3. Start altid med at hente ændringer

Skift til `main`:

```bash
git switch main
```

Hent seneste ændringer:

```bash
git pull
```

---

## 4. Opret en branch

```bash
git switch -c feature/min-aendring
```

Eksempler på branch-navne:

```text
feature/new-login
bugfix/printer-error
docs/update-guide
```

---

## 5. Lav ændringer og se status

```bash
git status
```

Se præcist hvad der er ændret:

```bash
git diff
```

---

## 6. Stage ændringer

Alle ændringer:

```bash
git add .
```

Kun én fil:

```bash
git add README.md
```

Kontroller igen:

```bash
git status
```

---

## 7. Commit

```bash
git commit -m "Update printer configuration"
```

Brug en kort besked der forklarer hvad du ændrede.

---

## 8. Push

Første gang en ny branch pushes:

```bash
git push -u origin feature/min-aendring
```

Efterfølgende:

```bash
git push
```

Opret derefter en Pull Request på GitHub.

---

## 9. Efter din Pull Request er merged

Skift tilbage til `main`:

```bash
git switch main
```

Hent den nye version:

```bash
git pull
```

Slet den gamle lokale branch:

```bash
git branch -d feature/min-aendring
```

---

# Hurtigt workflow

```bash
git switch main
git pull
git switch -c feature/min-aendring

# Lav dine ændringer

git status
git add .
git commit -m "Beskriv ændringen"
git push -u origin feature/min-aendring
```

Derefter: **Pull Request → Review → Merge**.

---

# Nyttige kommandoer

| Kommando | Funktion |
|---|---|
| `git status` | Se ændrede filer |
| `git diff` | Se ændringer |
| `git pull` | Hent ændringer |
| `git add .` | Stage alle ændringer |
| `git commit -m "tekst"` | Lav commit |
| `git push` | Upload commits |
| `git branch` | Se branches |
| `git switch BRANCH` | Skift branch |
| `git switch -c BRANCH` | Opret ny branch |
| `git log --oneline` | Se commit-historik |
| `git remote -v` | Se GitHub remote |
