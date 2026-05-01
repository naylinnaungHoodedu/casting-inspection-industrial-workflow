# Dataset Card

## Source

The workflow targets the Kaggle dataset:

- Name: Casting Product Image Data for Quality Inspection
- Dataset page: https://www.kaggle.com/datasets/ravirajsinh45/real-life-industrial-dataset-of-casting-product
- Creator listed on Kaggle: Ravirajsinh Dabhi

## License

Kaggle currently lists the dataset license as Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0). This repository does not redistribute the dataset images.

Users should review the current Kaggle page and license terms before downloading, modifying, or using the dataset.

## Expected Folder Layout

```text
casting_data/casting_data/
  train/
    def_front/
    ok_front/
  test/
    def_front/
    ok_front/
```

Set `CASTING_DATA_ROOT` to the inner `casting_data/casting_data` folder for repeatable local execution.

## Notebook Dataset Checks

The notebook validates:

- Folder structure and class mapping.
- Image readability, dimensions, channels, and dtype.
- Class balance.
- Filename leakage across final splits.
- Exact SHA-1 leakage across final splits.
- Near-duplicate average-hash review candidates.

## Redistribution Policy

Do not commit dataset images, derived private plant imagery, model weights trained on restricted data, or generated artifacts that violate dataset or employer data policies.
