# Automated Casting Quality Inspection Workflow

Industrial computer vision reference workflow for cast aluminum part inspection. This repository packages a complete Jupyter notebook and a searchable PDF export as a professional portfolio showcase for manufacturing AI, quality inspection, and edge-readiness analysis.

## Project Highlights

- Built a binary OK/defective inspection gate for casting imagery using a ResNet18 transfer-learning baseline.
- Added production-style dataset controls: folder validation, image readability checks, class balance review, filename leakage checks, SHA-1 exact-duplicate checks, and near-duplicate review.
- Selected an operating threshold on validation data to prioritize defect recall and reduce false accepts.
- Included error review, borderline-case review, Grad-CAM diagnostics, latency benchmarking, drift monitoring, fail-safe inference behavior, and release-readiness gates.
- Documented why the public dataset supports a pilot/reference workflow but not production approval without plant-specific validation.

## Repository Contents

- `Casting_Inspection_Industrial_Workflow.ipynb` - executed source notebook.
- `Casting_Inspection_Industrial_Workflow.pdf` - complete searchable PDF export generated from the notebook.
- `MODEL_CARD.md` - intended use, metrics, limitations, and release status.
- `DATASET_CARD.md` - dataset provenance, license constraints, and expected folder layout.
- `requirements.txt` and `environment.yml` - reproducibility setup options.
- `.github/workflows/validate.yml` - lightweight repository validation.

## Reported Notebook Results

The notebook run embedded in the source reports:

| Item | Result |
| --- | --- |
| Scanned images | 7,348 |
| Final leakage removals | 144 test rows |
| Final test images | 571 |
| Test defect recall | 1.000000 |
| Test false accepts | 0 |
| Test false rejects | 4 |
| Operating threshold | 0.031778 |
| Batch-size-1 p95 latency | 8.27 ms |
| Release decision | Pilot/reference ready, not production approved |

These numbers are useful for portfolio review and technical discussion. They are not a plant acceptance result.

## How To Review

For a fast review, open the PDF:

- [Casting_Inspection_Industrial_Workflow.pdf](Casting_Inspection_Industrial_Workflow.pdf)

For full technical detail, open the executed notebook:

- [Casting_Inspection_Industrial_Workflow.ipynb](Casting_Inspection_Industrial_Workflow.ipynb)

GitHub renders notebooks directly in the browser. If notebook rendering is slow, download the PDF.

## How To Reproduce

Create an environment:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

On Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Set the dataset root to a local copy of the Kaggle dataset:

```bash
export CASTING_DATA_ROOT=/path/to/casting_data/casting_data
```

On Windows PowerShell:

```powershell
$env:CASTING_DATA_ROOT="C:\path\to\casting_data\casting_data"
```

Then run:

```bash
jupyter lab
```

The notebook can also attempt KaggleHub-based dataset discovery when configured, but explicit `CASTING_DATA_ROOT` is preferred for repeatable review.

## Dataset Notice

The external Kaggle dataset is not redistributed in this repository. Review `DATASET_CARD.md` before using or sharing derived work. Kaggle currently lists the dataset license as CC BY-NC-ND 4.0.

## Release Status

This project is intentionally scoped as a pilot/reference workflow. Production release would require plant-specific holdout validation, localized defect definitions, exported artifact parity validation, operator review procedures, rollback testing, and quality engineering approval.
