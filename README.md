# Grădina Vie — web app

Aplicație de planificare a unei grădini de legume fără săpat (no-dig), cu calendar de plantare
adaptat zonei climatice, sarcini lunare, pași de amenajare de la zero și estimare de costuri.
Disponibilă în română și engleză.

## Utilizare rapidă (fără instalare)

Deschide `index.html` direct într-un browser (dublu-click pe fișier). Funcționează complet local —
datele profilului tău se salvează în browser (localStorage), nu sunt trimise nicăieri.

> Notă: dacă deschizi fișierul direct (`file://`), butonul de instalare pe telefon și modul offline
> (service worker) nu vor funcționa — acestea necesită ca aplicația să fie servită prin `http(s)://`.
> Geolocalizarea poate fi de asemenea restricționată de browser pentru fișiere locale.

## Rulare ca web app locală (recomandat pentru testare)

Din acest folder, cu Python instalat:

```
python3 -m http.server 8000
```

Apoi deschide `http://localhost:8000` în browser (Chrome/Edge/Safari/Firefox).

## Publicare online (ca să o poți instala pe telefon ca aplicație)

Cea mai simplă variantă, gratuită, fără cod:

1. Creează un cont gratuit pe [Netlify](https://app.netlify.com/drop) sau [Vercel](https://vercel.com).
2. Trage acest folder întreg (cu `index.html`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`)
   în zona de "deploy" (Netlify Drop e cel mai simplu — nu necesită cont pentru un test rapid).
3. Vei primi un link public (ex: `https://gradina-vie.netlify.app`).
4. Deschide acel link pe telefon:
   - **Android (Chrome)**: meniul (⋮) → „Adaugă pe ecranul principal” / „Instalează aplicația”.
   - **iPhone (Safari)**: butonul de partajare (□↑) → „Adaugă pe ecranul principal”.
5. Aplicația va apărea ca o iconiță separată, se deschide pe tot ecranul (fără bara browserului)
   și funcționează parțial offline datorită service worker-ului (`sw.js`).

Alternativ, poți publica gratuit pe **GitHub Pages**: creezi un repository, încarci fișierele din
acest folder, activezi „Pages” din setările repository-ului, și primești un link similar.

## Transformare într-o aplicație „nativă” de App Store / Play Store (opțional, pas avansat)

Dacă la un moment dat vrei o aplicație publicată în magazine, acest PWA poate fi împachetat cu
unelte precum [Capacitor](https://capacitorjs.com) sau [PWABuilder](https://www.pwabuilder.com/)
(încarci link-ul public de mai sus în PWABuilder și generează automat un pachet pentru Android/iOS).
Acesta e un pas separat, care necesită cont de dezvoltator Google/Apple.

## Structura fișierelor

```
index.html      — aplicația completă (HTML + CSS + JS, tot într-un fișier)
manifest.json   — configurare PWA (nume, iconițe, culori)
sw.js           — service worker pentru cache/funcționare offline
icon-192.png    — iconiță aplicație (mică)
icon-512.png    — iconiță aplicație (mare)
```

## Limitări de care să fii conștient

- Zonele climatice (caldă / temperată / rece) sunt aproximări generale bazate pe date medii de
  îngheț pe regiuni din România, nu pe stații meteo locale — verifică-le cu observațiile tale.
- Detectarea automată a locației foloseşte serviciul gratuit OpenStreetMap Nominatim pentru a afla
  județul din coordonatele GPS; mapează județul la o zonă printr-o listă simplificată — poți oricând
  corecta manual selecția din formularul de profil.
- Costurile din tab-ul „Amenajare & costuri” sunt medii naționale estimative, nu prețuri regionale
  exacte în timp real.
