# Gemmology Knowledge

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

FGA curriculum documentation and study materials for the [Gemmology Project](https://gemmology.dev).

This repository contains comprehensive reference documentation covering the Gemmological Association of Great Britain (Gem-A) Foundation and Diploma curriculum topics, organized as modular knowledge bases that integrate with the [gemmology-plugin](https://github.com/gemmology-dev/gemmology-plugin) for Claude Code.

## Overview

The Gemmology Knowledge repository serves as the authoritative reference library for coloured gemstone expertise. It provides:

- **13 Knowledge Modules** covering core gemmological topics
- **Quick Reference Sheets** for rapid data lookup
- **Study Guides** aligned with FGA Foundation and Diploma courses
- **Glossary** of gemmological terminology

All content is designed to be both human-readable documentation and machine-consumable knowledge for AI-assisted gem identification and education.

## Knowledge Modules

The `skills/` directory contains 13 comprehensive knowledge modules:

| Module | Description |
|--------|-------------|
| `physical-properties/` | Hardness (Mohs scale), specific gravity, crystal systems, cleavage, fracture, and lustre |
| `optical-properties/` | Refractive index, birefringence, pleochroism, dispersion, and spectroscopy |
| `chemical-properties/` | Chemical composition, chromophores, trace elements, and colour causes |
| `inclusions-fingerprints/` | Internal features, diagnostic inclusions, growth patterns, and fingerprint identification |
| `gem-testing-instruments/` | Refractometer, spectroscope, polariscope, dichroscope, Chelsea filter, UV lamp, and microscopy |
| `treatments-enhancements/` | Heat treatment, diffusion, filling, coating, irradiation, and treatment detection |
| `synthetics-simulants/` | Flame fusion, hydrothermal, flux growth, CVD/HPHT, and synthetic identification |
| `gemstone-species/` | Detailed profiles for 50+ gem species and varieties |
| `grading-valuation/` | Colour grading (hue, tone, saturation), clarity, cut quality, and value factors |
| `gem-care-durability/` | Stability, cleaning methods, setting recommendations, and storage |
| `origin-determination/` | Geographic origin characteristics, provenance, and origin premiums |
| `phenomenal-gems/` | Asterism, chatoyancy, adularescence, labradorescence, play of colour, and colour change |
| `crystal-visualization/` | CDL notation, crystal morphology, Miller indices, and 3D visualization |

## Repository Structure

```
gemmology-knowledge/
├── skills/                    # 13 knowledge modules
│   ├── physical-properties/
│   │   ├── SKILL.md          # Main skill definition
│   │   └── references/       # Supporting reference files
│   │       ├── hardness-scale.md
│   │       ├── specific-gravity.md
│   │       ├── crystal-systems.md
│   │       └── cleavage-fracture.md
│   ├── optical-properties/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── ... (other modules)
│   └── crystal-visualization/
├── quick-reference/           # Rapid lookup tables
│   ├── ri-table.md           # Refractive index reference
│   ├── sg-table.md           # Specific gravity reference
│   ├── hardness-comparison.md
│   └── spectrum-chart.md
├── study-guides/              # Course-aligned study materials
│   ├── fga-foundation/
│   └── fga-diploma/
├── glossary/
│   └── terms.md              # Gemmological terminology
├── docs/                      # Generated documentation site
├── scripts/
│   └── generate_docs.py      # Build docs from skills
├── .github/
│   └── workflows/
│       ├── docs.yml          # Documentation deployment
│       └── link-check.yml    # Internal link verification
├── README.md
├── LICENSE
└── CHANGELOG.md
```

## Content Structure

Each knowledge module follows a consistent structure:

### SKILL.md Format

```markdown
---
name: Physical Properties
description: Use this skill when the user asks about...
triggers:
  - gemstone hardness
  - Mohs scale
  - specific gravity
  - cleavage
related_skills:
  - optical-properties
  - gem-testing-instruments
---

# Physical Properties

[Main content with sections, tables, and examples]

## References
- [Link to reference files]
```

### YAML Frontmatter Fields

| Field | Description |
|-------|-------------|
| `name` | Human-readable module name |
| `description` | When to activate this skill (trigger phrases) |
| `triggers` | Keywords and phrases that invoke this module |
| `related_skills` | Cross-references to other modules |
| `status` | Content status: `draft`, `review`, `complete` |
| `tags` | Categorization tags for filtering |

### Reference File Format

Reference files use Obsidian-compatible markdown with:

- YAML frontmatter for metadata
- Wiki-style links: `[[Crystal Systems]]`
- Embedded images: `![[diamond.svg|300]]`
- LaTeX math: `$$a_1 = a_2 = a_3$$`
- Tables for structured data

## How to Add New Modules

### 1. Create the Module Directory

```bash
mkdir -p skills/new-module/references
```

### 2. Create the SKILL.md File

Create `skills/new-module/SKILL.md` with the required frontmatter:

```markdown
---
name: New Module Name
description: Use this skill when the user asks about...
triggers:
  - keyword1
  - keyword2
related_skills:
  - existing-module
status: draft
---

# New Module Name

## Overview
[Introduction to the topic]

## Key Concepts
[Main content sections]

## Practical Applications
[How this knowledge is used]

## References
- [[reference-file-1]]
- [[reference-file-2]]
```

### 3. Add Reference Files

Create supporting reference files in the `references/` subdirectory:

```markdown
---
type: reference
module: new-module
topic: Specific Topic
status: draft
tags: [new-module, topic]
---

# Specific Topic

[Detailed content]
```

### 4. Update Related Modules

Add cross-references to existing modules that relate to your new content.

### 5. Test Links

Run the link checker to verify all internal links resolve:

```bash
./scripts/check-links.sh
```

### 6. Submit for Review

Create a pull request with your new module. Ensure:

- [ ] All required frontmatter fields are present
- [ ] Content follows the established style
- [ ] Internal links are valid
- [ ] Tables are properly formatted
- [ ] Examples are accurate and helpful

## Learn Content (YAML)

The `docs/learn/` tree contains 138 YAML articles consumed by [gemmology.dev](https://gemmology.dev) and structured as Astro content collections. Each file follows a typed schema (sections, callouts, tables, comparisons, subsections) and, since **v1.2.0**, carries structured citations.

### References block

Every article that makes factual claims declares its sources in a top-level `references:` array:

```yaml
references:
  - id: read-2014-gemmology
    kind: book
    authors:
      - family: "Read"
        given: "Peter G."
    title: "Gemmology"
    edition: "3rd"
    publisher: "Butterworth-Heinemann / Routledge"
    year: 2014
    doi: "10.4324/9780080507224"

  - id: palke-2019-origin-ruby
    kind: journal
    authors:
      - family: "Palke"
        given: "Aaron C."
    title: "Geographic origin determination of ruby"
    journal: "Gems & Gemology"
    year: 2019
    volume: 55
    issue: 4
    pages: "580–613"
    doi: "10.5741/gems.55.4.580"
```

| Field | Type | Required for kinds | Notes |
|-------|------|-------------------|-------|
| `id` | string (`/^[a-z0-9][a-z0-9-]*$/`) | all | Stable slug used by inline markers |
| `kind` | `book \| journal \| web \| standard` | all | No other values accepted |
| `authors` | `{ family, given }[]` | all except `web` | CSL-JSON-inspired |
| `title` | string | all | Source title |
| `year` | integer | all except `standard` | Publication year |
| `journal` | string | `journal` | Periodical name |
| `volume` / `issue` | int or string | `journal` (optional) | String accepted for compound issues (e.g. `"1–4"`) |
| `pages` | string | `journal` (optional) | Page range |
| `doi` | string | `book`, `journal` (optional) | Resolves via `doi.org/{value}` |
| `isbn` | string | `book` (optional) | Digits-only normalised |
| `publisher` / `edition` | string | `book` (optional) | |
| `url` | URL string | `web` (required), others (optional) | |
| `organization` | string | `standard` (optional) | E.g. `"ISO"`, `"LMHC"`, `"CIBJO"` |

### Inline `{cite:id}` markers

Cite a reference from anywhere inside a section, callout, item, subsection, or table caption using the `{cite:id}` syntax:

```yaml
sections:
  - title: Diagnostic Inclusions
    content: |
      Marble-hosted Burmese ruby characteristically shows short, dense rutile
      silk inclusions oriented along the three crystallographic axes
      {cite:hughes-2017-ruby-sapphire}. Mong Hsu material instead shows
      blue-cored colour zoning indicative of high-iron primary growth
      {cite:hanni-1990-kashmir}.
```

The website pipeline resolves each marker to a numbered superscript (`<sup>[1]</sup>`) that backlinks to the bibliography section at the article footer. Dangling ids (a marker pointing at no `references:` entry) are a build-time error.

### Current scope (v1.2.0)

- 138 articles annotated across 8 categories
- 623 inline `{cite:id}` markers
- Top sources: Read (2014) *Gemmology*, Hughes (2017) *Ruby & Sapphire*, Palke et al. (2019) origin trilogy, Nassau (2001) *Color*, Gübelin & Koivula *Photoatlas* v1 & v2

Release notes: https://github.com/gemmology-dev/gemmology-knowledge/releases/tag/v1.2.0

## Integration with gemmology-plugin

The knowledge modules in this repository integrate with the [gemmology-plugin](https://github.com/gemmology-dev/gemmology-plugin) Claude Code plugin to provide:

### Skills

Each module in `skills/` corresponds to a Claude Code skill that can be invoked during conversations:

```
User: What causes the colour in ruby?
Claude: [Activates chemical-properties skill]
        Ruby's red colour is caused by chromium (Cr3+) substituting...
```

### Automatic Activation

Skills are automatically activated based on trigger keywords in user queries. The `triggers` field in each SKILL.md defines the activation patterns.

### Cross-Module References

Skills can reference each other to provide comprehensive answers:

```
User: How do I identify a natural ruby?
Claude: [Activates multiple skills: inclusions-fingerprints,
         treatments-enhancements, gem-testing-instruments]
```

### Knowledge Retrieval

The plugin retrieves relevant content from reference files to provide accurate, curriculum-aligned information.

## Website

The documentation site is deployed to [knowledge.gemmology.dev](https://knowledge.gemmology.dev).

### Building Locally

```bash
# Generate documentation from skills
python scripts/generate_docs.py

# Preview the site (requires Jekyll or mkdocs)
cd docs && bundle exec jekyll serve
# or
mkdocs serve
```

### Features

- Full-text search across all modules
- Interactive glossary with definitions
- Progress tracking for study guides
- Mobile-friendly responsive design

## Contributing

We welcome contributions to improve and expand the knowledge base.

### Content Guidelines

1. **Accuracy**: All content should align with FGA curriculum and established gemmological standards
2. **Clarity**: Write for both beginners and professionals
3. **Examples**: Include practical examples and real-world applications
4. **Sources**: Reference authoritative gemmological texts where appropriate
5. **Consistency**: Follow the established format and style

### Review Process

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request
5. Address review feedback

Content is reviewed for:
- Technical accuracy
- Curriculum alignment
- Writing quality
- Proper formatting

## Related Repositories

| Repository | Description |
|------------|-------------|
| [gemmology-plugin](https://github.com/gemmology-dev/gemmology-plugin) | Claude Code plugin that consumes this knowledge |
| [mineral-database](https://github.com/gemmology-dev/mineral-database) | Gemstone property database |
| [cdl-parser](https://github.com/gemmology-dev/cdl-parser) | Crystal Description Language parser |
| [crystal-renderer](https://github.com/gemmology-dev/crystal-renderer) | Crystal visualization engine |
| [gemmology.dev](https://github.com/gemmology-dev/gemmology.dev) | Main project website |

## License

This work is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/) (CC BY-SA 4.0).

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit and indicate if changes were made
- **ShareAlike** — If you remix or build upon the material, you must distribute your contributions under the same license

See [LICENSE](LICENSE) for full details.

## Attribution

Content in this repository is based on the curriculum of the Gemmological Association of Great Britain (Gem-A) and other authoritative gemmological sources. This is an educational resource and is not affiliated with or endorsed by Gem-A.

### Acknowledgements

- Gem-A Foundation and Diploma curriculum
- GIA Gemological Institute
- CIBJO terminology standards
- Contributing gemmologists and educators

## Links

- [Documentation](https://knowledge.gemmology.dev)
- [Main Project](https://gemmology.dev)
- [GitHub Organization](https://github.com/gemmology-dev)
- [Issue Tracker](https://github.com/gemmology-dev/gemmology-knowledge/issues)
