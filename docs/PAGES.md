# Pubblicazione su GitHub Pages — Fontanelle

Indirizzo: **https://fontanelle.entratadisicurezza.com/** (repository `pippotorre/fontanelle`).

## Impostazione una tantum (sul sito GitHub)
1. **Settings → Pages → Build and deployment → Source: «GitHub Actions»**.
2. **Settings → Pages → Custom domain:** `fontanelle.entratadisicurezza.com` → Save. Quando il controllo DNS è verde, spunta **Enforce HTTPS**. (Su Tophost il record DNS deve essere un `CNAME` da `fontanelle` a `pippotorre.github.io`.)
3. **Actions → «Pubblica il sito» → Run workflow** (la prima volta scarica anche i dati, può richiedere diversi minuti).
4. Apri `https://fontanelle.entratadisicurezza.com/` e controlla in fondo al pannello la riga della versione (`v… · data dei dati`).

## Come funziona
- A ogni push su `main` il workflow esegue le prove, prepara il sito (senza `test/`, `tools/`, `art/`, `store/`, `docs/`) e lo pubblica.
- Ogni lunedì e a richiesta, prima ricrea `data/t/` da OpenStreetMap (`tools/genera-tessere.mjs`) e lo salva nel repository. Se il download fallisce non cambia nulla: restano i dati precedenti.
- Di default copre tutta Italia (`35.4,6.6,47.2,18.9`, circa 150 richieste a Overpass: serve qualche decina di minuti). Per cambiare la zona modifica `BBOX` in `tools/genera-tessere.mjs` (sud,ovest,nord,est) o lancia lo script con un rettangolo: `node tools/genera-tessere.mjs 41,11,43,14`.

## Problemi comuni
| Sintomo | Causa e rimedio |
|---|---|
| Il workflow non parte o «Pages not enabled» | Manca il passo 1: Source deve essere «GitHub Actions». |
| «Domain's DNS record could not be retrieved» | Il CNAME su Tophost non è ancora propagato o punta a un nome sbagliato. |
| Il telefono mostra ancora la versione vecchia | Chiudi e riapri l'app: il service worker prende prima la rete e si aggiorna da solo. |
