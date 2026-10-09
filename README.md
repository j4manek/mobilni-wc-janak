# Návrh webu Mobilní WC Janák (lokální prototyp)

Jednostránkový web pro pronájem mobilních WC a hygienického zázemí. Design, fonty, barvy
a vizuální styl jsou převzaté z webu janak-instalaterstvi.cz (`outputs/janak-web-navrh-local`),
aby obě stránky působily jako sourozenecké weby – obsah je ale napsaný od nuly, protože pro
tuto službu dosud žádný web neexistoval (ověřeno webovým hledáním 2026-10-07).

## Spuštění

```bash
cd outputs/mobilni-wc-janak-web
python3 -m http.server 8000
```

Pak otevřete http://localhost:8000.

## Co obsahuje

Jedna stránka (`index.html`): hero, nabídka (3 karty), pro koho, oblast působnosti, o službě,
kontakt s formulářem. Plus `ochrana-soukromi.html` a `zasady-cookies.html` (právní stránky,
bez nich formulář nemůže mít GDPR souhlas) a `mereni.js`/`navrh.js` (stejná měřicí/menu logika
jako u instalatérství, jen přejmenované proměnné `wc-janak-consent` / `WCJANAK_LEAD_ENDPOINT`,
ať nekolidují, pokud by weby časem běžely na stejné doméně).

## Rozhodnutí z rozhovoru s Jonym (2026-10-07)

- **Samostatná firma** – mobilní WC Janák je jiný subjekt než instalatérství Janák, proto:
  - **logo není převzaté** (originál má vlastní wordmark „Janak Instalatérství“) – nový web má
    jednoduché textové logo „Mobilní WC / Janák“ + maskot záchodu (`hajzl.png`, obecný klipart
    použitý i na původním webu, ne firemní logo).
  - **žádný odkaz/provázání** mezi weby, žádné sdílené IČO.
  - **žádné reálné fotky ani reference nejsou převzaté** – fotky práce a recenze z instalatérství
    patří k jiné firmě a nehodí se sem. Sekce O nás proto nemá galerii ani recenze.
- **Kontakt a oblast – stejné jako instalatérství** (na výslovné přání): telefon
  +420 773 146 244, e-mail instalater.janak@seznam.cz, adresa Struha 794, Vamberk,
  Královéhradecký a Pardubický kraj.
- **Rozsah: jedna stránka**, ne víc podstránek jako u instalatérství.

## Otevřené body (žlutě označené „[ověřit]“ v textu)

Obsah nabídky (typy kabin, umývárny, servis, doplňky) je návrh podle běžné nabídky v oboru
(TOI TOI, WC4YOU a podobné firmy – ověřeno websearchem), **ne podle reálné nabídky firmy**.
Před spuštěním je nutné s majitelem potvrdit a nepotvrzené smazat:

1. **Skutečná nabídka**: jaké typy kabin/umýváren firma reálně půjčuje, jestli nabízí VIP
   kabiny, oplocení, kontejnery, doplňování spotřebního materiálu.
2. **Ceník**: web tvrdí transparentní ceny, žádnou neuvádí.
3. **IČO** firmy (patička, JSON-LD) – chybí úplně, nesmí se použít IČO instalatérství.
4. **E-mail**: je instalater.janak@seznam.cz vhodný i pro tuto službu, nebo založit nový?
5. **Pracovní doba a dostupnost** (hero i kontakt).
6. **Oblast**: okresy a maximální dojezdová vzdálenost.
7. **Doména**: v JSON-LD je placeholder `mobilni-wc-janak.cz` – doménu je potřeba zaregistrovat
   nebo nahradit skutečnou.
8. **Sociální sítě**: web zatím žádné neodkazuje (nevymýšlel jsem profily) – doplnit až budou
   založené.
9. Stránky mají `noindex` – před nasazením odstranit (`<meta name="robots">` ve všech 3 souborech).
10. Formulář zatím nic neodesílá (jen potvrzení) – napojení na e-mail/Telegram viz
    `outputs/lead-telegram-automation/`, stejně jako u instalatérství.

## Update 2026-10-07 (večer): 4 produkty + vlastní logo

Na Jonyho pokyn jsem se inspiroval konkurencí (TOI TOI, Johnny Servis – websearch, produktová
řada "JOE"/"JOE kontejner") a přepracoval sekci Nabídka z obecných 3 karet na **4 konkrétní
produkty**, každý jako vlastní ilustrace v barvách webu (modrá/bílá), ne fotky cizích firem:

1. Mobilní WC (`assets/img/product-wc.svg`)
2. Mobilní WC pro invalidy – bezbariérové (`product-invalid.svg`)
3. Mobilní pisoár (`product-pisoar.svg`)
4. Mobilní umyvadlo (`product-umyvadlo.svg`)

Ilustrace jsou vlastní vektorová kresba (ne reálné fotky produktů, které firma nemá) s nápisem
„JANÁK" na kabině – stejný princip jako konkurence značí vlastní kabiny. Každá karta teď má
primární CTA tlačítko „Nezávazná poptávka" + telefon, podle Jonyho zadání že aktuální cíl webu
je dostat lidi do formuláře nebo na telefon.

