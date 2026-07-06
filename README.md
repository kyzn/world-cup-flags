# World Cup Flags

Square PNG flag images for football bots, scoreboards, Slack app icons, and other small UI surfaces that need national-team flags by stable filename.

The repository covers every senior men's national-team association in the six football confederations. Files are 1280 x 1280 PNGs with a white square background and a thin black border so they remain visible in tiny Slack/avatar contexts.

## Coverage

| Confederation | Region represented | Teams |
|---|---|---:|
| UEFA | Europe | 55 |
| CAF | Africa | 54 |
| AFC | Asia plus Australia | 47 |
| CONCACAF | North America, Central America, and the Caribbean | 41 |
| OFC | Oceania | 11 |
| CONMEBOL | South America | 10 |

Total coverage: **218 football teams**.

## Previews

### UEFA

![UEFA preview](previews/uefa.png)

Order:

```text
al     ad     am     at     az     by     be     ba     bg     hr     cy     cz     dk     gb-eng
ee     fo     fi     fr     ge     de     gi     gr     hu     is     il     it     kz     xk
lv     li     lt     lu     mt     md     me     nl     mk     gb-nir no     pl     pt     ie
ro     ru     sm     gb-sct rs     sk     si     es     se     ch     tr     ua     gb-wls
```

### CAF

![CAF preview](previews/caf.png)

Order:

```text
dz     ao     bj     bw     bf     bi     cm     cv     cf     td     km     cg     cd     ci
dj     eg     gq     er     sz     et     ga     gm     gh     gn     gw     ke     ls     lr
ly     mg     mw     ml     mr     mu     ma     mz     na     ne     ng     rw     st     sn
sc     sl     so     za     ss     sd     tz     tg     tn     ug     zm     zw
```

### AFC

![AFC preview](previews/afc.png)

Order:

```text
af     au     bh     bd     bt     bn     kh     cn     gu     hk     in     id     ir     iq
jp     jo     kp     kr     kw     kg     la     lb     mo     my     mv     mn     mm     mp
np     om     pk     ps     ph     qa     sa     sg     lk     sy     tw     tj     th     tl
tm     ae     uz     vn     ye
```

### CONCACAF

![CONCACAF preview](previews/concacaf.png)

Order:

```text
ai     ag     aw     bs     bb     bz     bm     bq     vg     ca     ky     cr     cu     cw
dm     do     sv     gf     gd     gp     gt     gy     ht     hn     jm     mq     mx     ms
ni     pa     pr     kn     lc     mf     vc     sx     sr     tt     tc     us     vi
```

### OFC

![OFC preview](previews/ofc.png)

Order:

```text
as     ck     fj     nc     nz     pg     ws     sb     pf     to     vu
```

### CONMEBOL

![CONMEBOL preview](previews/conmebol.png)

Order:

```text
ar     bo     br     cl     co     ec     py     pe     uy     ve
```

## Usage

Use the raw GitHub URL for a flag image:

```text
https://raw.githubusercontent.com/kyzn/world-cup-flags/main/{code}.png
```

Examples:

```text
https://raw.githubusercontent.com/kyzn/world-cup-flags/main/jp.png
https://raw.githubusercontent.com/kyzn/world-cup-flags/main/gb-eng.png
https://raw.githubusercontent.com/kyzn/world-cup-flags/main/pf.png
```

In Python:

```python
def flag_url(code: str) -> str:
    return f"https://raw.githubusercontent.com/kyzn/world-cup-flags/main/{code}.png"
```

## Filename Standard

Most filenames use the lowercase [ISO 3166-1 alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country or territory code:

```text
ar.png  Argentina
jp.png  Japan
ma.png  Morocco
za.png  South Africa
```

When football uses a distinct association identity or a common team name that does not map cleanly to a sovereign-state name, the filename still follows the flag/territory code used for that team.

### UK Home Nations

The UK home nations are separate football associations, so they use explicit subdivision-style slugs:

```text
gb-eng.png  England
gb-nir.png  Northern Ireland
gb-sct.png  Scotland
gb-wls.png  Wales
```

### Common Football Aliases

These are common team-name aliases and the file they should use:

| Team name / alias | File |
|---|---|
| Cape Verde, Cabo Verde, Cape Verde Islands | `cv.png` |
| Congo, Congo-Brazzaville, Republic of the Congo | `cg.png` |
| Curacao, Curaçao | `cw.png` |
| DR Congo, Congo DR, Democratic Republic of the Congo | `cd.png` |
| Eswatini, Swaziland | `sz.png` |
| Ivory Coast, Côte d'Ivoire, Cote d'Ivoire | `ci.png` |
| North Korea, Korea DPR, DPR Korea | `kp.png` |
| South Korea, Korea Republic, Republic of Korea | `kr.png` |
| Tahiti, French Polynesia | `pf.png` |
| Timor-Leste, East Timor | `tl.png` |
| Türkiye, Turkiye, Turkey | `tr.png` |
| United States, USA | `us.png` |

### Football-Specific Edge Cases

- **Afghanistan** uses the black-red-green tricolor commonly used for international sporting representation.
- **Bonaire** uses `bq.png`.
- **Chinese Taipei** uses `tw.png`.
- **Kosovo** uses `xk.png`.
- **Northern Ireland** uses `gb-nir.png`.
- **Northern Mariana Islands** uses `mp.png`.
- **Palestine** uses `ps.png`.
- **Saint Martin** uses `mf.png`; **Sint Maarten** uses `sx.png`.
- **Tahiti** uses `pf.png`, because the flag asset is French Polynesia.

## Adding Or Regenerating Images

The house style is:

1. Render the source SVG to a large PNG.
2. Resize it inside a 1280 x 1280 square.
3. Add a thin black border around the flag.
4. Center it on a white background.

Equivalent ImageMagick shape:

```sh
magick raw.png \
  -resize 1186x1186 \
  -bordercolor black -border 7 \
  -background white -gravity center -extent 1280x1280 \
  code.png
```

The result should be easy to read as a Slack app icon, reaction-adjacent image, or compact scoreboard asset.
