# Cryo-ET template blocks (plain-language menu)

This is the same set of blocks defined in `admin/config.yml`, written out in
plain language. When a researcher builds an experiment, these are the blocks
they can add and reorder. They only add the ones they actually did.

1. **Sample & Vitrification** — specimen type, organism, buffer, concentration,
   grid type, glow discharge, plunge freezer + blot force/time/humidity/temp,
   cryogen, notes.

2. **Cryo-FIB Milling (lamella)** — instrument, target thickness, milling angle,
   rough/fine currents, number of lamellae, Pt coating, milling software,
   lamella image, notes.

3. **Tilt-Series Acquisition** — microscope, voltage, detector, energy filter
   slit, magnification, pixel size, tilt scheme, tilt range/increment,
   dose per tilt, total dose, defocus range, acquisition software,
   number of tilt series, notes.

4. **Pre-processing** — motion correction software, CTF estimation software,
   dose weighting, frames per tilt, notes.

5. **Tilt-Series Alignment** — method (fiducial / patch tracking / AreTomo),
   fiducial size, software, mean residual error, notes.

6. **Tomogram Reconstruction** — method (WBP/SIRT/SART), software, 3D CTF
   correction, binning, tomogram dimensions, representative slice image, notes.

7. **Subtomogram Averaging** — particle, picking method, number of subtomograms,
   box size, STA software, symmetry, final resolution, final map image, notes.

8. **Deposition & Data** — EMDB / EMPIAR / PDB accessions, data storage
   location, notes.

- **Free-text / Observation** — a catch-all block with a heading, Markdown
  content, and an optional attachment.

---

### How to change the template

- **Add a field to a block:** in `admin/config.yml`, find the block and add a
  line like `- { label: "New field", name: "new_field", widget: "string" }`.
- **Add a whole new block:** copy any existing block under `types:`, give it a
  new `name` and `label`, and change its fields.
- **Make a new subject (e.g. single-particle cryo-EM):** copy the whole
  `cryo_et` collection, rename it, and swap in its blocks.

`widget` types you'll use most: `string` (one line), `text` (paragraph),
`number`, `select` (dropdown), `boolean` (toggle), `image` (upload),
`markdown` (rich text), `datetime`.
