# Fejl og løsninger

Her er nogle af de mest almindelige Git-problemer.

## Merge conflict

En merge conflict opstår typisk, når to personer har ændret den samme del af den samme fil.

Git kan vise noget i denne stil:

```text
<<<<<<< HEAD
Din ændring
=======
Den anden ændring
>>>>>>> origin/main
```

Du skal vælge, hvad der skal beholdes, og fjerne conflict-markeringerne.

Derefter:

```bash
git add .
git commit -m "Resolve merge conflict"
git push
```

I GitHub Desktop bliver conflicten vist i brugerfladen. Åbn de berørte filer, løs konflikten, markér den som løst og commit ændringen.

---

## `git push` bliver afvist

Hvis andre har pushed ændringer før dig, kan Git afvise dit push.

Prøv først:

```bash
git pull
```

Hvis der kommer en conflict, skal den løses før du kan push igen.

Undgå at bruge `git push --force` på fælles branches, medmindre du ved præcis hvorfor det er nødvendigt og teamets regler tillader det.

---

## Jeg er på den forkerte branch

Se hvilken branch du er på:

```bash
git branch
```

Skift branch:

```bash
git switch main
```

---

## Jeg vil se, hvad jeg har ændret

```bash
git status
git diff
```

Staged ændringer:

```bash
git diff --staged
```

---

## Jeg vil fortryde lokale ændringer i en fil

```bash
git restore FILNAVN
```

Eksempel:

```bash
git restore README.md
```

> Dette fjerner lokale ændringer i filen, som ikke er committed. Brug kommandoen med omtanke.

---

## Jeg har committed noget forkert

Hvis det allerede er pushed til en fælles branch, er den sikreste løsning ofte at lave et nyt commit, der retter fejlen, i stedet for at omskrive historikken.

Hvis du er i tvivl, spørg en kollega før du bruger kommandoer som:

```text
git reset
git rebase
git push --force
```

De kan ændre Git-historikken og skabe problemer for andre.

---

## Jeg kom til at committe et password eller token

Det er ikke nok bare at slette det i et nyt commit, fordi værdien stadig kan ligge i Git-historikken.

Gør som minimum:

1. Deaktivér eller roter password/token med det samme
2. Informér den relevante ansvarlige på arbejdspladsen
3. Fjern hemmeligheden fra koden
4. Følg virksomhedens procedure for at rense Git-historikken, hvis det er nødvendigt

Commit aldrig:

- Passwords
- API keys
- Access tokens
- Private SSH keys
- Produktions-secrets
- `.env` filer med credentials

---

## GitHub Desktop viser ikke mine ændringer

Kontroller:

1. At det rigtige repository er valgt
2. At du redigerer filer i den lokale repository-mappe
3. At filen ikke er ignoreret via `.gitignore`
4. At du er på den branch, du forventer

---

## Hurtig kontrol

Når noget ser forkert ud i CMD, er disse kommandoer et godt sted at starte:

```bash
git status
git branch
git remote -v
git log --oneline -10
```

De ændrer ikke noget og giver et hurtigt overblik over repository'et.
