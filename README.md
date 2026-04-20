# Debussy OMR Dataset

A dataset of handwritten music score images paired with MusicXML ground-truth transcriptions, drawn from autograph manuscripts by **Claude Debussy** (1862–1918) held at the [Bibliothèque nationale de France (BnF)](https://gallica.bnf.fr/).

## Dataset Overview

| Property | System-Level | Full-Page |
|---|---|---|
| Samples | 561 | 101 |
| Documents | 37 | 37 |
| Image format | JPEG | JPEG |
| Transcription format | MusicXML 4.0 | MusicXML 4.0 |

The dataset is released in two complementary versions:

- **System-level** (`system-level/`): Individual image crops, each paired with a MusicXML file containing exactly one grand-staff piano system.
- **Full-page** (`full-page/`): Full-page images, each paired with a MusicXML file encoding all systems on the page.

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
- **Color-coded annotations**: Manuscript-specific phenomena are encoded using color attributes:
  - **Magenta (`#FF40FF`)**: Beat repeat symbols
  - **Yellow**: Non-orthodox repeat signs
  - **Cyan**: Flat trills
  - **Brown**: Sharp trills
  - **Green**: Erasures and editorial annotations
- **Layout**: System breaks in full-page files use `<print new-system="yes"/>`.
- **Dynamics**: Only conventional dynamics are transcribed; idiosyncratic textual instructions are excluded.

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
