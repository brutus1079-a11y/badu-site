# BADU SITE – pubblicazione su GitHub Pages

## 1. Crea il repository
1. github.com → **New repository**
2. Nome: `badu-site` (GitHub non accetta spazi; "BADU-SITE" funziona ma gli indirizzi sono più puliti in minuscolo)
3. **Public** (GitHub Pages gratuito funziona solo con repository pubblici)
4. Create repository

## 2. Carica i file
1. Nel repository vuoto: **uploading an existing file**
2. Trascina **il contenuto** della cartella `badu-site` (index.html, app.js, style.css, le cartelle img, fonts, umzugsreinigung-zuerich, …) – non la cartella stessa
3. Commit changes
   ⚠️ Il file `.nojekyll` è nascosto: se il tuo computer non lo mostra, crealo su GitHub con **Add file → Create new file**, nome `.nojekyll`, contenuto vuoto.

## 3. Attiva GitHub Pages
Settings → **Pages** → Source: **Deploy from a branch** → Branch: `main`, cartella `/ (root)` → Save.
Dopo 1–2 minuti il sito è online su `https://TUO-UTENTE.github.io/badu-site/`

## 4. Collega il dominio (quando il sito è controllato)
**In Hostpoint (DNS di badufacility.ch)** – modifica SOLO questi record:
| Tipo | Nome | Valore |
|---|---|---|
| A | badufacility.ch | 185.199.108.153 |
| A | badufacility.ch | 185.199.109.153 |
| A | badufacility.ch | 185.199.110.153 |
| A | badufacility.ch | 185.199.111.153 |
| CNAME | www | TUO-UTENTE.github.io |

Elimina il vecchio A `185.230.63.107` (Wix) e il CNAME `www → pointing.wixdns.net`.
⚠️ NON toccare i record MX (`mx1/mx2.mail.hostpoint.ch`) e TXT (SPF): servono per le email.

**In GitHub:** Settings → Pages → Custom domain: `www.badufacility.ch` → Save → dopo la verifica attiva **Enforce HTTPS**.

## 5. Da sapere
- I file `_redirects` e `_headers` funzionano solo su Cloudflare/Netlify: su GitHub vengono ignorati (i vecchi indirizzi Wix non vengono reindirizzati).
- Le condizioni di GitHub Pages non sono pensate per siti commerciali: se un giorno serve, lo stesso repository si collega in 2 minuti a Cloudflare Pages.
- Modulo: inserisci la chiave Web3Forms in `app.js` (cerca `WEB3FORMS_ACCESS_KEY`).

## 6. Farsi trovare da Google (dopo aver collegato il dominio)
1. **Google Search Console** – https://search.google.com/search-console
   - Aggiungi proprietà → tipo **Dominio** → `badufacility.ch`
   - Google ti dà un record **TXT**: inseriscilo nel DNS di Hostpoint (non tocca le email) → Verifica
   - Menu **Sitemap** → inserisci `sitemap.xml` → Invia
   - **Controllo URL** → incolla l'indirizzo della home e delle 4 pagine servizio → "Richiedi indicizzazione"
2. **Google Business Profile** – https://business.google.com
   - Indirizzo: **Badenerstrasse 865, 8048 Zürich** (uguale al sito), sito web `https://www.badufacility.ch`
   - Categorie: Impresa di pulizie, Servizio di pulizia per traslochi
3. **Bing Webmaster Tools** – https://www.bing.com/webmasters → "Importa da Google Search Console" (1 clic)
4. **Vecchio dominio badureinigung.ch** – reindirizzalo a `https://www.badufacility.ch` (301), così Google trasferisce il posizionamento
5. **Test** – https://search.google.com/test/rich-results : incolla una pagina servizio, devono comparire "Service", "Breadcrumb" e in home "FAQ"
