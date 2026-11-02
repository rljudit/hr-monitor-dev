# HR monitor – fejlesztői változat

Ez a [rljudit/hr-monitor](https://github.com/rljudit/hr-monitor) kísérleti másolata. A keresők nem indexelik. Ami itt beválik, azt visszavezetjük az élő tárolóba.

A Sajtóművek HR-es AI sajtófigyelője: globális munkaerőpiaci hírek és HR-trendek magyar szűrővel, naponta frissítve.

Fejlesztői oldal: https://rljudit.github.io/hr-monitor-dev/  
Élő oldal: https://rljudit.github.io/hr-monitor/

## Felépítés

| Mappa / fájl | Mi ez |
| --- | --- |
| `data/articles.json` | Az összes hír és trend. Ezt bővíti minden reggel az automata frissítés. |
| `src/config.json` | Oldalnév, alcím, témák és színeik, ikonkészlet, impresszum adatai. |
| `src/style.css`, `src/app.js` | A megjelenés és a főoldal szűrői. |
| `src/og.png` | Megosztási kép (újragenerálás: `python3 src/make_og.py <Montserrat.ttf>`). |
| `build.py` | Statikus generátor: a fentiekből elkészíti a `docs/` mappát. |
| `docs/` | A kész weboldal, ezt szolgálja ki a GitHub Pages. Kézzel ne szerkeszd. |

## Frissítés kézzel

```
python3 build.py
git add -A && git commit -m "Frissítés" && git push
```

## Saját domain

A `src/config.json`-ban a `site.url` legyen az új cím, és add hozzá: `"domain": "hrmonitor.example.hu"`. A build ebből `docs/CNAME`-et ír; a DNS-ben egy CNAME rekord kell `rljudit.github.io` értékkel.

## Impresszum

A `src/config.json` → `site.impressum` mezői: `publisher`, `address`, `editor`, `host`. Ami hiányzik, az az oldalon „[kitöltendő]” jelöléssel jelenik meg.
