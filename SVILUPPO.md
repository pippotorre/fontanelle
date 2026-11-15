# Sviluppo — Fontanelle

Scopo: trovare la fontanella pubblica più vicina in tutta Italia. Stack: HTML/CSS/JS puro, Leaflet vendored, nessuna build. Hosting: GitHub Pages (dominio personalizzato fontanelle.entratadisicurezza.com). Dati: OpenStreetMap, tessere pronte in `data/t/` + Overpass dal vivo.

## Funzioni
- [x] Ricerca da posizione (GPS/rete) o toccando la mappa; raggio 1→5 km.
- [x] Tessere nazionali rigenerate ogni settimana (workflow).
- [x] Percorso a piedi, link a Google/Apple Maps, 5 lingue, installabile, offline parziale.
- [ ] Prima pubblicazione: impostare Pages e lanciare il workflow (docs/PAGES.md).
- [ ] App Android su Google Play (docs/ANDROID.md).

## Diario
| Data | Cosa |
|---|---|
| 14/11/2026 | Creata da Nasone con grafica blu e testi generici; copertura nazionale a tessere. |
| 14/11/2026 | Tessere statiche come fonte principale: dentro la zona e con dati < 10 giorni nessuna chiamata a Overpass (che resta per fuori zona, dati vecchi o mancanti). |
| 15/11/2026 | **Statistiche.** Sul sottodominio il percorso della pagina è `/` per tutte le app, quindi dal 14/11 le visite finivano mescolate in un'unica voce `/` di GoatCounter. Ora lo script in `index.html` mette `/fontanelle` davanti al percorso (`/fontanelle/`): così l'app ha la sua voce nella dashboard comune https://entratadisicurezza.goatcounter.com. Se la pagina è già sotto `/fontanelle/` (vecchio indirizzo) il nome non viene ripetuto. Eventi `fontanelle-installa-…` invariati. Provato in Chromium sul sottodominio con lo script vero di GoatCounter. |
