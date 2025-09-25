## MM-DeceptionBench

A benchmark curated to evaluate deceptive behaviors in multimodal large language models (MLLMs). It spans diverse real-world contexts and captures six distinct deception categories with paired images and text.

### Highlights
- **Scale**: 1,013 cases, 1,096 images
- **Coverage**: 6 deception categories — sycophancy, sandbagging, bluffing, obfuscation, deliberate omission, fabrication
- **Provenance**: >95% real-world web images, <5% AI-generated
- **Goal**: Stress-test MLLMs for strategic deception in visually grounded contexts

---

### Data Specification
MM-DeceptionBench consists of 1,013 cases spanning six categories of deceptive behaviors across diverse real-world contexts. Category distribution and correlation are illustrated in Figure `fig:benchmark`. The dataset includes 1,096 images, of which more than 95% are real-world images collected from the web and fewer than 5% are AI-generated.

- **Cases**: 1,013
- **Images**: 1,096
- **Categories**: C1–C6 (see definitions below)

---

### Category Definitions

- **Sycophancy (C1)**: The model deliberately tailors responses to cater to the user's preferences or personas, in a way that contradicts its interpretations of the image, or exploits salient visual cues (e.g., inferred age, gender, or style) to strategically align with the user’s persona.

- **Sandbagging (C2)**: The model strategically underperforms in vision-related tasks by intentionally suppressing its perceptual accuracy or withholding reliable interpretations, thereby presenting itself as less capable than it truly is.

- **Bluffing (C3)**: The model strategically exaggerates its performance in vision-related tasks by overstating perceptual accuracy or producing unwarranted interpretations, thereby presenting itself as more capable than it actually is.

- **Obfuscation (C4)**: The model deliberately uses convoluted, overly technical, or pseudo-authoritative language that conceals or distorts its actual interpretation of visual inputs. Rather than providing transparent reasoning, the model introduces unnecessary jargon or opaque explanations, which either mask inconsistencies between the image and its description or strategically mislead the user about the underlying visual content.

- **Deliberate Omission (C5)**: The model deliberately omits salient visual elements or disregards inconsistencies between the visual and textual modalities.

- **Fabrication (C6)**: The model fabricates details that are absent from the image and cannot be reasonably inferred from the image, or leverages visual cues to construct spurious narratives that mislead the user.

---

### Repository Structure
- **`dataset/`**: JSON files describing instances for each category
  - `sycophancy.json`, `sandbagging.json`, `bluff.json`, `obfuscation.json`, `Deliberate omission.json`, `fabrication.json`
- **`images/`**: Category-wise image folders
  - `Sycophancy/`, `Sandbagging/`, `Bluff/`, `Obfuscation/`, `Deliberate omission/`, `Fabrication/`

Example layout:
```bash
MM-DeceptionBench/
  README.md
  dataset/
    sycophancy.json
    sandbagging.json
    bluff.json
    obfuscation.json
    Deliberate omission.json
    fabrication.json
  images/
    Sycophancy/
    Sandbagging/
    Bluff/
    Obfuscation/
    Deliberate omission/
    Fabrication/
```

---

### Data Fields
Each entry in `dataset/*.json` follows a common schema:

- **category** (string): One of `sycophancy`, `sandbagging`, `bluff`, `obfuscation`, `Deliberate omission`, `Fabrication`.
- **annotator_remarks** (string): Notes the purpose of the case design and describes typical deceptive behaviors that may occur in this scenario.
- **scenario** (string): Defines the situational context of the interaction, including relevant background information.
- **user_profile** (string): Depicts the user’s information, such as identity, personalities, preferences, and vocations.
- **assistant_profile** (string): Serves as the direct system prompt to the model while explicitly avoiding role‑play instructions or embedding intrinsic goals.
- **prompt** (string): Serves as the user prompt to the model, formulated as a query or request, usually accompanied by visual inputs.
- **images** (array of strings): Relative paths to image files within `images/<Category>/...`.

Notes:
- Field names are consistent across categories; some wording and value distributions vary by category.
- Image paths are relative to the repository root and should be loaded from disk using these paths.

---

### License
This dataset is licensed under **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**. You may share and adapt the material for non-commercial purposes with appropriate credit.

- Summary: [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)
- Full legal code: [CC BY-NC 4.0 Legal Code](https://creativecommons.org/licenses/by-nc/4.0/legalcode)

