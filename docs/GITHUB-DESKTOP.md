# GitHub Desktop

Denne guide viser det normale workflow i **GitHub Desktop** på arbejdspladsen.

## 1. Første gang du åbner GitHub Desktop

Når GitHub Desktop åbnes første gang:

1. Vælg muligheden for, at du **ikke har en GitHub-konto** / vil fortsætte uden at logge ind på GitHub.com.
2. Vælg derefter at hente et repository fra **internet / URL**.
3. Åbn arbejdspladsens **Git-server** i din browser.
4. Log ind på Git-serverens hjemmeside med din normale **AD-konto**.
5. Find det repository, du skal arbejde med.
6. Kopier repository'ets **HTTP/HTTPS clone-link**.

Eksempel:

```text
https://git-server/gruppe/projekt.git
```

> Brug det link, der står på arbejdspladsens Git-server. Eksemplet ovenfor er kun et eksempel.

---

## 2. Clone repository'et

I GitHub Desktop:

1. Vælg **Clone a repository from the Internet** / **Clone repository**.
2. Vælg fanen/feltet til **URL**.
3. Indsæt HTTP/HTTPS-linket fra Git-serveren.
4. Vælg hvor projektet skal gemmes på computeren under **Local path**.
5. Klik **Clone**.
6. Når login-vinduet vises, logger du ind med din normale **AD-konto**.

Når login er godkendt, bliver repository'et downloaded til computeren og åbnet i GitHub Desktop.

### Kort version

```text
Åbn GitHub Desktop
        ↓
Vælg at fortsætte uden GitHub.com-konto
        ↓
Clone repository fra internet / URL
        ↓
Åbn arbejdspladsens Git-server
        ↓
Find repository
        ↓
Kopier HTTP/HTTPS clone-link
        ↓
Indsæt linket i GitHub Desktop
        ↓
Klik Clone
        ↓
Log ind med AD-konto
```

---

## 3. Hent de nyeste ændringer

Inden du begynder at arbejde, skal du hente eventuelle nye ændringer fra serveren.

Klik først:

**Fetch origin**

Hvis der er nye ændringer, klik:

**Pull origin**

Gør dette før du starter nyt arbejde.

---

## 4. Opret en branch

Arbejd normalt ikke direkte på `main`.

1. Klik på **Current branch**.
2. Klik **New branch**.
3. Skriv et kort og beskrivende navn, fx:

```text
feature/min-aendring
```

Andre eksempler:

```text
feature/new-login
bugfix/printer-error
docs/update-guide
```

4. Klik **Create branch**.

---

## 5. Lav dine ændringer

Åbn projektet i den editor, du normalt bruger, og rediger filerne.

GitHub Desktop viser automatisk ændrede filer under **Changes**.

Her kan du:

- se hvilke filer der er ændret
- klikke på en fil og se ændringerne
- vælge hvilke filer der skal med i dit commit

Fjern fluebenet ved en fil, hvis den ikke skal med i det aktuelle commit.

---

## 6. Commit

Når ændringerne er klar:

1. Kontroller filerne under **Changes**.
2. Skriv en kort besked i **Summary**.
3. Tilføj eventuelt en længere beskrivelse.
4. Klik **Commit to [branch-navn]**.

Eksempel:

```text
Update printer configuration
```

Et commit gemmer ændringerne lokalt. De er endnu ikke sendt til Git-serveren.

---

## 7. Push ændringer til Git-serveren

Hvis branchen ikke tidligere er sendt til serveren, klik:

**Publish branch**

Hvis branchen allerede findes på serveren, klik:

**Push origin**

Hvis du bliver bedt om login igen, bruger du din **AD-konto**.

---

## 8. Opret Pull Request

Hvis arbejdspladsen bruger Pull Requests:

1. Push først dine ændringer.
2. Åbn repository'et på Git-serverens hjemmeside.
3. Find muligheden for at oprette en **Pull Request** eller **Merge Request**.
4. Kontroller at din branch bliver sammenlignet med `main`.
5. Skriv en kort titel og beskrivelse.
6. Opret requesten.

Derefter kan ændringen blive reviewed og merged til `main`.

> Navnet kan være **Pull Request** eller **Merge Request**, afhængigt af hvilken Git-server arbejdspladsen bruger.

---

## 9. Efter ændringen er merged

1. Skift **Current branch** til `main`.
2. Klik **Fetch origin**.
3. Klik **Pull origin**, hvis der er nye ændringer.
4. Slet eventuelt den gamle lokale branch, når den ikke længere skal bruges.

---

# Normalt workflow

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
Pull Request / Merge Request
        ↓
Review
        ↓
Merge til main
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

> GitHub Desktop håndterer staging gennem markeringerne ved filerne under **Changes**, så du behøver normalt ikke selv køre `git add`.
