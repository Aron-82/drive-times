# Drive times

One static page: type one address, get the driving distance and time to every address on your saved list (up to ~200), nearest first.

## Privacy

- The list is stored **only in your browser** (`localStorage`). This repo and the page's host never see it.
- The address you type, and each list address the first time it is looked up, is sent to [OpenStreetMap Nominatim](https://nominatim.org/) to get coordinates.
- Coordinates (not addresses) are sent to a public [OSRM](https://project-osrm.org/) routing server.
- No account, no API key, no analytics, no cookies.

## CSV format

`name;address;lat;lon` — header optional (columns then default to that order, any order with a header).
Delimiter `;` `,` or tab is detected from the first line. Put addresses that contain commas in quotes, or use `;`.
`lat`/`lon` are optional; rows that have them skip the lookup. **Export CSV** includes coordinates, so a re-import is instant.
A single column is read as the address.

## Limits

- Times are typical free-flow estimates, **no live traffic**.
- Geocoding is 1 request per second (Nominatim policy): 200 new addresses take about 3.5 minutes, once.
- The public servers are free community services without an SLA.
- iPhone Safari may delete stored site data after about 7 days without a visit: keep an exported CSV.
- No address autocomplete (forbidden by the Nominatim usage policy).

## Data

Map data © OpenStreetMap contributors (ODbL). Geocoding: Nominatim. Routing: OSRM (`router.project-osrm.org`, fallback `routing.openstreetmap.de`).

## Changing the page

Edit `index.html` (HTML, CSS and JS in one file, no build step), commit, `git push`; GitHub Pages updates within a minute.
`test/landmarks.csv` holds public landmarks for testing.
