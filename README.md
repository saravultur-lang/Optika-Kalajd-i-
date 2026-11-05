# Optika Kalajdžić

Statični landing page za OK-OPTIC d.o.o. Trebinje, pripremljen za GitHub i Cloudflare Workers.

## Cloudflare Workers — preporučena objava ovog statičnog sajta

Projekt je spreman i za Cloudflare Workers Static Assets. Koristi wrangler.jsonc i public/. Nije potrebna Worker skripta niti build korak.

U Cloudflare dashboardu otvori Workers & Pages, kreiraj Worker iz Git repozitorija i odaberi repozitorij sajta.

- Naziv Workera: optika-kalajd-i (mora odgovarati name u wrangler.jsonc).
- Root directory: korijen repozitorija.
- Production branch: main.
- Build command: prazno.
- Deploy command: npx wrangler@4 deploy.
- Sajt se služi iz public, kako je navedeno u wrangler.jsonc.

Alternativno, za ručnu objavu iz terminala u folderu projekta, nakon instaliranja Node.js:

```powershell
npx wrangler@4 login
npx wrangler@4 deploy
```

Za lokalni preview: npx wrangler@4 dev.

Nakon objave dodaj domenu u Worker Settings → Domains & Routes → Add → Custom Domain. Domena mora biti aktivna zona na istom Cloudflare računu. Domenu možeš zadržati kod trenutnog registrara i povezati je kroz Cloudflare DNS. Tačne DNS/namserver podatke uzmi iz svog Cloudflare dashboarda. Sačuvaj postojeće e-mail DNS zapise.

Statični zahtjevi i pohrana statičnih fajlova su prema trenutnoj dokumentaciji besplatni; ovaj projekt ne izvršava serversku Worker skriptu. Domena se obnavlja zasebno. Buduće dodavanje serverskih funkcija može uvesti limite/troškove. Objava na Cloudflareu zahtijeva povezivanje ovog repozitorija s Cloudflare računom.

Email Routing može prosljeđivati npr. info@tvoja-domena na postojeći potvrđeni Gmail. To nije zaseban inbox i samo prosljeđivanje ne omogućava slanje iz Gmaila kao ta domena. Kontakt na sajtu ostaje ocnakuca@gmail.com dok nova adresa ne bude zaista podešena.

Dokumentacija:
https://developers.cloudflare.com/workers/static-assets/get-started/
https://developers.cloudflare.com/workers/static-assets/billing-and-limitations/
https://developers.cloudflare.com/workers/ci-cd/builds/configuration/
https://developers.cloudflare.com/email-service/get-started/route-emails/

## Struktura

- public/index.html — cijela stranica, CSS i mali skript za mobilni meni.
- public/assets/ — samo šest fotografija/logotipova koje stranica koristi.
- public/robots.txt — dozvoljava indeksiranje.
- vercel.json — statična objava bez build koraka, izlaz public.

## Lokalni pregled

Otvori public/index.html u pregledniku. Nisu potrebni Node.js, instalacija paketa, baza podataka, API ključevi ni varijable okruženja.

## Git / GitHub

Repozitorij: https://github.com/saravultur-lang/Optika-Kalajd-i-
Produkcijska grana: main.

Nakon kloniranja repozitorija, izmjene spremaj iz njegovog foldera:

```powershell
git add .
git commit -m "Update website"
git push origin main
```

U Cloudflare Git integraciji odaberi upravo ovaj repozitorij i granu main. Worker zadrži pod nazivom optika-kalajd-i; naziv GitHub repozitorija može se razlikovati.

## Vercel

1. Add New → Project → importuj GitHub repozitorij.
2. Framework Preset: Other.
3. Root Directory: korijen repozitorija (folder koji sadrži ovaj README i vercel.json).
4. Build Command: prazno; Output Directory: public. To je već upisano u vercel.json.
5. Nisu potrebne varijable okruženja niti instalacija zavisnosti.
6. Deploy, zatim provjeri naslovnu stranicu, navigaciju, slike i mobilni meni.
7. U Settings → Domains dodaj kupljenu domenu i unesi DNS zapise koje Vercel prikaže kod DNS provajdera. Ne koristiti nasumične ili stare IP adrese.
8. Zadrži postojeće MX/TXT zapise e-mail servisa ako već postoji.

Vercel Hobby je za nekomercijalnu/personalnu upotrebu. Za komercijalni sajt optike planiraj Pro. Račun/pretplata, domena i DNS još nisu povezani.

Dokumentacija:
https://vercel.com/docs/builds/configure-a-build
https://vercel.com/docs/plans/hobby
https://vercel.com/docs/domains/working-with-domains/add-a-domain

## E-mail

Vercel ne pruža e-mail sandučiće. Adrese na vlastitoj domeni kreiraju se kod zasebnog e-mail provajdera; njegovi MX i TXT zapisi dodaju se u DNS. Postojeći kontakt na sajtu je ocnakuca@gmail.com, prema dostavljenim podacima. Primjer info@optikalajdzic.com nije otvorena adresa i nije dodan na sajt.
https://vercel.com/docs/domains/managing-dns-records

## Sadržaj i održavanje

Radno vrijeme Trebinja pon–uto zadržano je po izričitoj potvrdi korisnika. Ne dopisivati nepoznate dane. Oftalmološki pregled: samo Trebinje, telefonsko zakazivanje. Provjera vida: Trebinje i Banjaluka. Lokacije i kontakti su iz korisnikovog teksta.

Logo i tri fotografije radnje dostavio je korisnik. hero.jpg i naocale.jpg su generisani ilustrativni vizuali. Nema izmišljenih ocjena, recenzija ni statistika.

Promjene u Figma Designu ne mijenjaju automatski ovaj kod. Uređuje se public/index.html, zatim commit i push. Cloudflare nakon povezivanja repozitorija objavljuje promjene prema postavkama Git integracije.

## Provjera

Originalni HTML je pregledan u Chromeu na širinama 320, 390, 768, 1024 i 1440 px; provjereni su slike, lokalni anchor linkovi i mobilni meni. Fajl public/index.html je identična kopija provjerenog izvora. Objavljivanje na Vercelu još nije izvršeno.

Mobilni prikaz: provjeren na 22 širine od 320 do 1440 px, s otvorenim menijem i simuliranim uvećanjem teksta 130% i 200%. Provjera širine obavljena i bez overflow zaštite.
