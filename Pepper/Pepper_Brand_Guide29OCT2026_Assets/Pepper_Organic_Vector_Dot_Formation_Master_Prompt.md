### Pepper — Master Prompt: Organic Vector Dot Formation

Create a **pure SVG vector graphic composed exclusively of individual, uniformly sized, circular vector dots**, using the attached reference image as the definitive guide for the original dotted visual style.

**1. Reference Interpretation**

Use the attached references according to the following hierarchy:

- **Style reference:** Use the original dotted graphic to establish the exact visual language — dot size, spacing, density, distribution, negative space, colour scattering, and overall composition.
- **Subject reference:** Use the provided image of the desired object to establish its silhouette, structure, proportions, orientation, and recognisable features.

The style reference determines *how the object is constructed*. The subject reference determines *what the object looks like*.

Reconstruct the subject using the established dot-generation style rather than copying its original surface appearance, texture, shading, or material.

**2. Core Visual Style**

The object must appear to emerge from a carefully distributed collection of individual vector dots. The dots collectively define the object's silhouette and internal structure without creating a conventional solid illustration.

- Use perfectly circular dots, all with exactly the same diameter.
- Maintain consistent dot sizing throughout the entire composition.
- Keep every dot individually distinct, with clear separation from neighbouring dots.
- Never allow dots to overlap, touch, merge, or form clusters that resemble solid fills.
- Preserve generous negative space between dots to create an airy, lightweight, breathable composition.
- Use a relatively low dot density, following the sparse and deliberate distribution of the original style reference.
- Arrange dots organically to follow the contours and structural features of the subject, allowing its form to emerge through their collective placement.
- Ensure the silhouette remains recognisable despite the sparse distribution.
- Vary dot positions naturally according to the object's geometry, rather than placing them on a rigid grid or creating an evenly spaced halftone pattern.

**The dots themselves are the illustration.** Do not draw the object first and apply a dotted texture over it. Construct the object directly from individual dots.

**3. Colour Palette and Distribution**

Use only the following five colours:

**Primary colours**

- Orange: #FF5600
- Warm orange: #FF9C2C
- Golden yellow: #FFCE5E

**Secondary colours**

- Purple: #6E3FE7
- Light lavender: #D1B5FF

Distribute these colours organically throughout the dotted form, using the original style reference as the guide for colour placement and scattering.

- Let the primary colours establish the dominant visual presence.
- Introduce the secondary colours as complementary accents distributed naturally across the form.
- Allow colours to intermingle spatially through individual dot placement, creating a lively, scattered colour composition.
- Maintain a balanced distribution across the subject, with colour variation following the overall composition rather than a predetermined colour gradient.
- Do not assign colours according to artificial lighting, surface planes, shadows, highlights, or material properties.
- Do not use colour to simulate three-dimensional shading or to divide the object into conventional colour-coded sections.
- Avoid uniform colour blocks, gradient transitions, outlines, and artificial colour bands.

**Colour should feel scattered through the form, not applied as shading to the form.**

**4. Form Construction**

Interpret the subject's geometry and translate its defining features into a deliberate arrangement of dots.

- Follow the major contours and proportions of the subject.
- Use the distribution of dots to communicate the object's overall shape and essential structural details.
- Maintain sufficient dot density in visually important areas to preserve recognisability, while retaining the sparse, open quality of the reference.
- Use fewer dots in peripheral areas where additional detail is unnecessary.
- Preserve the natural relationship between the subject's main components.
- Keep the silhouette clean and intentional, without stray dots that weaken the composition.

Do not add solid shapes, filled silhouettes, continuous paths representing the subject, strokes, outlines, or additional graphic elements. The final visible object must be formed exclusively by the coloured dots.

**5. Technical Output Requirements**

Deliver the final result as a **standalone, editable SVG vector file**.

- Use native SVG `<circle>` elements for every dot.
- Give every circle the same radius.
- Specify colours using the exact hexadecimal values listed above.
- Keep all dots as separate vector elements.
- Use a clean SVG `viewBox` with appropriate margins around the composition.
- Use a transparent background.
- Do not embed raster images, base64 images, linked images, or image textures.
- Do not use filters, masks, gradients, blur, opacity effects, or raster-based effects.
- Do not include hidden raster assets, unnecessary metadata, or unrelated decorative elements.
- Ensure the SVG opens correctly in Adobe Illustrator, Figma, and standard SVG-compatible software.

**6. Strict Exclusions**

Do not generate a raster image, PNG, JPEG, or rendered preview as the deliverable.

Do not create a photorealistic object, a 3D render, a conventional flat illustration, a halftone effect, a stippled texture, or a shaded silhouette.

Do not vary dot sizes, overlap dots, merge them, or increase their density to create a solid-looking mass.

Do not introduce colours outside the specified palette.

Do not add text, labels, borders, shadows, backgrounds, connecting lines, or decorative particles unrelated to the subject.

**Final Deliverable**

Generate only the finished SVG vector file containing the individual coloured dots that form the requested subject.

The final graphic must preserve the original reference's distinctive qualities: **uniform dot size, sparse distribution, generous negative space, organic form construction, and freely scattered colours**. The result should feel like the same established visual system applied to a different subject, not a new interpretation of the style.

**Pepper-specific interpretation:** The five approved SVG dot colours are `#FF5600`, `#FF9C2C`, `#FFCE5E`, `#6E3FE7`, `#D1B5FF`. The wider brand palette also includes dark brown `#23120B`, which is **not** a permitted dot colour. The SVG background stays transparent; `GROUND IT WILL SIT ON` describes the preview surface and does not authorize a rectangle in the SVG. Exact dot diameter and minimum spacing must be approved separately before declaring finished production assets.

**Validation:**
- [ ] Every generated asset's "ground it will sit on" matches a real background color used in the final HTML — generating on white and dropping onto beige is the most common visible seam
- [ ] Generated assets never introduce a color outside §2's palette — if the model drifts, regenerate with the hex codes repeated in the prompt, don't hand-patch the output's colors after the fact
- [ ] If the asset includes any text/wordmark, it uses a font licensed for the brand, not a lookalike the image model substituted

---