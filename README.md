# AAROHAN — Aerial SAR Review Pipeline

Human-in-the-loop post-flight person detection for search & rescue review.  
**SEVA FIRST 2026 · INDRA NAT-002 · Golu Kumar (IIM Sambalpur)**

## Pipeline
`Video/image → OpenCV sampling → YOLO (tiled) → human Confirm/Reject/Flag → CSV audit → metrics`

## Benchmark (HERIDAL test, 101 images, IoU ≥ 0.5, Apple M4)

| Model | conf | Precision | Recall | F1 |
|-------|------|-----------|--------|-----|
| Baseline COCO YOLO11s | 0.10 | 52.4% | 36.2% | 0.43 |
| Fine-tuned AAROHAN | 0.40 | 63.6% | 65.9% | 0.65 |

Test images were not used in fine-tuning. Operating threshold 0.40 chosen after comparing F1.

## Scope
- Software-only, laptop, post-flight
- Human is final authority (Confirm / Reject / Flag)
- No autonomous flight · no life-saving or rescue-time claim

## Author note
Pipeline uses open-source YOLO and OpenCV. Configuration, evaluation protocol, fine-tune runs, and human-review workflow were executed and measured by the author on Apple M4. Run artefacts are logged under `~/AAROHAN/runs/`.

## Evidence pack
https://drive.google.com/drive/folders/1O6UJq8gmZfcl3zJALZnsRx0T6B5FYN6Q

## Run
Open `AAROHAN.ipynb` and follow cells in order:  
Setup → Sample → Data → Detect → Review → Audit → Metrics  
(Fine-tune cell is optional; flags default off after training.)
