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
  WEBRip-1080p als nicht bevorzugten Fallback erlaubt. Dual-Audio-Releases (deutsche Synchro +
  Originalspur) werden hier bewusst **nicht** belohnt (`German DL` und `German 1080p Booster`
  fehlen absichtlich) — kleine Releases sind fast immer German-only, Dual-Audio würde dem
  Zweck des Profils widersprechen. `German Microsized` ist mit `+7000` bewertet — hoch genug,
  dass eine kleine Gruppe wie FuN oder w00t jedes noch so vollständig ausgestattete Bluray-
  oder Web-Tier-01-Release schlägt, selbst wenn dieses zusätzlich IMAX, HDR und verlustfreies
  Audio mitbringt.
- **German Anime HD+UHD Bluray + WEB (nur Sonarr):** ein kombiniertes 1080p/2160p-Anime-Profil,
  das dem normalen Upgrade-Pfad bis UHD folgt, aber ein 2160p-Release nur dann greift, wenn es
  deutsche Tonspur hat — Nicht-deutsche UHD-Releases werden grundsätzlich blockiert.
- **German Remux HD/UHD:** ein reines Remux-Profil — kein WEBDL/WEBRip/Bluray-Fallback bei
  keiner Auflösung. Folgt dem normalen Upgrade-Pfad von Remux-1080p zu Remux-2160p, falls
  jemals ein deutsches 2160p-Remux auftaucht.
- **WOTT, alyh, TzP in German Bluray Tier 02:** diese Gruppen liefern gute Encodes (egal ob
  AV1 oder x265/HEVC) und sind ganz normal als Tier-02-Gruppen gelistet — keine
  Sonderbehandlung, kein Blocking.
- **Audio-Codec-Belohnung:** AC3 (`DD`) und EAC3 (`DD+`) werden im 1080p- und 1080p-LQ-Profil
  standardmäßig belohnt, dazu ein kleiner Bonus für 5.1 Surround. Im 2160p-Profil wird DTS
  belohnt, dazu ein kleiner Bonus für 7.1 Surround.
- **IMAX-Belohnung (nur Radarr):** `IMAX` und `IMAX Enhanced` sind im 1080p-, 1080p-LQ- und
  2160p-Profil aktiv.
- **HDR-Belohnung:** `HDR` und `HDR10+ Boost` sind im 1080p-, 1080p-LQ- und 2160p-Profil aktiv
  (reiner Bonus, kein Blocking). `DV (w/o HDR fallback)` blockiert Dolby-Vision-Releases ohne
  HDR10-Fallback in denselben drei Profilen. Reines SDR-2160p wird nicht blockiert.

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
