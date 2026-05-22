# Google Search Console — Setup

Schritt-für-Schritt-Anleitung, um die CrushIt-Landingpage bei Google
indexieren zu lassen.

---

## 1. Property hinzufügen

1. Öffne <https://search.google.com/search-console>
2. Klick **„Property hinzufügen"** → wähle **„URL-Präfix"**
3. Gib die volle URL ein: `https://crushitapp.vercel.app/`
4. **Weiter** klicken.

## 2. Verifizierung (HTML-Tag-Methode)

Google bietet mehrere Verifizierungswege — am einfachsten ist das **HTML-Tag**:

1. Google zeigt dir einen Meta-Tag, etwa:
   ```html
   <meta name="google-site-verification" content="dEr-Zeichen-string-hier" />
   ```
2. Diesen Tag in `index.html` einfügen — direkt nach dem `<title>`-Tag
   (oder irgendwo im `<head>`).
3. Committe + push:
   ```bash
   cd ~/Developer/crushit-landing
   git add index.html
   git commit -m "chore: Google Search Console Verifizierung"
   git push origin main
   ```
4. Warte ~30 Sekunden, bis Vercel automatisch deployed hat.
5. Zurück zu Search Console → **„Verifizieren"** klicken.

> ✅ Wenn Verifizierung erfolgreich: bekommst du Zugriff aufs Dashboard.

## 3. Sitemap einreichen

1. Linke Sidebar → **„Sitemaps"**
2. Im Eingabefeld: `sitemap.xml` (oder volle URL)
3. **„Senden"** klicken
4. Status sollte nach wenigen Minuten auf **„Erfolg"** wechseln. Sonst
   prüfen: <https://crushitapp.vercel.app/sitemap.xml> direkt im Browser
   öffnen — muss XML zurückgeben.

## 4. URL-Prüfung (sofortige Indexierung beantragen)

1. Oben in der Suchleiste die Haupt-URL eingeben: `https://crushitapp.vercel.app/`
2. Google prüft die URL (dauert ~30 Sekunden).
3. Falls **„URL ist nicht in Google"**: **„Indexierung beantragen"** klicken.
4. Wiederhole für die wichtigen Sektionen (optional):
   - `https://crushitapp.vercel.app/#datenschutz`
   - `https://crushitapp.vercel.app/#agb`
   - `https://crushitapp.vercel.app/#impressum`

> Hinweis: Indexierung kann **mehrere Tage** dauern — auch nach
> erfolgter Anfrage.

## 5. Rich-Result-Test (optional, aber empfohlen)

Prüfe ob deine Structured-Data (MobileApplication + AggregateRating)
korrekt geparst wird:

1. <https://search.google.com/test/rich-results>
2. URL eingeben → **„URL testen"**
3. Bei Erfolg: „CrushIt" wird als **Mobile App** erkannt; Sterne-Rating
   und Free-Offer sind sichtbar.

## 6. Performance + Core Web Vitals beobachten

Nach ein paar Tagen siehst du in Search Console unter **„Leistung"**:
- Impressionen (wie oft warst du in Suchergebnissen)
- Klicks
- Durchschnittliche Position
- Top-Keywords

Unter **„Core Web Vitals"** prüft Google ob die Seite mobil/desktop schnell
genug ist. Aktueller Stand sollte „Gut" sein, da:
- Statisches HTML (kein JS-Framework)
- Inline CSS (kein render-blocker)
- Nur Google Fonts als externe Resource
- Lazy-Load wo möglich

---

## 7. Domain-Upgrade (langfristig)

`crushitapp.vercel.app` ist eine **Subdomain**. Für besseres SEO und
Branding später eine eigene Domain registrieren — z.B.:

- `crushit.app` (~50 €/Jahr bei Namecheap)
- `crushitapp.com` (~12 €/Jahr)
- `crushit.de` (~6 €/Jahr bei einer DE-Registrar)

In Vercel: **Project Settings → Domains → Domain hinzufügen** → DNS-
Records beim Registrar setzen wie von Vercel angezeigt.

Dann in `index.html` + `sitemap.xml` + `robots.txt` alle URLs ersetzen
und 301-Redirect von `crushitapp.vercel.app` zur neuen Domain via
`vercel.json` setzen.

---

## Checkliste

- [ ] Property in Search Console hinzugefügt
- [ ] Verifizierungs-Meta-Tag eingefügt + gepusht + verifiziert
- [ ] Sitemap `sitemap.xml` eingereicht (Status: Erfolg)
- [ ] Haupt-URL „Indexierung beantragt"
- [ ] Rich-Result-Test bestanden
- [ ] (Optional) eigene Domain registriert + verbunden
