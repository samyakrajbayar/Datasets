Art Institute of Chicago Collection

### 12,000 objects from the Art Institute of Chicago

The Art Institute publishes its collection through a free API, including curatorial metadata that most
museums keep internal: classification, style, theme, subject tags, provenance text and even computed
image colour statistics.

This snapshot has **12,000 objects** and **62 parameters**:
- **Identity** — id, title, accession number, reference API link, fiscal year.
- **Creation** — display date, start and end years, derived century, decade, object age, place of origin.
- **Materials** — medium text, a normalised medium class, dimensions, classification and artwork type.
- **Curation** — department, style(s), themes, subject tags, tag count, description and provenance lengths.
- **Artist** — id, name, display string, attribution flags.
- **Rights and access** — public-domain flag, copyright notice, zoomability, educational and multimedia
  resource flags, alternate images, documents, audio.
- **Imaging** — thumbnail presence and pixel dimensions, aspect ratio, colourfulness, dominant colour
  hue/saturation/lightness and its pixel population.
- **Display** — gallery title and coordinates when the object is on view.

**50.5%** of the objects are public domain and many ship with a thumbnail URL pattern
(`https://www.artic.edu/iiif/2/<image_id>/full/843,/0/default.jpg`), so the file doubles as an
image-classification manifest.

62 columns; one row per artwork.
