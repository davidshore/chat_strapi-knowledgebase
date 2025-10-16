# **Knowledge Hub** med Strapi 5 + TanStack Start

Bygg en enkel innehållssajt där **Strapi** fungerar som CMS och **TanStack Start** visar innehållet.

---

## 🎯 Lärandemål

- Modellera `Article` + `Category` i Strapi.
- Hämta data från Strapi i en **loader** (ingen client-fetch).
- Skapa dynamiska sidor: `/articles` och `/articles/$slug`.
- Rendera Strapi **Rich text** (rubriker, stycken, listor) i React.

---

## ✅ Resultat

När du är klar ska du ha:

- `/articles` – lista över alla artiklar (titel + kategori)
- `/articles/$slug` – en sida per artikel
- Rich text-innehåll renderas i React
- All data hämtas via **Route loaders**

---

## Del 1 – Strapi

### 1. Skapa content types

**Category**

- `name` (Text)
- `slug` (UID, target: name)

**Article**

- `title` (Text)
- `slug` (UID, target: title)
- `content` (**Rich Text**)
- `category` (Relation → many-to-one → Category)
- `publishedAt` (auto via Publish)

### 2. Lägg till innehåll

- Skapa **3 kategorier** (t.ex. Frontend, Backend, Tools)
- Skapa **5 artiklar** med **Rich Text** (rubriker, stycken, listor, bilder)
- Glöm inte att **Publicera** allt

### 3. Tillåt publik åtkomst

Gå till:  
**Settings → Users & Permissions → Roles → Public**  
Kryssa i:

- `Article`: find, findOne
- `Category`: find, findOne

---

## Del 2 – TanStack Start

### 1. Skapa nytt projekt

```bash
npm create @tanstack/start@latest knowledge-hub
cd knowledge-hub
npm i
npm run dev
```

### Routes & sidor

#### `/articles` (lista alla artiklar)

Skapa fil: `routes/articles.tsx`

**Loader**

- Skapa getArticles som hämtar alla artiklar
- Returnera `{ articles }`

**Component**

- Visa lista med alla artiklar
  - Titel → länka till `/articles/$slug`
  - Visa kategori (om finns)

#### `/articles/$slug` (enskild artikel)

Skapa fil: `routes/articles_.$slug.tsx`

**Loader**

- Skapa getArticleBySlug som hämtar en artikel genom sin slug
- Returnera `{ article }`

**Component**

- Visa artikelns titel och kategori
- Använd `BlockRenderer` och prose för innehållet

#### BlockRenderer

Installera strapi block renderer och prose för att kunna visa Rich text
i artikeln.

---

## VG - Extra uppgifter

- `/categories` – lista alla kategorier
- Skapa kategori-sidor och Filtrera artiklar per kategori
- Skapa en första-sida som använder Blocks

---

**Mål:** Du har byggt en “Knowledge Hub” där TanStack Start och Strapi samverkar som fullstack-lösning!
