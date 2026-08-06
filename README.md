# Persönlicher TRaSH-Guides Fork

> **Hinweis:** Dieses Projekt richtet sich an deutschsprachige Nutzer — die angepassten
> Quality-Profiles betreffen ausschließlich die **German**-Profile.

Dies ist ein **persönlicher Fork** von [TRaSH-Guides](https://trash-guides.info/), der die
Quality-Profiles etwas an meine eigenen Vorlieben anpasst und **hochwertige AV1-Encodes
zulässt**, statt sie zu bestrafen.

Der Fork ist auf die Custom-Format- und Quality-Profile-JSON-Daten unter
[`docs/json`](docs/json) reduziert, damit er direkt von einer Custom-Format-Sync-Anwendung
(Recyclarr, Clonarr, etc.) eingelesen werden kann.

## Was sich vom Upstream unterscheidet

- **AV1 ist erlaubt:** die negativen AV1-Scores wurden neutralisiert, sodass hochwertige
  AV1-Encodes nicht mehr blockiert werden.
- **Angepasste Quality-Profiles:** die German-Quality-Profiles wurden nach meinem Geschmack
  verschärft (z. B. wird 720p zugunsten von 1080p/2160p Bluray und WEB-DL fallengelassen).
  Diese sind mit `[lekl7]` präfixiert.
- **AV1-Groups Bad x265:** Gruppen, die gute AV1-Encodes, aber schlechte x265/HEVC-Encodes
  liefern (bisher WOTT), bekommen ihre h265-Encodes blockiert, während ihre AV1-Encodes weiter
  belohnt werden.
- **German HD Bluray + WEB (LQ):** ein Low-Quality-Geschwisterprofil des Standard-1080p-Profils,
  das kleine `German Microsized`-Releases aktiv bevorzugt (statt sie zu blockieren) und
  WEBRip-1080p als nicht bevorzugten Fallback erlaubt.
- **German Anime HD+UHD Bluray + WEB (nur Sonarr):** ein kombiniertes 1080p/2160p-Anime-Profil,
  das dem normalen Upgrade-Pfad bis UHD folgt, aber ein 2160p-Release nur dann greift, wenn es
  deutsche Tonspur hat — Nicht-deutsche UHD-Releases werden grundsätzlich blockiert.
- **German Remux HD/UHD:** ein reines Remux-Profil — kein WEBDL/WEBRip/Bluray-Fallback bei
  keiner Auflösung. Folgt dem normalen Upgrade-Pfad von Remux-1080p zu Remux-2160p, falls
  jemals ein deutsches 2160p-Remux auftaucht.
- **TSiNT:** auf Sonarr zu German Web Tier 02 hinzugefügt für ihre vollwertigen
  WEB-AVC-Releases, aber ihre WEB-HEVC-Encodes sind nah an Microsized-Qualität — ein neues
  `WEB-HEVC Microsized`-Custom-Format blockiert diese gezielt (während sie im LQ-Profil als
  bevorzugt bewertet werden, genau wie `German Microsized`). Auf Radarr zu German Bluray Tier 01
  hinzugefügt für ihre hochwertigen AV1-Movie-Encodes.
- **AV1-Gruppen-Whitelist:** da AV1 global entblockt ist, erzwingen zwei gekoppelte
  Custom-Formats eine strikte Kopplung zwischen AV1 und einer geprüften Gruppenliste:
  `AV1 Whitelist: Unlisted Group` blockiert jedes AV1-Release (auch gruppenlose) dessen Gruppe
  nicht freigegeben ist, und `AV1 Whitelist: Non-AV1 Release` blockiert Nicht-AV1-Releases einer
  freigegebenen Gruppe — sodass diese Gruppen nur noch als AV1 gegriffen werden. Aktuell ist nur
  `WOTT` freigegeben. Gilt für dieselben German-HD/UHD/LQ-Profile wie `AV1-Groups Bad x265`.

> **Hinweis:** Diese Änderungen wurden ausschließlich an den **German**-Profilen vorgenommen.
> Alle anderen Profile entsprechen unverändert dem Upstream-TRaSH-Guides.

Alles Weitere folgt der hervorragenden Arbeit des ursprünglichen TRaSH-Guides-Projekts.

## Credit

Alle zugrundeliegenden Custom Formats, Scorings und Profile-Designs stammen von
[TRaSH-Guides](https://trash-guides.info/), entwickelt in enger Zusammenarbeit mit den Radarr-
und Sonarr-Teams. Für Dokumentation bitte die offiziellen Guides konsultieren und das
Original-Projekt unterstützen.
