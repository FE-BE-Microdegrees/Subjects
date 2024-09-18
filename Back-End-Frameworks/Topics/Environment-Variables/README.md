# Keskkonnamuutujad, ehk Environmental Variables

- [Keskkonnamuutujad, ehk Environmental Variables](#keskkonnamuutujad-ehk-environmental-variables)
  - [Õpiväljundid](#õpiväljundid)
  - [Keskkonnamuutujate kasutamine Node.js-is](#keskkonnamuutujate-kasutamine-nodejs-is)
    - [Näide `.env` failist](#näide-env-failist)
    - [`dotenv` Mooduli Kasutamine](#dotenv-mooduli-kasutamine)
    - [Keskkonnamuutujate Kasutamine Otse Käsurealt](#keskkonnamuutujate-kasutamine-otse-käsurealt)
    - [Keskkonna Tuvastamine](#keskkonna-tuvastamine)
    - [Keskkonnamuutujate Lisamine `package.json`-i](#keskkonnamuutujate-lisamine-packagejson-i)

## Õpiväljundid

Peale selle peatüki läbimist:

- oskad seadistada keskkonnamuutujaid Node.js-is
- oskad kasutada keskkonnamuutujaid Node.js-is

Keskkonnamuutujad on muutujad, mis on saadaval kõigile protsessidele, mis töötavad arvutis. Need on kasulikud, et määrata erinevaid seadeid ja parameetreid, nagu andmebaasi ühendused, API võtmed jne. Kasutades keskkonnamuutujaid, saame muuta rakenduse konfiguratsiooni ilma koodi muutmata, võimaldades erinevate keskkondade, näiteks arenduse, testimise ja tootmise vahel sujuvat üleminekut.

## Keskkonnamuutujate kasutamine Node.js-is

Keskkonnamuutujaid saab Node.js-is kasutada mitmel viisil. Üks levinud praktika on salvestada muutujad eraldi `.env` failis ja kasutada neid rakenduses.

### Näide `.env` failist

```bash
DB_HOST=localhost
DB_USER=root
DB_PASS=secret
```

### `dotenv` Mooduli Kasutamine

1. **Installi `dotenv` moodul:**

```bash
npm install dotenv
```

2. **Laadi `.env` fail rakenduses:**

```javascript
require("dotenv").config();
```

3. **Kasu muutujaid rakenduses:**

```javascript
const host = process.env.DB_HOST;
const user = process.env.DB_USER;
const pass = process.env.DB_PASS;
```

### Keskkonnamuutujate Kasutamine Otse Käsurealt

Samuti saab keskkonnamuutujaid määrata otse käsurealt. Näiteks:

```bash
PORT=3000 node index.js
```

Rakenduses:

```javascript
const port = process.env.PORT;
```

### Keskkonna Tuvastamine

Saame määrata, kas rakendus töötab arendus-, tootmis- või testikeskkonnas:

```bash
NODE_ENV=development node index.js
```

Rakenduses:

```javascript
const env = process.env.NODE_ENV;
const db = env === "test" ? "testdb" : "db";
```

### Keskkonnamuutujate Lisamine `package.json`-i

Keskkonnamuutujate lisamiseks `package.json`-isse on mugav kasutada `cross-env` moodulit:

1. **Installi `cross-env`:**

```bash
npm install cross-env
```

2. **Lisa skript `package.json`-i:**

```json
{
  "scripts": {
    "start": "cross-env NODE_ENV=production node index.js"
  }
}
```

`cross-env` võimaldab keskkonnamuutujate määramist sarnaselt erinevates operatsioonisüsteemides, tagades, et käsud töötavad nii Windowsis kui ka UNIX-põhistes süsteemides.

Nende praktikate kasutamine aitab hoida rakenduse konfiguratsiooni puhtana ja turvalisena, vältides tundlike andmete, nagu paroolid ja API võtmed, avalikustamist.
