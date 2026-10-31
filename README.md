# coming-soon

A single-file "coming soon" page for upcoming jay9874.in products. While visitors wait, it points them to the live products: [NREGA 2.0](https://nrega.jay9874.in) and [Musically](https://musically.jay9874.in).

## Pointing an upcoming product here

Redirect the product's domain to this page and pass the original host as `?from=`:

```
https://<coming-soon-host>/?from=newthing.jay9874.in
```

The page then:
- names the product in the headline ("Newthing is almost here.")
- shows the link the visitor was heading to
- counts visitors who are waiting for that product

`?product=`, `?ref=` and `?to=` work too. If there's no parameter, the page falls back to `document.referrer` when it comes from another `*.jay9874.in` subdomain. To give a product a proper display name, add it to `KNOWN` in `index.html`.

## Visitor counts

Counts use the free [Abacus](https://abacus.jasoncameron.dev) API under the `jay9874-coming-soon` namespace. Each browser is counted once per product.

| Key | Meaning |
| --- | --- |
| `waiting-<slug>` | visitors redirected from `<slug>.jay9874.in` |
| `waiting-home` | visitors with no product in the link |
| `explore-nrega`, `explore-musically` | visitors who clicked through to a live product |

Read a count:

```bash
curl https://abacus.jasoncameron.dev/get/jay9874-coming-soon/waiting-home
```

## Run locally

```bash
python3 -m http.server 8080
```
