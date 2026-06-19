# whitebox-pro-adnetworks-meta

Meta as a self-contained WhiteBox ad-network: the canonical→Meta event map +
signal specs ([spec.js](src/spec.js)), the **Conversions API** server adapter
([index.js](src/index.js)), and the **Pixel** client mapper ([client.js](src/client.js)).
Composed into the conversions/audiences plugins.

```js
// server (CAPI) — fan-out leg
import { meta } from 'whitebox-pro-adnetworks-meta'
conversions({ networks: [ meta({ pixelId: '…', accessToken: '…' }) ] })

// client (window.fbq, loaded externally) — pixel leg
import { meta } from 'whitebox-pro-adnetworks-meta/client'
conversions({ networks: [ meta() ] })
```

Signals it collects/matches on: `_fbp`, `_fbc` (built from `fbclid`). Shares the
`event_id`/`eventID` with the pixel for CAPI dedup.