**Logo**: `assets/img/logo-janak.svg` – vlastní vektorové logo (ne převzaté z instalatérství):
velké černé „Janák" (stejná hierarchie jako na původním webu, aby fungovala značka napříč
oběma firmami) + menší modré „Mobilní WC" + maskot záchodu. Použité v hlavičce všech 3 stránek.

**Technická poznámka**: `lg:grid-cols-4` není v `entry.css` (originál ho nikde nepoužil), proto
je dopsaný v `navrh.css`. Stejný princip jako u `sm:grid-cols-3` v původním webu – chybějící
Tailwind třídy se doplňují ručně.

## Update 2026-10-07 (pozdě večer): realističtější ilustrace + maskot v logu na kabinách

Čtyři produktové ilustrace mají teď gradienty, jemný stín a odlesk (ne plochý sketch) a na
každé kabině je kolečkový odznak s maskotem záchodu (`hajzl.png`) místo jen textu „JANÁK" –
stejný princip jako nálepka/logo na reálných kabinách konkurence.

**Důležité omezení, které jsem Jonymu nahlásil**: tohle je pořád vektorová ilustrace, ne
fotorealistický render. Skutečnou fotorealistu (jako fotky konkrétního výrobku) bych musel
generovat přes placenou AI image-gen službu (Everygen/Canva/Figma generate-image) nebo sehnat
licencované stock fotky – obojí stojí peníze nebo nese riziko špatné licence, a bez výslovného
souhlasu jsem to nespouštěl (cost-zero-tolerance pravidlo). Pokud bude chtít skutečný foto-look,
je to další krok, ne automatické rozšíření tohoto promptu.

## Update 2026-10-07 (noc): světlejší modrá + logo naopak, ChatGPT prompty pro reálné fotky

Jony chtěl zkusit světlejší modrou, inspirovanou konkurencí **Wecko** (mobilniwecko.cz, hlavní
barva `#3ebdec` – zjištěno z jejich CSS, ne převzato 1:1, jen jako směr). Použil jsem vlastní
odstín `#0ea5e9` (Tailwind "sky"), ne jejich přesný hex, aby se weby nepletly.

**Co se změnilo:**
- **Celá stránka** má teď světlejší modrou místo původní tmavší `#2563eb` – udělané přepisem
  Tailwind proměnných `--color-blue-*` v `navrh.css` (fungují, protože `entry.css` je volá přes
  `var()`), takže se to promítlo do všech tlačítek, nadpisů i ikon najednou, ne ručně po jednom.
- **Logo (`logo-janak.svg`/`.png`) má prohozenou hierarchii**: teď je velké černé "Mobilní WC"
  (hlavní nabízená služba) a malé modré "Janák" pod ním (příjmení, menší důraz) – obráceně než
  předtím a obráceně než na instalatérství (tam je velké příjmení). Důvod: lidé hledají
  "mobilní WC", ne "Janák", a je to i jasnější odlišení od sesterské firmy.
- 4 produktové ilustrace mají upravené odstíny bandu/ikon na stejnou novou modrou.
- **`image-prompts.md`** – prompty pro ChatGPT na reálné fotky produktů, aktualizované na novou
  modrou (`#0ea5e9`) a na nahrávání `logo-janak.png` jako reference (ne textový dohad loga).
  Čeká se na výsledky od Jonyho.

## Update 2026-10-08: foto hero banner (festival) podle vzoru konkurence

Jony poslal screenshot hero banneru konkurenční firmy (fotka ze stavby + jejich kabina s logem
přes foto + bílý nápis). Udělal jsem obdobu, ale s festivalem místo stavby (sedí líp k naší
"jsme i instalatéři" story) a naší kabinkou/logem:

- **Fotka**: `assets/img/hero-festival.jpg` – stock foto z Pexels (fotografka Wendy Wei,
  photo ID 2342409), licence Pexels = volné pro komerční i nekomerční použití bez nutnosti
  uvádět autora. <span class="ov">[i tak doporučuju před ostrým spuštěním ověřit aktuální
  licenční podmínky na pexels.com/license, pro jistotu]</span>
- Kabinka (`product-wc.svg`) je v popředí vpravo dole, stejně jako na referenčním screenshotu.
- Text sedí na tmavé poloprůhledné kartě (`.hero-photo__panel`), ne přímo na fotce – vyzkoušel
  jsem napřed gradient přes celou fotku, ale kontrast textu byl nespolehlivý podle toho, co
  zrovna bylo na fotce pod textem (world. jasná zeleň stromů). Karta je spolehlivější a funguje
  stejně dobře na mobilu i desktopu.
- `.dark` třída na obsahovém wrapperu automaticky přepne `text-highlighted`/`text-muted`/atd.
  na světlé varianty z existujícího design systému (entry.css má vestavěný dark mode), takže
  nebylo potřeba ručně přebarvovat každý prvek v hero sekci zvlášť.

