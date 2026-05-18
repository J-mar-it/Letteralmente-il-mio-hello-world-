# Shion Iburi — Clean Build Plan

Questo file nasce come riferimento per ricostruire la scheda in modo pulito, senza patch storiche, file test annidati o override accumulati.

## Versione ufficiale di partenza

CSS ufficiale consolidato:

```html
<style>@import url("https://cdn.jsdelivr.net/gh/J-mar-it/Letteralmente-il-mio-hello-world-@aeb5b7194c16c639591315529677325be6c5921e/shion-land-v83-direct-land.css?v=1");</style>
```

Commit ufficiale CSS:

```text
aeb5b7194c16c639591315529677325be6c5921e
```

HTML ufficiale di riferimento:

```text
branch: codex/shion-v83-screen2-gatebox-fix
file: index.html
```

## Obiettivo della clean build

Creare una copia nuova e separata della scheda, ricostruita con solo le parti funzionanti.

La clean build dovrà avere:

- un file HTML pulito;
- un file CSS pulito, oppure un blocco CSS unico se richiesto dalla land;
- nessun import a catena verso V60/V61/V83;
- nessun file test annidato;
- nessun override storico inutilizzato;
- meno `!important` possibile;
- classi coerenti e leggibili;
- sezioni ordinate e commentate.

## Non modificare la versione ufficiale

La versione ufficiale rimane congelata come base stabile.

Durante la clean build non bisogna toccare:

- `index.html` ufficiale, salvo richiesta esplicita;
- `shion-land-v83-direct-land.css` ufficiale;
- i file test già usati;
- gli import ufficiali già funzionanti.

La clean build deve essere creata in file nuovi.

## File clean consigliati

Prima fase:

```text
shion-clean.html
shion-clean.css
```

Oppure, se la land richiede un blocco unico:

```text
shion-clean-single.html
```

## Struttura pulita proposta

### 1. Root e stati

- `.shion-root`
- radio `flow-*`
- radio `side-tabs`
- radio `intro-info`
- radio `main-gate`

Da mantenere solo gli stati realmente usati.

### 2. Schermata 1 — Intro

Elementi da conservare:

- petali;
- card centrale;
- simbolo `毒`;
- player OST;
- titolo `SHION IBURI`;
- sottotitolo;
- frase medicina;
- warning finale;
- bottone medicina.

Da ripulire:

- overlay intro disattivati;
- vecchi fallback non più usati;
- regole duplicate su warning/glow.

### 3. Schermata 2 — Main

Elementi da conservare:

- background stanza;
- ritratto centrale;
- cornice;
- Diagnosis;
- frase centrale;
- tab laterali sinistri: Venom / Smoke / Mark;
- tab laterali destri: Property / Observe / Need;
- immagini decorative basse;
- gate-player;
- bottoni Entra / Allontanati.

Fix da incorporare in modo pulito:

- un solo gruppo radio `side-tabs`;
- un solo overlay laterale visibile alla volta;
- scope per lato: sinistra apre solo Venom/Smoke/Mark, destra solo Property/Observe/Need;
- testi pannelli laterali a 15.5px;
- gate-player definitivo con `translateY(8px)`;
- immagini decorative basse 86x132px.

### 4. Percorso yandere

Schermate da conservare:

- trap-1;
- trap-2;
- trap-3;
- trap-4;
- trap-5;
- trap-6;
- dead-screen;
- easy-screen;
- blackout-screen.

Fix da incorporare:

- testi yandere in alto al centro;
- pulsanti yandere centrati in basso;
- dead end centrato;
- easy way out a destra con delay 8s;
- easy-screen con background alzato di 44px;
- blackout finale persistente durante click;
- frase finale divisa in tre livelli:
  - `Mi appartieni ~` statico;
  - `Vivo o morto..` con pulsazione centrata;
  - `NON MI IMPORTA.` freddo/intermittente.

## Testi definitivi pannelli laterali

### Venom

```html
<div class="tab-panel venom-panel"><h3>Venom</h3><p>Non tutti i veleni servono a uccidere.<br>Alcuni insegnano al corpo a cercare<br>ancora la mano di chi<br>li ha somministrati.</p></div>
```

### Smoke

```html
<div class="tab-panel pulse-panel"><h3>Smoke</h3><p>Il fumo scivola tra i margini,<br>si posa dove nessuno guarda.<br>Lascia il dubbio<br>se sia sempre stato lì,<br>o no.</p></div>
```

### Mark

```html
<div class="tab-panel mark-panel"><h3>Mark</h3><p>Un marchio è come una firma<br>lasciata con cura.<br>Un punto scelto.<br>Un ritorno possibile.<br>Una proprietà non dichiarata.</p></div>
```

### Property

```html
<div class="tab-panel vapor-panel"><h3>Property</h3><p>Ciò che considera suo<br>non sempre porta un nome.<br><br>A volte è un oggetto.<br>A volte un luogo.<br>A volte una persona<br>che non lo sa ancora.</p></div>
```

### Observe

```html
<div class="tab-panel keepsake-panel"><h3>Observe</h3><p>Ogni gesto lascia una traccia.<br>Ogni paura,<br>ogni insicurezza,<br>ogni tremito.<br>Ogni crepa del tuo essere.</p></div>
```

### Need

```html
<div class="tab-panel need-panel"><h3>Need</h3><p>Il bisogno non nasce nell'immediato.<br>Non chiede molto.<br>Solo la presenza.<br>Poi il respiro<br>e poi tutto il resto.</p></div>
```

## Metodo di lavoro consigliato

1. Creare `shion-clean.html` copiando solo la struttura HTML finale funzionante.
2. Creare `shion-clean.css` senza import esterni verso vecchie versioni.
3. Ricostruire il CSS per sezioni, una schermata alla volta.
4. Testare ogni schermata prima di passare alla successiva.
5. Evitare correzioni cumulative non documentate.
6. Quando la clean build replica la versione ufficiale, congelarla come nuova base stabile.

## Priorità della clean build

Ordine consigliato:

1. Canvas/root e gestione schermate.
2. Intro.
3. Main screen.
4. Tab laterali.
5. Gate-player.
6. Yandere 1-6.
7. Dead screen.
8. Easy screen.
9. Blackout screen.
10. Cleanup finale.
