# Lab17 - Varnostna analiza spletne aplikacije

## Analiza domene lanuma.eu

**Uporabljena orodja:**
- Nmap za skeniranje odprtih portov
- OWASP ZAP za analizo varnostnih ranljivosti

**Najdeni odprti porti:**

```
80/tcp   - HTTP
443/tcp  - HTTPS
8080/tcp - HTTP-Proxy
8443/tcp - HTTPS-Alt
```

Domena ima odprtih več portov kot je običajno. Porti 8080 in 8443 so pogosto uporabljeni za testno okolje, kar lahko predstavlja varnostno tveganje v produkciji.

---

## Najdene varnostne ranljivosti

**Srednje tveganje:**

- **Cookie without SameSite Attribute** - piškotki dovzetni za CSRF napade
- **Content Security Policy (CSP) Header Not Set** - omogoča XSS napade
- **CSP: style-src unsafe-inline** - dovoljuje inline CSS, tveganje XSS
- **CSP: script-src unsafe-inline** - dovoljuje inline JavaScript, tveganje XSS
- **Sub Resource Integrity Missing** - zunanje datoteke lahko spremenjene
- **Absence of Anti-CSRF Tokens** - omogoča CSRF napade
- **Cross-Domain Misconfiguration** - napačna CORS konfiguracija
- **Cookie No HttpOnly Flag** - dostop do piškotkov preko JavaScript

**Nizko tveganje:**

- **CSP: Wildcard Directive** - uporablja * v CSP, zmanjšuje učinkovitost
- **Cross-Domain JavaScript Inclusion** - tveganje pri kompromitiranem CDN

---

## Priporočila za izboljšave

Večina ranljivosti je povezanih z manjkajočimi varnostnimi glavami in nepravilno konfiguracijo piškotkov. Najpomembnejše izboljšave:

- Dodaj CSP header z omejitvenimi direktivami
- Nastavi piškotke z `HttpOnly`, `Secure` in `SameSite=Strict` atributi
- Implementiraj CSRF tokene za vse obrazce
- Zapri porte 8080 in 8443, če niso potrebni
- Dodaj SRI za zunanje JavaScript in CSS datoteke