Pokud by Jony chtěl i vlastní reálnou fotku (ne stock), stačí nahradit
`assets/img/hero-festival.jpg` – rozměry/ořez (object-fit: cover) se přizpůsobí automaticky.

## Update 2026-10-08 (2): skutečná fotka WC místo ilustrace

Jony trval na tom, že kabina v hero musí být vidět a musí být **reálná fotka, ne ilustrace**
(opakovaná zpětná vazba). Vektorové SVG ilustrace (`product-*.svg`) zůstávají na kartách v
sekci Nabídka – pro hero banner jsem místo nich udělal skutečný foto-kompozit:

1. **Zdrojová fotka**: Pexels, fotograf Ardalan Hamedani, photo ID 28759904 – reálná červená
   mobilní toaleta (značka "Maple Leaf Disposal") v přírodním prostředí. Licence Pexels.
2. **Přebarveno na naši modrou** (`#0ea5e9`) – cílený HSV hue-shift jen na sytě červené pixely
   (práh na saturaci a odstín), bílá střecha/šedé kování/zeleň pozadí zůstaly beze změny.
   Script: viz git historie (`assets/img/hero-wc-real.jpg` je už hotový výsledek, zdrojový
   skript se neukládal do repa).
3. **Nálepka "Maple Leaf Disposal + telefon" nahrazena naší** – vytvořená nálepka s maskotem,
   "JANAK", "MOBILNÍ WC" a telefonem, vložená přes měkký stín přesně na místo původní nálepky.
4. **Oříznuto** na poměr stran vhodný pro hero (kabina vpravo, prostor na stromy/zeleň vlevo
   pro textový panel).

`assets/img/hero-festival.jpg` (dřívější fotka davu na festivalu) je smazaná, nahrazená touto.
Textový panel (`.hero-photo__panel`) zůstal stejný – funguje nezávisle na tom, jaká fotka je
na pozadí.

**Otevřený bod**: stejně jako u festivalové fotky doporučuju před ostrým nasazením ověřit
aktuální podmínky licence Pexels (pexels.com/license) – changes v politice jsou vzácné, ale
stojí za kontrolu u webu, který bude mít reálný provoz.

## Update 2026-10-09: piktogramy podle skutečných standardů

Předchozí dva pokusy o piktogramy (jednoduchý obrys, pak detailnější obrys) nevypadaly dobře –
moc tenkých čar vedle sebe se na malé ploše slilo do nečitelné změti. Místo dalšího hádání jsem
našel skutečné zdroje:

- **Mobilní WC**: oficiální piktogram Google Material Icons „wc" (stejný typ značky jako na
  dveřích veřejných toalet).
- **Mobilní WC pro invalidy**: oficiální „International Symbol of Access" (ikona vozíčkáře),
  taky z Material Icons – stejná ikona, jakou používá ISO 7001 a skutečné bezbariérové značení.
  Obě pod licencí Apache 2.0 (ikony Google), volně použitelné.
- **Mobilní pisoár** a **Mobilní umyvadlo**: pro tyhle neexistuje žádný celosvětový standard
  (pisoár jako produkt nemá vlastní piktogram), takže jsem je domaloval ve stejném plném
  (vyplněném, ne obrysovém) stylu, aby to vizuálně sedělo k těm dvěma oficiálním.

Klíčové poučení: plné vyplněné tvary (solid fill) čte oko mnohem líp než tenké obrysové linky
na malé ploše – to byla hlavní chyba předchozích verzí, ne množství detailu.

## Update 2026-10-09 (2): piktogramy ve stylu wcmarket.cz

Jony poslal přímo zdrojový web (wcmarket.cz/mobilni-wc-cena) jako referenci podruhé – šel jsem
se tam přímo podívat a vytáhl přes Playwright skutečný SVG kód jejich ikon (dvojitá silueta
dveří kabiny, tenká linka, nádrž/pisoárová silueta). Jejich přesný kód jsem **nekopíroval**
(je to jejich vlastní grafika), ale nakreslil vlastní ikony se stejným vizuálním jazykem –
stejná silueta dveří, stejná síla čáry, jen v naší modré místo bílé (jejich web má tmavé
pozadí, náš světlé karty).

Předchozí plné (vyplněné) piktogramy z Google Material Icons byly samy o sobě v pořádku
(skutečné standardy), ale neseděly stylově k tomu, co měl Jony na mysli – tenký obrys, ne
plná barva.

## Ověření

Prototyp jsem otestoval přes Playwright (desktop 1440px, mobil 390px): hero, karty nabídky,
mobilní menu, sticky lišta volání, cookie banner i právní stránky se vykreslují správně,
bez chyb v konzoli. Doplnil jsem `scroll-mt-[var(--ui-header-height)]` na kotvy sekcí – bez
toho menu scrollovalo pod sticky hlavičku (stejný neduh by měl i původní web na analogických
kotvách mimo `#sluzby`).
