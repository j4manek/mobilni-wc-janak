# Prompty pro ChatGPT (DALL-E / GPT-4o obrázky) – realistické fotky produktů

## Důležité: nejdřív nahraj logo

Nahraj do chatu soubor **`assets/img/logo-janak.png`** (je v projektu, 1320×520 px, vysoké
rozlišení) jako referenční obrázek – a až pak pošli prompt k obrázku. ChatGPT s GPT-4o image
generation umí vzít nahraný obrázek jako referenci a vložit ho do nové scény. Díky tomu se
na kabině objeví **přesně náš skutečný grafický návrh loga** (velké černé "Mobilní WC" +
světle modré "Janák" + maskot záchodu), ne AI dohad/zkomolený text.

Logo je aktuální verze 2026-10-07 (světlejší modrá #0ea5e9, "Mobilní WC" jako hlavní nápis,
"Janák" jako menší příjmení pod ním) – pokud máš na ploše starší `logo-janak.png`, přepiš ho
tím z `assets/img/logo-janak.png` v projektu.

Pokud by GPT i přes nahrané logo generoval vlastní zkomolený nápis navíc, doplň do promptu
větu: *"Use only the uploaded logo image, do not generate any additional text."*

Doporučení: generuj všechny 4 v jedné konverzaci po sobě (logo nahraj jednou na začátku,
pak jen měň prompt) – ChatGPT pak drží konzistentní styl mezi obrázky. Požaduj portrétovou
orientaci (na výšku) – sedí to s kartami na webu.

Až dostaneš 4 obrázky zpět, pošli mi je (soubory nebo odkazy) a zapracuju je do karet.

---

## 1. Mobilní WC (standardní kabina)

```
Using the uploaded logo image exactly as provided (do not redraw or alter it), create a
professional product photo of a modern portable toilet cabin (porta-potty), front
three-quarter view. Vibrant blue (hex #0ea5e9) glossy plastic body — this exact blue is the
main color of the whole unit, matching a brand's website blue — with a white dome-shaped
roof and a white accent band near the top, small ventilation slits below the roofline.
Place the uploaded logo on the white accent band, keeping it crisp and fully legible. Below
the band, a closed white door with a simple blue person silhouette icon. Studio lighting,
soft realistic shadow on the ground, plain light gray seamless background, realistic
plastic material with subtle sheen and reflections, high detail, commercial product
catalog photo style, no additional text besides the uploaded logo, no watermark, portrait
orientation, 4k quality.
```

## 2. Mobilní WC pro invalidy (bezbariérová kabina)

```
Using the uploaded logo image exactly as provided (do not redraw or alter it), create a
professional product photo of a wider wheelchair-accessible portable toilet cabin, front
three-quarter view. Vibrant blue (hex #0ea5e9) glossy plastic body — this exact blue is the
main color of the whole unit, matching a brand's website blue — with a white dome-shaped
roof and a white accent band near the top, a wider door than a standard unit with a blue
wheelchair accessibility icon on the white door, a visible grab rail through the door gap.
Place the uploaded logo on the white accent band, keeping it crisp and fully legible. Same
studio lighting, soft realistic shadow, plain light gray seamless background, realistic
plastic material, high detail, commercial product catalog photo style, no additional text
besides the uploaded logo, no watermark, portrait orientation, 4k quality.
```

## 3. Mobilní pisoár (samostatná jednotka)

```
Using the uploaded logo image exactly as provided (do not redraw or alter it), create a
professional product photo of a standalone outdoor urinal screen unit (portable pissoir),
front view. Vibrant blue (hex #0ea5e9) glossy plastic modesty-screen panels — this exact
blue is the main color of the whole unit, matching a brand's website blue — with a white
accent band near the top, flat open top with no roof dome, compact footprint. Place the
uploaded logo on the white accent band, keeping it crisp and fully legible. Same studio
lighting, soft realistic shadow, plain light gray seamless background, realistic plastic
material, high detail, commercial product catalog photo style, no additional text besides
the uploaded logo, no watermark, portrait orientation, 4k quality.
```

## 4. Mobilní umyvadlo (umývací stanice)

```
Using the uploaded logo image exactly as provided (do not redraw or alter it), create a
professional product photo of a mobile hand-washing station, front view. A vibrant blue
(hex #0ea5e9) glossy plastic water tank unit on top — this exact blue is the main color of
the whole unit, matching a brand's website blue — with a white accent band, a round white
wash basin with two blue tap spouts mounted below the tank, standing on simple metal legs.
Place the uploaded logo on the white accent band, keeping it crisp and fully legible. Same
studio lighting, soft realistic shadow, plain light gray seamless background, realistic
plastic and metal material, high detail, commercial product catalog photo style, no
additional text besides the uploaded logo, no watermark, portrait orientation, 4k quality.
```

---

Pokud se logo na fotce i přes tohle zkreslí/rozmaže (časté u image modelů s malým detailním
textem), pošli mi radši fotku BEZ loga (vynech tu první větu z promptu) – ořežu a přidám naše
logo já sám přesně a ostře, jak to dělám teď na vektorových ilustracích.
