# Personal TRaSH-Guides Fork

This is a **personal fork** of [TRaSH-Guides](https://trash-guides.info/) that tweaks the
quality profiles a bit to match my own preferences, and **allows high-quality AV1 encodes**
instead of penalizing them.

It is stripped down to just the custom format and quality profile JSON data under
[`docs/json`](docs/json), so it can be consumed directly by a custom format sync application
(Recyclarr, Clonarr, etc.).

## What's different from upstream

- **AV1 is allowed:** the negative AV1 scores have been neutralized, so high-quality AV1
  encodes are no longer blocked.
- **Adjusted quality profiles:** the German quality profiles have been tightened to my taste
  (for example, dropping 720p in favor of 1080p/2160p Bluray and WEB-DL). These are prefixed
  with `[lekl7]`.
- **AV1-Groups Bad x265:** groups that make good AV1 encodes but bad x265/HEVC ones (starting
  with WOTT) have their h265 encodes blocked while their AV1 encodes stay rewarded.
- **German HD Bluray + WEB (LQ):** a low-quality sibling of the standard 1080p profile that
  actively prefers small `German Microsized` releases over full-size ones (instead of
  blocking them) and allows WEBRip-1080p as a non-preferred fallback.
- **German Anime HD+UHD Bluray + WEB (Sonarr only):** a combined 1080p/2160p anime profile
  that follows the normal upgrade path all the way to UHD, but only ever grabs a 2160p release
  if it has German audio — non-German UHD releases are blocked outright.
- **German Remux HD/UHD:** a Remux-only profile — no WEBDL/WEBRip/Bluray fallback at any
  resolution. Follows the normal upgrade path from Remux-1080p to Remux-2160p in case a German
  2160p Remux ever shows up.
- **TSiNT:** on Sonarr, added to German Web Tier 02 for their full-size WEB-AVC releases, but
  their WEB-HEVC encodes are close to microsized quality — a new `WEB-HEVC Microsized` custom
  format blocks those specifically (while scoring them as preferred in the LQ profile, same as
  `German Microsized`). On Radarr, added to German Bluray Tier 01 for their high-quality AV1
  movie encodes.

> **Note:** These changes were only made to the **German** profiles. All other profiles are
> left as they are in upstream TRaSH-Guides.

Everything else follows the excellent work of the original TRaSH-Guides project.

## Credit

All of the underlying custom formats, scoring, and profile design come from
[TRaSH-Guides](https://trash-guides.info/), developed in close collaboration with the Radarr
and Sonarr teams. Please refer to the official guides for documentation, and support the
original project.
