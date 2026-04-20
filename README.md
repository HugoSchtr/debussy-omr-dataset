# Debussy OMR Dataset

A dataset of handwritten music score images paired with MusicXML ground-truth transcriptions, drawn from autograph manuscripts by **Claude Debussy** (1862–1918) held at the [Bibliothèque nationale de France (BnF)](https://gallica.bnf.fr/).

## Dataset Overview

The dataset is released in two complementary versions:

- **System-level** (`system-level/`): Individual image crops, each paired with a MusicXML file containing exactly one grand-staff piano system.
- **Full-page** (`full-page/`): Full-page images, each paired with a MusicXML file encoding all systems on the page.

### Corpus

| Property | Value |
|---|---|
| Documents (piano / voice+piano / double piano / mixed) | 37 (25 / 6 / 5 / 1) |

### Full-Page Version (101 pages, 492 systems)

| Property | Value |
|---|---|
| Measures | 2,604 |
| 2-stave (piano) | 283 |
| 3-stave (extra stave / voice+piano) | 128 (44 / 84) |
| 4-stave (double piano / extra stave) | 81 (73 / 8) |

### System-Level Version (561 systems)

| Property | Value |
|---|---|
| Measures | 3,039 |
| Grand staff (2-stave) | 494 |
| 3-stave (extra stave) | 55 |
| 4-stave (extra stave) | 12 |

### MusicXML Vocabulary (264 classes)

| Category | Count |
|---|---|
| Pitches | 172 |
| Note durations / Rest durations | 8 / 10 |
| Accidentals | 5 |
| Clefs (G2, F4) | 2 |
| Key signatures | 15 |
| Time signatures | 16 |
| Dynamics / Hairpins | 15 / 2 |
| Articulations / Ornaments | 7 / 4 |
| Fermatas / Arpeggiates | 1 / 2 |
| Barlines | 5 |

### Element Instances

| Element | Sys. Total | Sys. Avg | FP Total | FP Avg |
|---|---|---|---|---|
| Pitched notes | 33,054 | 58.9 | 34,025 | 336.9 |
| Rests | 4,854 | 8.7 | 5,029 | 49.8 |
| Chord notes | 12,438 | 22.2 | 12,438 | 123.1 |
| Accidentals | 7,989 | 14.2 | 8,134 | 80.5 |
| Ties | 2,733 | 4.9 | 2,767 | 27.4 |
| Slurs | 4,649 | 8.3 | 4,723 | 46.8 |
| Tuplets | 2,419 | 4.3 | 2,479 | 24.5 |
| Dynamics | 1,239 | 2.2 | 1,287 | 12.7 |
| Hairpins | 1,096 | 2.0 | 1,146 | 11.3 |
| Articulations | 5,720 | 10.2 | 5,871 | 58.1 |

### Manuscript-Specific Annotations

| Type | Total (FP) | Avg / page | % pages | Total (Sys) | Avg / sys | % sys |
|---|---|---|---|---|---|---|
| Erasures | 338 | 3.35 | 18.8 | 338 | 0.60 | 6.2 |
| Beat repeats | 187 | 1.85 | 16.8 | 187 | 0.33 | 5.3 |
| Non-orthodox repeats | 135 | 1.34 | 4.0 | 135 | 0.24 | 1.4 |
| Altered trills | 19 | 0.19 | 7.9 | 19 | 0.03 | 1.8 |
| Invisible elements | 920 | 9.11 | 82.2 | 908 | 1.62 | 39.0 |
| **All** | **1,599** | **15.83** | **85.1** | **1,587** | **2.83** | **46.3** |

## Repository Structure

```
debussy-omr-dataset/
├── README.md
├── LICENSE
├── system-level/
│   └── <document_id>/
│       └── <folio>/
│           ├── <document_id>_f<folio>_system_<nn>.jpg
│           └── <document_id>_f<folio>_system_<nn>.musicxml
└── full-page/
    └── <document_id>/
        ├── <document_id>_f<folio>.jpg
        └── <document_id>_f<folio>.musicxml
```

## Transcription Guidelines

Transcriptions were produced using MuseScore Studio 4 by a single annotator with musicological training.

### Encoding Conventions

- **Invisible elements**: Musical elements structurally necessary for valid MusicXML but not visually present in the manuscript (e.g., repeated clefs) are flagged with `print-object="no"`.
- **Layout**: System breaks in full-page files use `<print new-system="yes"/>`.
- **Dynamics**: Only conventional dynamics are transcribed; idiosyncratic textual instructions are excluded.

### Colour-Coded Annotations

Manuscript-specific phenomena that fall outside MuseScore's standard editing interface are encoded using colour attributes:

| Colour | Code | Meaning | Count |
|---|---|---|---|
| Green | `#00F900` | Erasure / editorial | 338 |
| Magenta | `#FF40FF` | Beat repeat | 187 |
| Yellow | `#FFFB00` | Non-orthodox repeat | 135 |
| Brown | `#AA7942` | Sharp trill | 28 |
| Cyan | `#00FDFF` | Flat trill | 6 |
| Blue | `#0433FF` | Natural trill | 4 |

## Source

The manuscript images originate from the **Gallica** digital library of the BnF and were accessed through the IIIF protocol. Documents date from 1887 to 1915 and include solo piano, four-hand piano, and piano-voice layouts.

## License

This dataset is released under the [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/) license.

## Citation

If you use this dataset, please cite:

```bibtex
@misc{debussy_omr_dataset,
  title={Debussy OMR Dataset},
  author={Hugo Scheithauer},
  year={2026},
  url={https://github.com/HugoSchtr/debussy-omr-dataset}
}
```

## Related Resources

- [HugoSchtr/debussy-omr-system-lvl](https://huggingface.co/datasets/HugoSchtr/debussy-omr-system-lvl) — HuggingFace version (system-level)
- [HugoSchtr/debussy-omr-fullpage-lvl](https://huggingface.co/datasets/HugoSchtr/debussy-omr-fullpage-lvl) — HuggingFace version (full-page)
