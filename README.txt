Finans PWA – bestanden

Inhoud:
- manifest.json
- sw.js
- icons/ (PNG iconset + master icon.svg)

Wat je moet doen in je bestaande HTML (index.html):
1) Verwijder de inline manifest <script> in <head> (die Blob/URL.createObjectURL maakt).
2) Voeg in <head> dit toe (liefst net na <title>):

<link rel="manifest" href="manifest.json">
<link rel="icon" type="image/png" sizes="32x32" href="icons/favicon-32.png">
<link rel="apple-touch-icon" sizes="180x180" href="icons/apple-touch-icon.png">
<meta name="theme-color" content="#0c0c0e">

3) Voeg in je bestaande <script> (onderaan, of helemaal aan het einde) toe:

if ("serviceWorker" in navigator) {
  window.addEventListener("load", () => {
    navigator.serviceWorker.register("./sw.js");
  });
}

Deploy:
- Zet index.html + manifest.json + sw.js + icons/ op dezelfde root.
- Serve via HTTPS (Vercel/Netlify/GitHub Pages/etc).

Installeren:
- Android/Chrome: open site → menu → “Installeren”.
- Desktop Chrome/Edge: install-icoon in adresbalk.
- iOS Safari: Share → “Zet op beginscherm” (iOS gebruikt apple-touch-icon).
