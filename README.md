# Mfumo wa Kuhifadhi Location (Location Tracking System)

Mfumo rahisi wa kuhifadhi eneo la watumiaji kwa idhini yao kwa kutumia Geolocation API na Node.js/Express backend.

## Sifa za Mfumo

- ✅ Kuhifadhi eneo la watumiaji (latitude, longitude)
- ✅ Interface rahisi kwa Kiswahili
- ✅ Kuhifadhi data kwenye faili `locations.txt`
- ✅ API endpoint `/api/save-location` (POST)
- ✅ Inapatika kwenye Render/Railway (cloud deployment)

## Muundo wa Faili

```
Location-tracking-/
├── package.json       # Project dependencies
├── server.js          # Express backend server
├── index.html         # Frontend interface
├── locations.txt      # Auto-generated locations log
└── README.md          # Documentation
```

## Jinsi ya Kuanzisha

### 1. Kuinstall Dependencies
```bash
npm install
```

### 2. Kuendesha Seva
```bash
npm start
```

Seva itaanza kwenye **http://localhost:3000**

### 3. Kubukwa kwenye Kivinjari
Fungua **http://localhost:3000** ili kuona interface

## API Endpoints

### POST `/api/save-location`

Kupokea na kuhifadhi location data

**Request Body:**
```json
{
    "latitude": 51.5074,
    "longitude": -0.1278,
    "timestamp": "2026-06-07T10:30:00Z"
}
```

**Response (Success):**
```json
{
    "status": "success",
    "message": "Location imepokelewa vizuri."
}
```

**Response (Error):**
```json
{
    "status": "error",
    "message": "Data hazijakamilika"
}
```

## Mfumo wa Kuhifadhi Data

Data zote zikamilifu zilizo na latitude na longitude zitahifadhiwa kwenye faili `locations.txt` kwa umbizo:

```
[6/7/2026, 1:30:45 PM] - Latitude: 51.5074, Longitude: -0.1278
[6/7/2026, 1:35:20 PM] - Latitude: 51.5080, Longitude: -0.1285
```

## Kutengeneza kwenye Cloud (Render/Railway)

### Kwa Render:
1. Fanya push ya repo kwenye GitHub
2. Fungua https://render.com
3. Weka "Connect GitHub repository"
4. Chagua repo hii
5. Fanya konfigurasi:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`

### Kwa Railway:
1. Fanya push ya repo kwenye GitHub
2. Fungua https://railway.app
3. Weka "Connect Repository"
4. Chagua repo hii
5. System itabuild na kucheza otomatiki

## Variables za Mazingira

- `PORT` - Port ambapo seva itaendesha (default: 3000)

## Mahitaji ya Browser

- Kioo kinachosupport **Geolocation API** (Chrome, Firefox, Safari, Edge)
- Ruhusa ya kufaham eneo

## Mabadiliko Muhimu

Kwenye `index.html`, unaweza kubadilisha:

```javascript
// Lini location imekubali, kuredeleza kwenye URL nyingine:
// window.location.href = "https://www.google.com";
```

## Shida na Suluhisho

| Shida | Suluhisho |
|-------|----------|
| Browser inapiga kelele "Geolocation not supported" | Tumia browser nyingine ya kisasa |
| "Permission denied" | Buruhsa haikuruhusu geolocation, cheki settings |
| "Failed to save location" | Akikaza katika kuandika faili, cheki folder permissions |

## Tekskani

Repo hii inatumiwa kwa madhumuni ya elimu pekee.

---

**Kirekebya:** 2026-06-07
