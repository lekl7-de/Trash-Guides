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
- **Adjusted quality profiles:** some German quality profiles have been tightened to my taste
  (for example, dropping 720p and WEBRip in favor of 1080p/2160p Bluray and WEB-DL). These
  are prefixed with `[lekl7]`.

> **Note:** These changes were only made to the **German** profiles. All other profiles are
> left as they are in upstream TRaSH-Guides.

Everything else follows the excellent work of the original TRaSH-Guides project.

## Credit

All of the underlying custom formats, scoring, and profile design come from
[TRaSH-Guides](https://trash-guides.info/), developed in close collaboration with the Radarr
and Sonarr teams. Please refer to the official guides for documentation, and support the
original project.
