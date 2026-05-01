# Model Card: Casting Inspection Baseline

## Intended Use

This workflow demonstrates a part-level OK/defective screening gate for controlled casting imagery in a pilot inspection setting.

## Non-Use

This project is not a final production release, safety certification package, supplier chargeback system, severity-scoring system, or localized defect detector. It should not be used for production decisions without plant-specific validation and quality engineering approval.

## Model and Inputs

- Architecture: ResNet18 transfer-learning classifier.
- Input type: single casting image.
- Output: OK or defective decision, defect probability, and threshold-based decision metadata.
- Preprocessing: OpenCV grayscale normalization, optional CLAHE, deterministic resizing to 224 x 224, and ImageNet-style tensor normalization.

## Embedded Run Summary

| Metric | Reported Result |
| --- | --- |
| Final test images | 571 |
| Test defect recall | 1.000000 |
| Test false accepts | 0 |
| Test false rejects | 4 |
| Operating threshold | 0.031778 |
| Batch-size-1 p95 latency | 8.27 ms |

## Validation Controls

The notebook includes image readability checks, final split leakage checks, exact SHA-1 duplicate filtering, near-duplicate warnings, threshold selection on validation data, ROC/PR/calibration review, confidence intervals, error review, Grad-CAM diagnostics, and fail-safe inference behavior.

## Known Limitations

- Dataset labels are image-level binary labels, not localized defect annotations.
- The public dataset may contain acquisition artifacts and repeated or augmented visual patterns.
- Metrics are from a public dataset split after leakage governance, not from a plant-specific holdout.
- Exported artifact parity was not completed in the embedded run because artifact saving and ONNX export were disabled.
- Drift monitoring is based on lightweight image-quality features and should be treated as an alerting aid, not an automatic retraining trigger.

## Release Status

Pilot/reference ready for technical review. Not production approved.
