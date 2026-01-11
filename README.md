# Andreas Lang - CV Landing Page

Modernit, yksisivuiset CV-kotisivut Junior QA Engineer -ammattilaiselle. Sivusto on optimoitu QR-koodiystävällisyyteen ja mobiililaitteille.

## Ominaisuudet

- **Responsiivinen design**: Toimii saumattomasti mobiilissa, tabletissa ja työpöytänäytöllä
- **QR-koodi-ystävällinen**: Kompakti, nopea ladata, helppo skannata
- **Ei build-prosessia**: Puhdas HTML/CSS, ei riippuvuuksia
- **Mobile-first**: Ensisijaisesti suunniteltu mobiililaitteille
- **Ammattimaiset värit**: Sininen-violetti gradienttiteema
- **Hover-efektit**: Hienovaraiset animaatiot linkeissä ja taitoissa

## Teknologiat

- HTML5
- CSS3 (inline styles)
- [Font Awesome 6.4.0](https://fontawesome.com/) - Ikonit

## Käyttö

1. **Avaa selaimessa**: Tuplaklikkaa `index.html`-tiedostoa tai avaa se suoraan selaimessa
2. **Ei palvelinta tarvita**: Tiedosto toimii `file://`-protokollalla
3. **Testaa responsiivisuus**:
   - Muuta selaimen ikkunan kokoa
   - Käytä DevTools device emulation -työkalua
   - Testaa oikealla mobiililaitteella

## Rakenne

```
├── index.html      # Pääsivusto (kaikki markup + CSS)
├── CLAUDE.md       # Ohjeet Claude Code -työkalulle
└── README.md       # Tämä tiedosto
```

## Responsiivisuus

- **Desktop** (>768px): 2-sarakkeinen grid-layout
- **Tablet** (480px-768px): 1-sarakkeinen layout, mukautetut fonttikoot
- **Mobile** (<480px): Optimoitu pienille näytöille

## Muokkaaminen

### Yhteystiedot
Päivitä `<header>`- ja `<footer>`-osioissa:
- Nimi, titteli, valmistumispäivä
- LinkedIn, GitHub, puhelin, sähköposti

### Sisältö
Jokaisella osiolla on oma `.section`-div:
- **Koulutus**: `.education-item`
- **Työkokemus**: `.experience-item`
- **Taidot**: `.skill-tag` span-elementit
- **Erikoisosaaminen**: `.special-item`

### Värit
Väripaletti löytyy CSS:stä:
- Päägradietti: `#667eea` → `#764ba2`
- Header: `#2d3748` → `#4a5568`
- Aksenttiväri: `#667eea`
- Hover: `#90cdf4`

## Lisenssi

© 2026 Andreas Lang. Kaikki oikeudet pidätetään.
