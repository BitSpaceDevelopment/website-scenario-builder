# BSD XR Scenario Builder / Use Case Finder

Single-page BSD XR web tool for mapping industry challenges to recommended XR solutions and exporting a client-ready scenario brief as PDF.

This project is intentionally lightweight:

- No build step
- No framework dependency
- One deployable `index.html`
- Branding assets and reference guidance stored in `branding/`

## What The Tool Does

The interface is designed for discovery calls, internal scoping, and customer-facing walkthroughs.

Users can:

- Select an industry
- Select a challenge
- Review tailored XR recommendations
- Add client, project, priority, and note details
- Generate a print-ready PDF brief

Example solution outputs include:

- VR Lockout / Tagout Training
- WebXR Remote Maintenance Guides
- AR Assisted Inspections
- Soft Skill Simulations

## Current UX

The current version is structured as a working tool rather than a marketing landing page.

- Left panel: scenario inputs and editable brief metadata
- Right panel: live-updating scenario brief preview
- Action bar: reset and PDF generation
- Theme toggle: BSD XR dark/light modes with matching logo swap
- Print mode: optimized layout for browser "Save as PDF"

## PDF Export

The `Generate PDF` button uses the browser print flow via `window.print()`.

This keeps the implementation simple and dependency-free while still producing a clean deliverable.

How it works:

1. Fill in the brief fields.
2. Choose the industry and challenge.
3. Click `Generate PDF`.
4. In the browser print dialog, choose `Save as PDF`.

The print stylesheet hides configuration-only UI and formats the scenario brief for export.

## Brand Direction

This tool follows the BSD XR branding references in the `branding/` directory.

Core design rules carried into the app:

- Space Mono everywhere
- Uppercase user-facing text
- Sharp 90-degree corners only
- 1px borders only
- No shadows
- No decorative UI gradients
- Minimal accent usage
- Sparse, structured layout

The XR logo gradient remains reserved for the logo assets only.

## Project Structure

```text
scenario-builder/
├── index.html            # Main single-page application
├── README.md             # Project documentation
├── .gitignore            # Local machine file ignores
└── branding/
    ├── branding.md       # Source-of-truth brand guidelines
    ├── README.md         # Branding package documentation
    ├── theme.json        # Brand tokens
    ├── logo-dark.png     # Use on dark backgrounds
    ├── logo-light.png    # Use on light backgrounds
    ├── dark.png          # UI reference image
    ├── light.png         # UI reference image
    ├── index.html        # Branding reference implementation
    └── vercel.json
```

## Scenario Mapping

The recommendation engine is currently hardcoded inside `index.html`.

It maps:

- 5 industries
- 5 challenge types
- 25 scenario combinations

Each combination includes:

- Scenario title
- Summary
- Why-it-works explanation
- Deployment guidance
- Impact bullets
- Fit bullets
- Three recommended XR solutions

## Local Use

Because the app is fully static, you can open it directly in a browser:

```bash
open index.html
```

Or serve it locally with any static server if preferred.

Example:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Deployment

This repo is suitable for static hosting platforms.

Good options:

- GitHub Pages
- Vercel
- Netlify
- Any static web server

No build pipeline is required.

## Customization Notes

If you want to evolve the tool further, the next logical additions would be:

- More industries and challenge categories
- Editable recommendation data outside the HTML file
- Lead capture or CRM handoff
- Branded cover page for exported PDF
- Multiple export templates
- Richer scoring or recommendation weighting

## Known Implementation Notes

- PDF export relies on the browser print dialog rather than a dedicated PDF library.
- Scenario data currently lives inline in the page script for portability.
- The project intentionally avoids a JS framework to keep deployment friction near zero.

## BSD XR

- Website: [bsdxr.com](https://bsdxr.com)
- Contact: [bsdxr.com/contact](https://bsdxr.com/contact)
- Company: Bit Space Development Ltd.
- Location: Winnipeg, Manitoba, Canada

