# Branches og Pull Requests

Denne side forklarer det vigtigste om branches og Pull Requests på en arbejdsplads.

## Hvorfor bruge branches?

En branch gør det muligt at arbejde på en ændring uden at ændre `main` direkte.

Eksempel:

```text
main
 └── feature/new-login
```

Når arbejdet er klar, opretter du en Pull Request tilbage til `main`.

---

## Gode branch-navne

Brug korte og tydelige navne.

```text
feature/new-login
bugfix/printer-error
docs/update-guide
```

Undgå fx:

```text
test
ny
seb-branch
```

---

## Opret en branch i CMD

Start fra opdateret `main`:

```bash
git switch main
git pull
git switch -c feature/new-login
```

---

## Opret en branch i GitHub Desktop

1. Skift til `main`
2. Klik **Fetch origin** / **Pull origin**
3. Klik **Current branch**
4. Klik **New branch**
5. Skriv branch-navnet
6. Klik **Create branch**

---

## Pull Request

En Pull Request bruges til at foreslå, gennemgå og merge ændringer.

Et typisk flow:

```text
Branch
  ↓
Commits
  ↓
Push
  ↓
Pull Request
  ↓
Review
  ↓
Eventuelle rettelser
  ↓
Merge til main
```

## Hvad skal en Pull Request indeholde?

En god Pull Request bør kort forklare:

- Hvad der er ændret
- Hvorfor det er ændret
- Om der er noget særligt, reviewer skal teste eller være opmærksom på

Eksempel:

```text
Titel: Fix printer mapping for Finance

Ændrer printer-mappingen for Finance-brugere, så den nye printer bliver sat som standard.
```

---

## Efter merge

Opdater din lokale `main`.

CMD:

```bash
git switch main
git pull
```

GitHub Desktop:

1. Skift til `main`
2. Klik **Fetch origin**
3. Klik **Pull origin**

Slet derefter den gamle branch, hvis den ikke længere skal bruges.

---

## Arbejd ikke direkte på main

På et team er det normalt en dårlig idé at lave almindelige ændringer direkte på `main`.

Branches og Pull Requests giver blandt andet:

- Code review
- Tydelig historik
- Mindre risiko for fejl på `main`
- Mulighed for at diskutere ændringer før merge
