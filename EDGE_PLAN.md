# Edge Deployment Plan

## Goal

Deploy the system on mobile / on-device environments.

---

## Model Choice

* TF-IDF + XGBoost
* Lightweight and efficient

---

## Model Size

* TF-IDF vocabulary: ~3–5 MB
* XGBoost models: ~2–10 MB
* Total: ~10–15 MB

---

## Latency

* Feature extraction: ~10 ms
* Model inference: ~5–10 ms
* Total: < 30 ms

---

## Deployment Strategy

1. Export models
2. Use ONNX / lightweight runtime
3. Run inference locally

---

## Optimizations

* Quantization
* Reduce TF-IDF features if needed
* Batch size = 1

---

## Tradeoffs

| Approach     | Pros                 | Cons          |
| ------------ | -------------------- | ------------- |
| TF-IDF       | Fast                 | Less semantic |
| Transformers | Better understanding | Heavy         |

---

## Offline Capability

* Fully functional without internet
* No dependency on APIs

---

## Robustness Handling

### Short Text

* fallback to metadata

### Missing Values

* imputation

### Uncertainty

* safe recommendations

---

## Future Improvements

* Tiny transformer models (DistilBERT)
* Personalized on-device learning
* Incremental updates

---

## Conclusion

The system is designed for **fast, lightweight, and reliable on-device inference**, making it suitable for real-world deployment.
