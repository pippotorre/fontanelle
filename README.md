# Fontanelle — le fontanelle d'Italia più vicine

Web app (installabile come app su Android e iPhone) che trova la fontanella pubblica o il punto d'acqua potabile più vicino **in tutta Italia** e disegna il percorso a piedi. Lingue: italiano, inglese, francese, spagnolo, tedesco.

È la sorella «nazionale» di [Turet](https://github.com/pippotorre/turet) (Torino) e [Nasone](https://github.com/pippotorre/nasone) (Roma): stesso motore, copertura su tutta Italia. Sito: **https://fontanelle.entratadisicurezza.com/**

## Come funziona
- **Dati:** punti d'acqua potabile di OpenStreetMap (`amenity=drinking_water`, `amenity=fountain` con `drinking_water=yes`, rubinetti potabili, anche come aree).
- **Tessere pronte:** ogni lunedì un'azione di GitHub scarica tutta Italia con `node tools/genera-tessere.mjs` e la divide in tessere di 0,25° (`data/t/<riga>_<colonna>.json` + `index.json`). L'app scarica solo le tessere attorno a te. Dentro la zona coperta e con dati di meno di 10 giorni usa **solo** quelle: risultati immediati e nessuna richiesta ai server pubblici (che hanno limiti d'uso). Fuori zona, o con tessere vecchie o mancanti, interroga Overpass.
- **Percorsi:** routing.openstreetmap.de (a piedi). **Mappa:** OpenStreetMap con Leaflet (in `vendor/`).
- Raggio 1 km, estendibile a 2 / 3,5 / 5 km senza altre richieste.

## Pubblicazione
GitHub Pages su `https://fontanelle.entratadisicurezza.com/` tramite `.github/workflows/pubblica.yml`. Impostazione una tantum: [docs/PAGES.md](docs/PAGES.md). Google Play: [docs/ANDROID.md](docs/ANDROID.md).

## Struttura
`index.html`, `css/`, `js/` (app, geo, i18n), `vendor/leaflet/`, `img/`, `manifest.webmanifest`, `sw.js` (rete per prima, copia salvata solo offline), `privacy.html`, `data/t/` (generata), `tools/`, `test/` (`node test/geo.test.js && node test/i18n.test.js`), `art/` (`python3 art/build.py` rigenera icone e grafica dello store), `store/`, `docs/`.

## Privacy
La posizione non viene salvata né inviata a un server del progetto: resta nel browser. Ai servizi esterni vanno solo un punto arrotondato (circa 100 m) e, per il percorso, le due coordinate del tragitto. Statistiche di visita senza cookie con GoatCounter.
