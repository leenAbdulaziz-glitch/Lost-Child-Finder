# Lost Child Finder

An intelligent real-time system for detecting and alerting when a child becomes separated from their guardian in public spaces.

---

## Project Idea

Lost Child Finder is a computer vision system designed to improve public safety by monitoring children in live video streams and detecting the moment they separate from their guardian. The system targets crowded environments such as malls, parks, and public events where a child can wander off within seconds.

**How It Works:**
1. Detect all persons in each video frame using a YOLOv8 model trained to distinguish between children and adults.
2. Track each individual across frames using ByteTrack, assigning a unique ID to every person.
3. Pair each child with the nearest adult upon first detection (assumed guardian).
4. Continuously measure the pixel distance between the child and their assigned guardian and convert it to an estimated real-world distance in meters.

**Alert System:**
| State | Distance | Color |
|-------|----------|-------|
| Safe | ≤ 2.0 m | Green |
| Warning | 2.0 – 2.5 m | Yellow |
| Lost / Alert | > 2.5 m | Red + Banner |

---

## Technologies Used

- **YOLOv8n** — person detection and classification (Child / Adult)
- **ByteTrack** — multi-object tracking across frames
- **OpenCV** — video processing and visualization
- **Supervision** — computer vision utilities
- **Google Colab** — training and inference environment

---

## Dataset

| Dataset | Source | Total Images |
|---------|--------|-------------|
| Children vs Adults (2024) | Roboflow — a-4euhx | 999 |
| Children vs Adults (2025) | Roboflow — aghababa | 797 |

**Training split (Dataset 2024):**

| Split | Images |
|-------|--------|
| Train | ~797 |
| Validation | 102 |
| Test | ~100 |

---

## Results

### Training Results

| Metric | Value |
|--------|-------|
| mAP50 | 0.892 |
| mAP50-95 | 0.662 |
| Precision | 0.763 |
| Recall | 0.855 |

### Evaluation Results (Validation Set — 102 images)

| Metric | Value |
|--------|-------|
| mAP50 | 0.341 |
| mAP50-95 | 0.076 |
| Precision | 0.411 |
| Recall | 0.564 |

**Per-class results:**

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| Adult | 0.374 | 0.642 | 0.473 |
| Child | 0.447 | 0.486 | 0.466 |

---

## Team

| Name | Role |
|------|------|
| **Abdullah** | Model training, system development & evaluation |
| **Leen** | Model training, system development & evaluation |
