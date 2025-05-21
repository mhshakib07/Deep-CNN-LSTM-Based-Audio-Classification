# DCNN-LSTM Hybrid for Urban Sound Classification  

**Achieving 93.19% accuracy on UrbanSound8K** by combining Deep CNN, LSTM, and stacked spectral features with data augmentation.  

---

## 📌 Key Features  
- **Hybrid Architecture**: Integrates **3-layer DCNN** (spatial features) with **2-layer LSTM** (temporal dependencies).  
- **Feature Engineering**: Extracts **169 spectral features** (MFCC, Mel-spectrogram, Chroma STFT, Tonnetz, ZCR, RMS).  
- **Data Augmentation**: Noise injection, pitch/time shifting to reduce overfitting.  
- **State-of-the-Art Performance**: Outperforms GoogleNet (93%) and DenseNet (87.42%) on UrbanSound8K.  

---

## 🛠️ Methodology  
### **Model Architecture**  
| Component       | Configuration                          |  
|-----------------|----------------------------------------|  
| **DCNN**        | 3x Conv2D (64-128 filters, ReLU, Dropout=0.3) + MaxPooling |  
| **LSTM**        | 2x LSTM (128 units, Dropout=0.2) + TimeDistributed Dense  |  
| **Optimizer**   | Adam (β₁=0.9, β₂=0.999)               |  
| **Input**       | Spectrograms (STFT-transformed audio)  |  

### **Data Pipeline**  
1. **Augmentation**:  

   **Librosa-based augmentation** 
   augmented_audio = librosa.effects.time_stretch(y, rate=**0.8**)  # Time stretching
   
2. **Feature Extraction**
   
      We extract **169 spectral features**

3. **Training:** **80%** train, **10%** validation, **10%** test with early stopping (patience=5).

## 📊 Benchmark Results

| Model                  | Accuracy | Dataset       |
|------------------------|----------|---------------|
| **Proposed DCNN-LSTM** | 93.19%   | UrbanSound8K  |
| GoogleNet              | 93.00%   | UrbanSound8K  |
| Conv1D + Gammatone     | 89.00%   | UrbanSound8K  |

**Key Insight**: Our hybrid DCNN-LSTM model outperforms comparable architectures, achieving state-of-the-art results on UrbanSound8K.
