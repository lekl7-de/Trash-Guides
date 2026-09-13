# Persönlicher TRaSH-Guides Fork

> **Note (EN):** This is a personal, German-language fork of TRaSH-Guides. It's tailored to a
> single owner's preferences and is not intended for general use — see
> [TRaSH-Guides](https://trash-guides.info/) for the original, actively maintained project.

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
- **German HD Bluray + WEB (LQ):** ein Low-Quality-Geschwisterprofil des Standard-1080p-Profils,
  das kleine `German Microsized`-Releases aktiv bevorzugt (statt sie zu blockieren) und
  WEBRip-1080p als nicht bevorzugten Fallback erlaubt. Der spezielle Dual-Audio-Zusatzbonus
  (`German 1080p Booster`, `+650` nur für German+Original-Language-Releases) fehlt hier
  absichtlich, die reguläre Sprachwertung (`German DL`, gleichwertig zu `German DL
  (undefined)`) bleibt aber erhalten, damit bestätigte Dual-Audio-Releases nicht auf 0 Punkte
  fallen. `German Microsized` ist mit `+8000` bewertet — hoch genug, dass eine kleine Gruppe
  wie FuN, w00t oder dAV1nci jedes noch so vollständig ausgestattete Bluray- oder Web-Tier-01-
  Release schlägt, selbst mit Dual-Audio, IMAX, HDR und verlustfreiem Audio.
- **German Anime HD+UHD Bluray + WEB (nur Sonarr):** ein kombiniertes 1080p/2160p-Anime-Profil,
  das dem normalen Upgrade-Pfad bis UHD folgt, aber ein 2160p-Release nur dann greift, wenn es
  deutsche Tonspur hat — Nicht-deutsche UHD-Releases werden grundsätzlich blockiert.
- **German Remux HD/UHD:** ein reines Remux-Profil — kein WEBDL/WEBRip/Bluray-Fallback bei
  keiner Auflösung. Folgt dem normalen Upgrade-Pfad von Remux-1080p zu Remux-2160p, falls
  jemals ein deutsches 2160p-Remux auftaucht.
- **WOTT und POSEIDON nur als AV1-Encode bevorzugt (`German AV1 Groups`):** beide Gruppen
  stehen nicht mehr in `German Bluray Tier 02` (`alyh` und `TzP` wurden dort ebenfalls
  entfernt und sind jetzt schlicht ungelistet). Stattdessen matcht ein eigener CF nur, wenn
  die Gruppe WOTT oder POSEIDON ist **und** `AV1` im Release-Titel steht, und vergibt `+3000`
  — knapp über `German Bluray Tier 01` (2900), sodass ein AV1-Encode dieser Gruppen bei sonst
  gleichem Release jede Tier-Gruppe schlägt. x265/HEVC-Releases von WOTT/POSEIDON bekommen
  dadurch keinen Tier-Score mehr (nicht geblockt, nur unbewertet wie jede ungelistete Gruppe). Aktiv in den 1080p-, 1080p-LQ-, 2160p- und
  UHD-Alternative-Profilen beider Apps; Remux- und Anime-Profil nutzen keine Bluray-Tiers und
  bleiben unberührt.
- **Audio-Codec-Belohnung:** AC3 (`DD`) und EAC3 (`DD+`) werden im 1080p-Profil standardmäßig
  **gleich hoch** belohnt (ein reines AC3-Release verliert also nicht mehr gegenüber einem sonst
  identischen EAC3-Release), dazu ein kleiner Bonus für 5.1 Surround. Im 1080p-LQ-Profil bleibt
  die ursprüngliche Upstream-Gewichtung (EAC3 höher als AC3) bestehen. Im 2160p-Profil wird DTS
  belohnt, dazu ein kleiner Bonus für 7.1 Surround. Im 1080p-LQ-Profil zusätzlich AAC, mit
  demselben Score wie AC3.
- **IMAX-Belohnung (nur Radarr):** `IMAX` und `IMAX Enhanced` sind im 1080p-, 1080p-LQ- und
  2160p-Profil aktiv.
- **HDR-Belohnung:** `HDR` und `HDR10+ Boost` sind im 1080p-, 1080p-LQ- und 2160p-Profil aktiv
  (reiner Bonus, kein Blocking). `DV (w/o HDR fallback)` blockiert Dolby-Vision-Releases ohne
  HDR10-Fallback in denselben drei Profilen. Reines SDR-2160p wird nicht blockiert.
- **HDR schlägt die Tier-Lücke (Radarr + Sonarr):** Gewünschte Reihenfolge bei sonst gleichem
  Release: HDR Bluray > HDR Web > SDR Bluray > SDR Web. Ein Web-Release soll nur dann gewinnen,
  wenn es HDR hat und kein HDR-Bluray existiert; bei SDR gewinnt immer Bluray. Da die Web-Tiers
  im Upstream bereits alle unter den Bluray-Tiers liegen, reichte es, den `HDR`-Bonus im
  `german`-Score-Set von 500 auf 1500 anzuheben, damit er die größte Bluray-vs-Web-Tier-Lücke
  (1100) plus kleine Zusatzboni sicher überbietet. Gilt im 1080p- und 2160p-Profil beider
  Apps; das LQ-Profil bleibt bei 500, das Anime-Profil ist nicht betroffen, IMAX-Bluray-
  Releases behalten bei Radarr ihren Vorsprung. Die frühere Sonarr-Angleichung der
  `German Web Tier 01/02/03` auf Bluray-Niveau wurde dafür wieder zurückgenommen (Upstream-
  Werte), weil sie der Regel "SDR Bluray schlägt SDR Web" widersprach.
- **Movie-Version-Belohnung (nur Radarr):** `Special Edition` (deckt Director's Cut, Extended,
  Unrated, Uncut u. ä. per Regex ab), `4K Remaster`, `Criterion Collection`, `Hybrid`,
  `Masters of Cinema`, `Open Matte`, `Remaster` und `Vinegar Syndrome` sind in allen
  German-Profilen aktiv (1080p, 1080p LQ, 2160p, UHD Alternative, Remux HD/UHD). `Hybrid` und
  `Remaster` sind zusätzlich auch bei Sonarr aktiv (inkl. Anime HD+UHD) — die restlichen CFs
  gibt es dort nicht (reine Film-Konzepte).

- **Fix (Fork-eigener Bug): `German Web Tier 01/02/03` matchten gar nicht mehr:** ein
  früherer Fork-Commit hatte die `WebDL`/`WebRip`-Source-Specs dieser CFs auf `required: true`
  gesetzt, in der Annahme, sonst würde ein Bluray-Release fälschlich als WEB-Tier gewertet.
  Radarr/Sonarr prüfen Specs aber pro Typ-Gruppe, und eine Gruppe fällt durch, sobald eine
  required-Spec darin nicht zutrifft — ein Release hat nur eine Quelle, also war immer eine der
  beiden required-Specs falsch und die Web-Tiers griffen bei keinem Release. Zurückgesetzt auf
  den Upstream-Stand (`required: false`), der korrekt ist.
- **Fix: unerwünschte Formate wurden nicht zuverlässig geblockt:** CFs wie `Upscaled`,
  `Obfuscated`, `BR-DISK`, `Extras`, `3D`, `Retags`, `No-RlsGroup` u. a. waren zwar über die
  Guide-Gruppe „Unwanted Formats German" dokumentiert, aber in keinem `[lekl7]`-Profil tatsächlich
  scharf geschaltet. Sind jetzt direkt in allen aktiven German-Profilen (1080p, 1080p LQ, 2160p,
  UHD Alternative, Remux HD/UHD, Anime HD+UHD) verdrahtet und werden zuverlässig bestraft
  (`German Microsized` bleibt dabei im LQ-Profil weiterhin bevorzugt, überall sonst geblockt).
- **x266 (H.266/VVC) und VC-1 geblockt:** beide Video-Codecs werden in allen aktiven
  German-Profilen (1080p, 1080p LQ, 2160p, UHD Alternative, Remux HD/UHD; bei Sonarr zusätzlich
  Anime HD+UHD) mit `-35000` in den Score-Sets `german`, `german-anime` und `german-microsized`
  bestraft — bei `minFormatScore: 0` bedeutet das ein hartes Reject, damit solche Releases gar
  nicht erst gegriffen werden. `VC-1` hatte zuvor gar keinen Score, `x266` nur `default:
  -10000`; der `default`-Score bleibt unverändert (nicht-German-Profile sind nicht betroffen).
  Die reinen `[German] HD/UHD Remux + WEB`-Upstream-Profile sind bewusst nicht einbezogen
  (gleiche Abgrenzung wie bei den übrigen Unwanted-Formats).

> **Hinweis:** Diese Änderungen wurden ausschließlich an den **German**-Profilen vorgenommen.
> Alle anderen Profile entsprechen unverändert dem Upstream-TRaSH-Guides.

Alles Weitere folgt der hervorragenden Arbeit des ursprünglichen TRaSH-Guides-Projekts.

## Credit

Alle zugrundeliegenden Custom Formats, Scorings und Profile-Designs stammen von
[TRaSH-Guides](https://trash-guides.info/), entwickelt in enger Zusammenarbeit mit den Radarr-
und Sonarr-Teams. Für Dokumentation bitte die offiziellen Guides konsultieren und das
Original-Projekt unterstützen.

---

*Dieses Repository wird mit Unterstützung von [Claude](https://claude.com) (Anthropic) gepflegt.*
