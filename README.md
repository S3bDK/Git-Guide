# Git Guide

En kort og overskuelig guide til at bruge Git på arbejdspladsen.

## Login

På arbejdspladsen logger du ind med din **administrative konto** via virksomhedens login/SSO.

Hvis GitHub Desktop, Git eller browseren beder dig om at logge ind, skal du bruge din administrative konto og følge virksomhedens login/SSO.

> Brug ikke en privat GitHub-konto, medmindre arbejdspladsen specifikt har bedt dig om det.

---

## Start her

Vælg den måde du arbejder på:

- [Git i CMD / Terminal](docs/CMD.md)
- [GitHub Desktop](docs/GITHUB-DESKTOP.md)
- [Branches og Pull Requests](docs/BRANCHES-AND-PR.md)
- [Fejl, merge conflicts og løsninger](docs/TROUBLESHOOTING.md)

---

## Det normale workflow

Uanset om du bruger CMD eller GitHub Desktop, er arbejdsflowet stort set det samme:

```text
Hent seneste ændringer
        ↓
Opret en branch
        ↓
Lav dine ændringer
        ↓
Commit
        ↓
Push
        ↓
Pull Request
        ↓
Review
        ↓
Merge til main
```

> På en arbejdsplads bør man normalt undgå at arbejde direkte på `main`. Brug en branch og en Pull Request.

---

## Hurtig hjælp

### CMD / Terminal

```bash
git pull
git switch -c feature/min-aendring

git add .
git commit -m "Beskriv ændringen"
git push -u origin feature/min-aendring
```

Derefter oprettes en Pull Request.

### GitHub Desktop

1. Klik **Fetch origin** / **Pull origin**
2. Opret en ny branch
3. Lav dine ændringer
4. Skriv en commit-besked
5. Klik **Commit to ...**
6. Klik **Push origin** eller **Publish branch**
7. Klik **Create Pull Request**

---

## Vigtigt

Commit aldrig følsomme oplysninger som:

- Passwords
- API keys
- Access tokens
- Private SSH keys
- Produktions-secrets
- `.env` filer med rigtige credentials

Brug fx `.env.example` til eksempelværdier.
