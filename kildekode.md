# Forvaltning av kildekode 

Kildekode til alle egenutviklede komponenter ligger åpent på [github](https://github.com/mong) med lisensen [GNU General Public License 3](https://www.gnu.org/licenses/gpl-3.0.en.html). 

I alle repositories er det én hovedgren: `master`. Denne grenen skal alltid være klar for å deployes til produksjon. Hver *commit* til `master` deployes til QA-miljø, som er identisk med produksjonsmiljø. Når en ny versjon lages i github, brukes [Semantic Versioning](https://semver.org/) for å navngi versjonen. Når en ny versjon lages, vil denne automatisk deployes til produksjon. 

Grenen `master` er i alle *repositories* beskyttet for direkte commits. Alle endringer må gjennom en *pull request* for å komme inn i `master`. For at kode skal komme inn i `master` må ingen av testene feile og koden må gjennom en *code review* av ett av medlemmene på https://github.com/mong. 

[Medlemmer av *mong* på github](https://github.com/orgs/mong/people) må ha aktivert to-faktor-autentisering (2FA) for å kunne bli og være medlem, og dette er et krav som er satt i instillingene på github. Kun medlemmer av gruppen kan dytte opp endringer direkte til en branch på https://github.com/mong. Unntaket er `master` branchen, der kun administratorene kan dytte opp endringer direkte.  Det er kun to av medlemmene som har administratorrettigheter (Are og Arnfinn). Andre, som ikke er medlemmer av *mong*, må lage en fork av koden og foreslå endringer til master gjennom denne forken. 

## Repositories aktivt i bruk

- [qmongjs](https://github.com/mong/qmongjs): Selve nettsiden (front-end) skrevet i javascript/typescript og bruker React.

- [mong-api](https://github.com/mong/mong-api): API for kommunikasjon mellom nettside og database.

- [imongr](https://github.com/mong/imongr): Koden bak nettside for å legge inn data til databasen. Kodet i R og Shiny. Leveres i et docker image som brukes av EC2-instanser på AWS.

- [lb-rp](https://github.com/mong/lb-rp): Lastbalanserer og reverse proxy, basert på NGINX og levert som et docker image, som står foran shinyproxy.

- [shinyproxy](https://github.com/mong/shinyproxy). Levert som docker image. Kjører shinyproxy (https://www.shinyproxy.io/) for å serve shiny-appen imongr.

- [db](https://github.com/mong/db) 

- [imongr-base-r](https://github.com/mong/imongr-base-r): Docker image som brukes av imongr docker image. Inneholder nødvendige R-pakker, som brukes av imongr. Dette gjør det kjappere å bygge imongr sitt docker image.

## Aktive repositories som skal ut av produksjon

- [qmongr](https://github.com/mong/qmongr) og [qmongr-base-r](https://github.com/mong/qmongr-base-r): Shiny-applikasjonen bak https://skde-resultater.no/. Denne skal erstattes av qmongjs. 

- [tmongr](https://github.com/mong/tmongr) og [tmongr-base-r](https://github.com/mong/tmongr-base-r): Shiny-applikasjonen bak tabellverket. Skal på sikt bakes inn i qmongjs.

## Eksterne komponenter

Koden [qmongjs](https://github.com/mong/qmongjs) er avhengig av følgende [eksterne bibliotek](https://github.com/mong/qmongjs/network/dependencies): 

- [TypeScript](https://github.com/microsoft/TypeScript). Store deler av koden er skrevet i Typescript, for å redusere sannsynligheten for bugs. Utviklet og utvikles av Microsoft og ekstremt utbredt. 
- [React](https://github.com/facebook/react). qmongjs er en React-app. Utviklet og utvikles av Facebook og ekstremt utbredt. 
- [Sentry](https://github.com/getsentry/sentry-javascript) for automatisk rapportering av feil som oppstår under bruk av nettside.  
- [D3](https://github.com/d3/d3) for visualisering/figurer.  
- [query-string](https://github.com/sindresorhus/query-string) 
- [react-query](https://github.com/tannerlinsley/react-query) 
- ...