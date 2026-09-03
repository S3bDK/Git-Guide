# Git i CMD / Terminal

Denne guide viser det normale Git-workflow med kommandoer.

## 1. Login og første opsætning

På arbejdspladsen bruger du din **administrative konto** via virksomhedens login/SSO.

Hvis Git åbner et browser-login eller beder dig godkende adgang, skal du gennemføre virksomhedens login/SSO med din administrative konto.

Tjek at Git er installeret:

```bash
git --version
```

Sæt dit navn og din arbejds-e-mail til commits:

```bash
git config --global user.name "Dit Navn"
git config --global user.email "din@arbejdsplads.dk"
```

> Din Git commit-identitet og dit login er to forskellige ting. `user.name` og `user.email` bestemmer, hvem der står som forfatter på commits.

---

## 2. Clone et repository

Kopiér repository-adressen fra arbejdspladsens Git-side.

Eksempel med HTTPS:

```bash
git clone https://git-server/organisation/project.git
```

Gå ind i mappen:

```bash
cd project
```

Hvis login bliver vist i browseren, gennemfører du virksomhedens login/SSO med din administrative konto.

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

Hvis du bliver bedt om login, bruger du din administrative konto via virksomhedens login/SSO.

Opret derefter en Pull Request på arbejdspladsens Git-side.

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
| `git remote -v` | Se remote server |
