# 🧠 Scene Graph Generation from Images & Videos

This project explores **Scene Graph Generation** for better understanding of both static images and dynamic videos. We extract object-level interactions to produce meaningful triplets like:

> `person - holding - bottle`  
> `laptop - on - bed`

By combining **YOLO** for object detection and a custom **relation classifier**, we build a structured representation of visual scenes.

---

## 📸 What is a Scene Graph?

A **scene graph** is a graphical representation of a visual scene where:
- **Nodes** = Objects (e.g., person, bottle, laptop)
- **Edges** = Relationships (e.g., beside, holding, touching)

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/SceneGraph.png/640px-SceneGraph.png" width="500"/>
  <br/><em>Illustration of a Scene Graph (Source: Wikipedia)</em>
</p>


# 🧠 Scene Graph Generation from Images & Videos

This project explores **Scene Graph Generation** for better understanding of both static images and dynamic videos. We extract object-level interactions to produce meaningful triplets like:

> `person - holding - bottle`  
> `laptop - on - bed`

By combining **YOLO** for object detection and a custom **relation classifier**, we build a structured representation of visual scenes.

---

## 📸 What is a Scene Graph?

A **scene graph** is a graphical representation of a visual scene where:
- **Nodes** = Objects (e.g., person, bottle, laptop)
- **Edges** = Relationships (e.g., beside, holding, touching)

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/SceneGraph.png/640px-Scenegraph.png" width="500"/>
  <br/><em>Illustration of a Scene Graph (Source: Wikipedia)</em>
</p>

---

## 🔍 Case Study: Dining Table Scene

### Input Image
<p align="center">
  <img src="./test_image.png" width="500"/>
  <br/><em>A collaborative workspace scene with multiple people around a dining table</em>
</p>

### Detection Output
<p align="center">
  <img src="./test_image_output.png" width="500"/>
  <br/><em>YOLO detection with bounding boxes identifying objects and their spatial relationships</em>
</p>
### Transcript for the Output
<p align="center">
  <img src="./transcript" width="500"/>
  <br/><em>YOLO detection with bounding boxes identifying objects and their spatial relationships</em>
</p>

### Extracted Scene Graph
---

## 🎥 Demo Snapshots

| Frame | Scene Graph |
|-------|-------------|
| ![Frame 1](./frame1.png) | `bottle - beside - laptop`<br>`person - touching - laptop` |
| ![Frame 2](./frame2.png) | `person - holding - bottle`<br>`person - lying on - bed`<br>`person - holding - vase` |
| ![Frame 3](./frame3.png) | `person - holding - bottle`<br>`person - beside - person`<br>`bottle - beside - person` |
| ![Frame 4](./frame4.png) | `laptop - in front of - person`<br>`person - beside - person`<br>`person - touching - laptop` |
| ![Frame 6](./frame6.png) | `person - touching - laptop`<br>`bottle - beside - laptop`<br>`laptop - in front of - person` |
| ![Frame 7](./frame7.png) | `person - holding - phone`<br>`laptop - on - bed`<br>`person - in front of - wall` |

> 🔄 See [Media1.mp4](./Media1.mp4) for the full video-based scene graph generation.

---

## 🏗️ Architecture

### 1. **Object Detection**
- **YOLOv5 / YOLOv8**
- Pre-trained on COCO
- Fast and real-time inference

### 2. **Relation Prediction**
- ROI Align features for object pairs
- Relative spatial encoding
- Word embeddings (GloVe)
- MLP-based relation classifier

---

## 📦 Dataset

We used the **Panoptic Scene Graph (PSG)** dataset:
- 49,000+ richly annotated images
- 330+ unique relationships
- COCO-style object categories
- `<Subject, Predicate, Object>` triplets

---

## 📊 Metrics

We evaluate with:
- **Recall@50, Recall@100**
- **Mean Recall** for rare relationships

| Model    | mR@50 | mR@100 |
|----------|-------|--------|
| Motifs   | 6.6   | 7.9    |
| VCTree   | 5.8   | 6.6    |
| PE-NET   | 16.7  | 18.8   |
| **Ours** | 12.4  | 14.5   |

> ⚡ Our model is real-time optimized and suitable for video understanding.

---

## 🧠 Applications

- **Surveillance & Monitoring**: Detect interactions in live feed
- **Human-Robot Interaction**: Understand commands via visual context
- **Video Captioning / Summarization**
- **Augmented Reality Anchors**

---

## 🔮 Future Work

- ✅ Action understanding: e.g., "Person is picking up bottle"
- ✅ Tracking across frames for temporal graphs
- 🚧 Integrate large vision-language models for open-world relationships

---

## 👨‍💻 Contributors

- Randhi Nagasurya (2021ITB015)  
- Somireddy Naveen Kumar Reddy (2021ITB085)  
- Moru Sai Tirupathi (2021ITB086)  

Under the guidance of **Dr. Arindam Biswas**,  
Department of Information Technology,  
**IIEST Shibpur**

---

## ⚙️ Installation

```bash
git clone https://github.com/<your-username>/scene-graph-generator.git
cd scene-graph-generator
pip install -r requirements.txt
