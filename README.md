# Parrocchia S. Bartolomeo — Formigine

Sito web one-page per la Parrocchia di S. Bartolomeo a Formigine (MO). Landing page moderna che presenta la parrocchia, gli orari delle messe, le news, la vita comunitaria e i canali di contatto/donazione.

**Demo:** apri [`index.html`](./index.html) in un browser, oppure servilo con un web server statico (vedi [Avvio locale](#avvio-locale)).

## Panoramica tecnica

Progetto **statico**, a file singolo: nessun framework, nessuna build, nessuna dipendenza da installare (`npm install` non serve).

| | |
|---|---|
| Markup | HTML5 semantico, un unico file (`demo.html`) |
| Stile | CSS puro, inline in `<style>`, con custom properties (`:root`) per la palette colori |
| Interattività | JavaScript vanilla (IIFE), inline in `<script>` |
| Carousel | [Swiper.js 11](https://swiperjs.com/) via CDN (jsDelivr) — nessuna installazione richiesta |
| Font | Google Fonts: **Fraunces** (titoli, serif) + **Source Sans 3** (testo, sans-serif) |
| Icone | SVG inline disegnate a mano (nessuna libreria di icone) |

## Struttura del progetto

```
site/
├── demo.html              # l'intero sito: markup + CSS + JS
├── assets/
│   ├── img/
│   │   ├── home_hero_01.jpeg      # foto di sfondo della hero (facciata della chiesa)
│   │   └── chiesa_conventino.jpg  # foto del Conventino (sezione restauro)
│   ├── css/                       # vuota — CSS interamente inline in demo.html
│   └── js/                        # vuota — JS interamente inline in demo.html
└── README.md
```

## Avvio locale

Essendo statico, basta un qualsiasi web server. Esempi:

```bash
# Python
python3 -m http.server 8000
# poi apri http://localhost:8000/demo.html

# Node (se hai npx disponibile)
npx serve .
```

Aprire direttamente `demo.html` col doppio click funziona quasi ovunque, ma è consigliato passare da un server locale per evitare limitazioni del browser sui percorsi relativi.

## Sezioni della pagina

1. **Header** — logo, menu desktop con dropdown, pulsante "Dona ora", hamburger per mobile.
2. **Hero** — carousel a 3 slide con dissolvenza incrociata (Swiper, `effect: fade`), autoplay, frecce e paginazione a pallini. Testo sempre allineato a sinistra, centrato verticalmente nella slide.
3. **Quick links** — 6 collegamenti rapidi (Calendario, Orari Messe, Sacramenti, Catechesi, Gruppi, Contatti). Sovrapposti a metà (+ offset extra) sul bordo inferiore della hero. Su mobile diventano un carousel (1 alla volta, frecce); da 980px in su tornano una riga statica di 6.
4. **Orari delle Messe** — tabella orari settimanali + card di download del "foglietto della settimana".
5. **Ultime novità** — carousel di news (3 visibili da 980px in su con frecce, 1 centrata su mobile).
6. **Vita comunitaria** — griglia a 4 card (Catechesi, Giovani, Carità, Comunità).
7. **Restauro** — banner a due colonne per la raccolta fondi sul restauro del Conventino.
8. **Newsletter** — form di iscrizione (solo front-end, nessun backend collegato).
9. **Footer** — contatti, link utili, Oratorio Don Bosco, social, torna-su.

### Menu mobile

Sotto i 980px l'header mostra un hamburger che apre un pannello **a schermo intero**, con animazione di ingresso da destra verso sinistra, sfondo navy, voci del menu con ingresso "a cascata" e sottomenu ad accordion. Chiusura con la X, con `Esc` o cliccando un link.

## Breakpoint responsive

| Breakpoint | Comportamento |
|---|---|
| `≥ 980px` | Navigazione desktop con dropdown; quick links e novità mostrano più elementi in riga con frecce (novità) o senza carousel (quick links) |
| `< 980px` | Navigazione sostituita dall'hamburger a schermo intero; quick links e novità diventano carousel a 1 elemento centrato |
| `< 640px` | Rifiniture di spaziatura/padding per schermi piccoli |

## Palette colori

Definita tramite custom properties in `:root`, in cima al CSS:

```css
--cream:  #F6F1E7   /* sfondo pagina */
--paper:  #FCFAF5   /* sfondo card/pannelli */
--ink:    #2A2119   /* testo principale */
--brick:  #A6462B   /* accento primario (icone, link attivi) */
--ochre:  #C6872F   /* accento secondario (bottoni CTA) */
--navy:   #1C2740   /* hero, footer, menu mobile */
```

Per cambiare la palette basta modificare questi valori: si propagano automaticamente a tutto il sito.

## Personalizzazione dei contenuti

Tutti i contenuti (testi, orari, link, immagini) sono scritti direttamente nell'HTML — non c'è un CMS o un file dati separato. Per aggiornarli, cercare la sezione corrispondente in `demo.html` (i commenti `<!-- ============ NOME SEZIONE ============ -->` aiutano a orientarsi) e modificare il markup.

## Da completare prima della messa online

- [ ] Sostituire i link segnaposto (`href="#"`) con gli URL reali: social (Facebook/Instagram/YouTube), pagina "Il parroco", documenti, calendario liturgico, Privacy/Cookie policy.
- [ ] Collegare il form newsletter a un servizio reale (attualmente mostra solo un messaggio di conferma via JS, senza inviare nulla).
- [ ] Caricare i PDF reali del "foglietto della settimana" al posto delle card segnaposto.
- [ ] Aggiungere altre foto per la hero (attualmente le 3 slide riusano la stessa immagine).
- [ ] Verificare/aggiornare orari messe, indirizzo, telefono ed email nel footer.

## Licenza

Da definire in base alle esigenze della parrocchia (es. contenuti testuali e foto potrebbero avere diritti diversi dal codice).
