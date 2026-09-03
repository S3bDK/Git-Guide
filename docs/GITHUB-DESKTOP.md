# GitHub Desktop

Denne guide viser det normale workflow uden at bruge Git-kommandoer.

## 1. Login

På arbejdspladsen bruger du din **normale AD-konto** via virksomhedens login/SSO.

Når GitHub Desktop åbner browseren for login, skal du gennemføre virksomhedens AD/SSO-login og derefter gå tilbage til GitHub Desktop.

> Brug ikke en privat GitHub-konto, medmindre arbejdspladsen specifikt har bedt dig om det.

---

## 2. Clone et repository

1. Åbn **GitHub Desktop**
2. Vælg **File → Clone repository**
3. Find arbejdspladsens repository
4. Vælg hvor det skal gemmes
5. Klik **Clone**

Hvis du bliver bedt om login, bruger du din AD-konto via virksomhedens SSO.

---

## 3. Hent de nyeste ændringer

Klik først:

**Fetch origin**

Hvis der er nye ændringer, klik:

**Pull origin**

Gør dette før du starter nyt arbejde.

---

## 4. Opret en branch

1. Klik på **Current branch**
2. Klik **New branch**
3. Skriv fx:

```text
feature/min-aendring
```

4. Klik **Create branch**

Eksempler:

```text
feature/new-login
bugfix/printer-error
docs/update-guide
```

---

## 5. Lav dine ændringer

Åbn projektet i din editor og rediger filerne.

GitHub Desktop viser automatisk de filer, der er blevet ændret, under **Changes**.

Klik på en fil for at se præcis hvad der er ændret.

Du kan fjerne fluebenet ved filer, som ikke skal med i committet.

---

## 6. Commit

Nederst til venstre:

1. Skriv en kort **Summary**
2. Tilføj eventuelt en længere beskrivelse
3. Klik **Commit to [branch-navn]**

Eksempel på en god commit-besked:

```text
Update printer configuration
```

---

## 7. Upload ændringer

Hvis branchen ikke tidligere er uploaded, klik:

**Publish branch**

Hvis branchen allerede findes på serveren, klik:

**Push origin**

Hvis login bliver vist, gennemfører du arbejdspladsens AD/SSO-login.

---

## 8. Opret Pull Request

Når ændringerne er pushed:

1. Klik **Create Pull Request**
2. Git-siden åbnes i browseren
3. Kontroller at din branch bliver sammenlignet med `main`
4. Skriv en kort titel og beskrivelse
5. Opret Pull Request

Derefter kan ændringen blive reviewed og merged.

---

## 9. Efter Pull Request er merged

1. Skift **Current branch** til `main`
2. Klik **Fetch origin**
3. Klik **Pull origin**, hvis der er ændringer
4. Den gamle branch kan derefter slettes, hvis den ikke længere skal bruges

---

# Hurtigt workflow

```text
Fetch origin / Pull origin
        ↓
New branch
        ↓
Lav ændringer
        ↓
Kontroller Changes
        ↓
Commit to branch
        ↓
Publish branch / Push origin
        ↓
Create Pull Request
        ↓
Review
        ↓
Merge
```

---

# Hvad svarer knapperne til i CMD?

| GitHub Desktop | CMD / Terminal |
|---|---|
| Clone repository | `git clone` |
| Fetch origin | `git fetch` |
| Pull origin | `git pull` |
| New branch | `git switch -c BRANCH` |
| Changes | `git status` / `git diff` |
| Commit to branch | `git add` + `git commit` |
| Publish branch | `git push -u origin BRANCH` |
| Push origin | `git push` |

> GitHub Desktop håndterer staging gennem markeringerne ved filerne i **Changes**, så du behøver normalt ikke selv køre `git add`.
