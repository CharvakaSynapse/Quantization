# Quantization-Aware Training with Knowledge Distillation

I recently tackled my first serious experiment with **Quantization-Aware Training (QAT)** to compress deep learning models while retaining performance. The experiments used **ResNet-50 on the CIFAR-100 dataset**. Here’s how the three approaches stacked up:

### 🧪 Approaches Compared

1. **QAT:** Standard 8-bit training that simulates INT8 operations during the forward pass.

2. **QAT + KD:** Combines QAT with knowledge distillation using a full-precision teacher model.

3. **QAT + EntKD:** An experimental variation where the distillation temperature adapts based on the entropy of the teacher’s output — a rarely used but promising idea. Encouragingly, it delivers repeatable improvements in both vanilla and augmentation-enhanced training pipelines.

---

### 🔍 Key Insights

- **🚀 Inference Speed:** INT8 quantized models run ~2× faster than FP32 counterparts.
- **📈 Accuracy Gains:** All QAT variants slightly outperform the FP32 baseline.
- **♻️ Entropy-Aware Distillation:** Entropy-conditioned temperature in EntKD is easy to implement and can generalize across distillation settings.

  ![QAT vs FP32 Comparison](compare.png)

---

### 📦 Future Plans

I’m working on exporting the QAT + EntKD model to **ONNX** for wider deployment and hardware acceleration. This will support lower-latency inference on edge devices and embedded systems.

---

