# Atlas Praxis

Atlas Praxis is an open geomatics teaching studio for visual reasoning. It is a browser-based learning environment for teaching how maps represent geographic information, how visual perception shapes map use, and how cartographic design choices become arguments.

The current release is fully static and deployable on Vercel. It has no backend, login, upload system, database, student accounts, paid API, API key, or external map token.

## Teaching Purpose

Atlas Praxis supports postgraduate geomatics teaching through a studio cycle:

- Observe mapped patterns and visual hierarchy.
- Modify classification, colour, opacity, variables, and representation methods.
- Critique representation, perception, interpretation, ethics, and communication.
- Communicate exploratory findings as concise featured graphics.

Atlas Praxis is developed in connection with postgraduate teaching at the University of Glasgow, including [GEOG5026 Visualisation & Map Use](https://www.gla.ac.uk/coursecatalogue/course/?code=GEOG5026). The course focuses on applied map design, geographic information visualisation, map use, visual perception, critical analysis of geospatial representation, map-user evaluation, map production, and oral discussion of cartographic issues.

Atlas Praxis is an open teaching studio and should not be described as an official University of Glasgow platform.

## Pages And Features

- Home: product overview, learning pathway, course integration, and classroom activities.
- Studio: Leaflet map studio centred on Glasgow with OpenStreetMap tiles, attribution, Glasgow SIMD 2020v2 data zones, deprivation-rank handling, palette notes, and classification notes.
- Cartographic Studio details: collapsible Legend, Diagram, Design Review, and Cartographic Note views inspired by *Mapping for a Sustainable World*.
- Concepts: public teaching notes on map communication, visual perception, geovisualisation, data structure, visualisation purpose, interaction, bivariate mapping, and cartograms.
- Critique: five-part framework covering Representation, Perception, Interpretation, Ethics, and Communication, plus a concise map critique activity.
- Featured Graphics: learning model for moving from map exploration to publication-style visual explanation.
- Case Studies: DOI-linked teaching cards with local open-access PDFs and prompts for reading featured graphics.
- About: course connection, implementation notes, and roadmap.

## Studio Data

The Visual Reasoning Studio uses a local static Glasgow SIMD 2020v2 GeoJSON file:

```text
public/data/glasgow-simd-2020v2.geojson
```

Generate or refresh the file with:

```bash
npm run fetch:simd
```

The fetch script queries the Scottish Government ArcGIS REST layer for Glasgow City only, saves the returned GeoJSON locally, and the browser reads that local file at runtime. This keeps the deployed app static and avoids live GIS service calls from the public site.

The Studio supports:

- Overall SIMD rank
- SIMD percentile
- SIMD quintile
- Income rank
- Employment rank
- Health rank
- Education rank
- Access rank
- Crime rank
- Housing rank

In SIMD, lower ranks indicate greater relative deprivation. The Studio reverses rank values for choropleth intensity so darker colours indicate greater deprivation, while popups still show the original SIMD ranks.

The Studio also includes lightweight collapsible details. Students start with the map as the main view, supported by a small reading overlay. The Legend and Diagram details compare the choropleth legend with class counts. The Design Review detail translates guidance from *Mapping for a Sustainable World* into purpose, data, symbolization, and use-environment checks. The Cartographic Note detail gives a compact printable source statement for classroom reporting.

The Studio uses the OpenStreetMap tile endpoint:

```text
https://tile.openstreetmap.org/{z}/{x}/{y}.png
```

No Mapbox token or paid map service is used.

## Teaching Use

Atlas Praxis is designed for a 30-60 minute practical session. A typical activity asks students to explore the Visual Reasoning Studio, change mapped variables, classification methods, and colour palettes, respond to critique prompts, and translate their observations into a featured-graphics style visual argument.

The core learning pathway is:

- Observe mapped patterns and visual hierarchy.
- Modify variables, classification, and palettes.
- Critique representation, perception, interpretation, ethics, and communication.
- Communicate a concise visual argument.

## Data And Attribution

The Visual Reasoning Studio uses Scottish Index of Multiple Deprivation (SIMD) 2020v2 data for Glasgow data zones. SIMD is a relative, area-based measure of deprivation and should not be interpreted as describing every individual within an area.

Map tiles are provided by OpenStreetMap contributors. SIMD data are provided by the Scottish Government and contain Ordnance Survey data © Crown copyright and database right. Used under the Open Government Licence.

## Case Study Resources

Open-access case-study PDFs are stored in `public/pdfs/` and linked from the Case Studies page:

- `construction-demolition-england-2025-epb.pdf`
- `scotland-twin-referendums-2026-rsrs.pdf`
- `academy-nations-2025-epb.pdf`

The site links to DOI records and local PDFs. It does not embed screenshots from the PDFs or republish slide content.

## Local Setup

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Fetch the Glasgow SIMD layer:

```bash
npm run fetch:simd
```

Build the static production bundle:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

## Deployment

Atlas Praxis can be deployed to Vercel or any static hosting platform with standard Vite settings.

- Build command: `npm run build`
- Output directory: `dist`
- Environment variables: none

Suggested deployment flow:

1. Push the repository to GitHub.
2. Import the repository into Vercel.
3. Confirm the Vite framework preset.
4. Ensure `public/data/glasgow-simd-2020v2.geojson` has been generated and committed.
5. Deploy the static site.

## Instructor Materials

See [docs/instructor-guide.md](docs/instructor-guide.md) for a 30-60 minute class plan that uses the Studio, Critique, and Featured Graphics pages without requiring accounts or external services.

## Roadmap

- Side-by-side map design comparison.
- Exportable critique sheets.
- Additional open teaching datasets.
- Instructor activity templates.
- Web/mobile mapping exercises.
- Geospatial data infrastructure and land information design modules.

## Citation And Acknowledgement

If you use Atlas Praxis in teaching or workshops, please acknowledge:

Wang, M. Atlas Praxis: An Open Geomatics Studio for Visual Reasoning. University of Glasgow. https://atlas-praxis.mingshuwang.org/

## Maintainer And Contact

Dr Mingshu Wang  
Reader in Geospatial Data Science  
University of Glasgow  
Email: Mingshu.Wang@glasgow.ac.uk  
Personal website: https://mingshuwang.org  
University profile: https://www.gla.ac.uk/schools/ges/staff/mingshuwang/

## License

MIT
