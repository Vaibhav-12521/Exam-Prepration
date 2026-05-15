# 🚀 IMAGE PROCESSING — LAST-MINUTE REVISION SHEET (1-Hour Read)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6105 | **Sem VI**

> Read this entire file in the **last hour before exam**. Everything important is condensed here.

---

## 📋 1. ALL FORMULAS (Memorize Cold)

### Image Fundamentals
- **Image function:** f(x, y) where 0 ≤ x ≤ M−1, 0 ≤ y ≤ N−1, 0 ≤ f ≤ L−1
- **Image formation:** f(x, y) = i(x, y) × r(x, y) — illumination × reflectance
- **Quantization levels:** L = 2^k (k = bits per pixel)
- **Storage:** M × N × k bits

### Gray-Level Transformations
- **Negative:** s = L − 1 − r → for 8-bit: s = 255 − r
- **Log:** s = c · log(1 + r) — compresses dynamic range
- **Power-law (Gamma):** s = c · r^γ — γ<1 brightens, γ>1 darkens
- **Threshold:** s = 0 if r<T, else L−1

### Histogram
- **Histogram:** h(r_k) = n_k
- **Normalized:** p_r(r_k) = n_k / MN
- **CDF:** cdf(r_k) = Σ_{j=0..k} p_r(r_j)
- **HE mapping:** s_k = (L − 1) · cdf(r_k)

### Spatial Filtering
- **Convolution:** g(x, y) = ΣΣ w(s, t) · f(x+s, y+t)
- **Gradient magnitude:** |∇f| = √(G_x² + G_y²) ≈ |G_x| + |G_y|
- **Gradient direction:** θ = arctan(G_y / G_x)
- **Laplacian:** ∇²f = f(x+1,y) + f(x-1,y) + f(x,y+1) + f(x,y-1) − 4f(x,y)
- **Unsharp masking:** g = f + k(f − f_blurred)

### Distance Measures
- **Euclidean:** D_e = √((x − s)² + (y − t)²)
- **City-block:** D_4 = |x − s| + |y − t|
- **Chessboard:** D_8 = max(|x − s|, |y − t|)

### Image Restoration
- **Degradation (spatial):** g(x, y) = h(x, y) * f(x, y) + η(x, y)
- **Degradation (frequency):** G(u, v) = H(u, v) · F(u, v) + N(u, v)
- **Inverse filter:** F̂(u, v) = G(u, v) / H(u, v)
- **Wiener filter:** F̂ = [H* / (|H|² + S_η/S_f)] · G
- **Motion blur PSF:** h(x, y) = 1/L for 0 ≤ x ≤ L, y = 0

### Noise Filters
- **Arithmetic mean:** f̂ = (1/mn) Σ g
- **Geometric mean:** f̂ = (Π g)^(1/mn)
- **Harmonic mean:** f̂ = mn / Σ (1/g)
- **Contra-harmonic:** f̂ = Σg^(Q+1) / Σg^Q  (Q>0 removes pepper; Q<0 removes salt)
- **Median:** f̂ = median{g}
- **Midpoint:** f̂ = ½(max + min)

### Color Models
- **RGB → I:** I = (R + G + B) / 3
- **RGB → S:** S = 1 − 3·min(R, G, B) / (R + G + B)
- **RGB → H:** θ = arccos{[½((R-G)+(R-B))] / √((R-G)²+(R-B)(G-B))}
                H = θ if B ≤ G; 360 − θ if B > G

### Compression
- **Compression Ratio:** CR = original_size / compressed_size
- **MSE:** (1/MN) · Σ(f − f̂)²
- **PSNR:** 10 · log₁₀(255² / MSE) dB

### Transforms
- **DFT:** F(u, v) = ΣΣ f(x, y) · exp[−j2π(ux/M + vy/N)]
- **DCT (2D, 8×8):** F(u,v) = (1/4)C(u)C(v)·ΣΣ f(x,y)·cos[(2x+1)uπ/16]·cos[(2y+1)vπ/16]

### Morphology
- **Dilation:** A ⊕ B = { z | (B̂)_z ∩ A ≠ ∅ }
- **Erosion:** A ⊖ B = { z | B_z ⊆ A }
- **Opening:** A ∘ B = (A ⊖ B) ⊕ B
- **Closing:** A • B = (A ⊕ B) ⊖ B
- **Boundary:** β(A) = A − (A ⊖ B)
- **Hole filling:** X_k = (X_{k-1} ⊕ B) ∩ A^c
- **Connected components:** X_k = (X_{k-1} ⊕ B) ∩ A
- **Hit-or-miss:** A ⊛ B = (A ⊖ B₁) ∩ (A^c ⊖ B₂)
- **Thinning:** A ⊗ B = A − (A ⊛ B)
- **Thickening:** A ⊙ B = A ∪ (A ⊛ B)

---

## 📐 2. ALL TRANSFORMS QUICK REFERENCE

| Transform | Formula (forward) | Properties | Application |
|---|---|---|---|
| **DFT** | F(u,v) = ΣΣ f(x,y) · exp[−j2π(ux/M + vy/N)] | Complex output, separable, FFT-able | Filtering, restoration |
| **DCT** | F(u,v) = (1/4)C(u)C(v)·ΣΣ f(x,y)·cos·cos | Real, high energy compaction | JPEG, MPEG |
| **WHT** | Walsh/Hadamard ±1 basis | ±1 valued, no multiplications | Fast compression |
| **Haar** | Rectangular wavelet basis | Multi-resolution, localizes features | JPEG 2000 |
| **KLT** | y = A(x − m_x), A from eigenvectors of C_x | Optimal MSE, data-dependent | PCA, Eigenfaces |

---

## 🧰 3. ALL FILTERS / MASKS REFERENCE

| Filter | Kernel/Mask | Purpose | Domain |
|---|---|---|---|
| **Mean (Box)** | 1/9 · [1 1 1; 1 1 1; 1 1 1] | Gaussian noise removal | Spatial LP |
| **Gaussian** | 1/16 · [1 2 1; 2 4 2; 1 2 1] | Gaussian noise (less blur) | Spatial LP |
| **Median** | sort + middle | Salt-and-pepper noise | Spatial (non-linear) |
| **Max** | max(neighborhood) | Pepper noise removal | Spatial (non-linear) |
| **Min** | min(neighborhood) | Salt noise removal | Spatial (non-linear) |
| **Sobel G_x** | [-1 0 1; -2 0 2; -1 0 1] | Vertical edge detection | Spatial HP |
| **Sobel G_y** | [-1 -2 -1; 0 0 0; 1 2 1] | Horizontal edge detection | Spatial HP |
| **Prewitt G_x** | [-1 0 1; -1 0 1; -1 0 1] | Vertical edges | Spatial HP |
| **Prewitt G_y** | [-1 -1 -1; 0 0 0; 1 1 1] | Horizontal edges | Spatial HP |
| **Roberts** | [0 1; -1 0] | Diagonal edges | Spatial HP |
| **Laplacian (4-conn)** | [0 -1 0; -1 4 -1; 0 -1 0] | Edge enhancement | Spatial HP |
| **Laplacian (8-conn)** | [-1 -1 -1; -1 8 -1; -1 -1 -1] | Edge enhancement | Spatial HP |
| **Ideal LPF** | H(u,v) = 1 if D ≤ D_0 else 0 | Smoothing | Freq LP |
| **Butterworth LPF** | H(u,v) = 1/(1 + (D/D_0)^(2n)) | Smooth smoothing | Freq LP |
| **Gaussian LPF** | H(u,v) = exp(−D²/2D_0²) | Smoothest smoothing | Freq LP |
| **Ideal HPF** | H(u,v) = 0 if D ≤ D_0 else 1 | Edge enhancement | Freq HP |
| **Gaussian HPF** | H(u,v) = 1 − exp(−D²/2D_0²) | Smoothest HPF | Freq HP |

---

## 📚 4. ALL DEFINITIONS (One line each — 40+)

| Term | One-Line Definition |
|---|---|
| **Digital Image Processing** | Algorithmic manipulation of digital image f(x, y) |
| **Pixel** | Smallest addressable unit (position + intensity) |
| **Sampling** | Discretization of spatial coords |
| **Quantization** | Discretization of intensity into L = 2^k levels |
| **Aliasing** | Artifact from undersampling (false patterns) |
| **False contouring** | Visible ridges from insufficient quantization |
| **Histogram** | Pixel count vs gray level plot |
| **CDF** | Cumulative sum of histogram probabilities |
| **Histogram equalization** | Map via (L-1)·CDF for uniform output |
| **Histogram matching** | Map to user-specified histogram |
| **Convolution** | g = w * f over neighborhood |
| **Mask/Kernel** | Small matrix defining filter weights |
| **Smoothing filter** | Low-pass — blurs, denoises |
| **Sharpening filter** | High-pass — enhances edges |
| **Sobel** | First-derivative edge detector |
| **Prewitt** | Like Sobel with equal weights |
| **Roberts** | 2×2 diagonal edge detector |
| **Laplacian** | Second-derivative edge detector |
| **Gradient** | Vector of partial derivatives |
| **Image enhancement** | Subjective visual improvement |
| **Image restoration** | Objective recovery using model |
| **Degradation function H** | Models corruption (PSF) |
| **Motion blur** | Streak in motion direction |
| **Gaussian noise** | Normally-distributed sensor noise |
| **Salt-and-pepper noise** | Impulse noise (0 or 255) |
| **Median filter** | Replace with median; best for impulse |
| **Wiener filter** | Optimal MSE restoration |
| **Inverse filter** | F̂ = G/H; amplifies noise |
| **Color** | Perception of light wavelengths 400-700 nm |
| **Hue** | Dominant wavelength of color |
| **Saturation** | Purity of color |
| **Intensity** | Brightness of color |
| **RGB** | Additive color model |
| **CMY** | Subtractive color model |
| **HSI** | Perceptual color model |
| **YCbCr** | Luminance + chrominance (JPEG) |
| **Pseudocoloring** | Map gray to color for visualization |
| **Color quantization** | Reduce palette size |
| **Color constancy** | Consistent color under different lights |
| **Image compression** | Reduce size via redundancy removal |
| **Lossless** | Exact recovery (PNG, GIF) |
| **Lossy** | Approximate recovery (JPEG) |
| **Compression ratio** | Original / compressed |
| **Huffman coding** | Variable-length prefix code |
| **RLE** | Replace runs with (count, value) |
| **LZW** | Dictionary-based lossless coding |
| **Arithmetic coding** | Encode as single number |
| **DPCM** | Predict + encode error |
| **Vector quantization** | Map blocks to codebook indices |
| **DCT** | Discrete Cosine Transform — JPEG basis |
| **JPEG** | Lossy DCT-based compression |
| **PNG** | Lossless image format |
| **Morphology** | Set-theoretic shape analysis |
| **Structuring element** | Probe mask in morphology |
| **Dilation** | Grow objects (A ⊕ B) |
| **Erosion** | Shrink objects (A ⊖ B) |
| **Opening** | Erode then dilate |
| **Closing** | Dilate then erode |
| **Hit-or-miss** | Detect specific patterns |
| **Thinning** | Reduce to skeleton |
| **Skeleton** | Single-pixel-wide medial axis |
| **Boundary extraction** | A − (A ⊖ B) |
| **Hole filling** | Iterative dilation in complement |

---

## 📚 5. UNIT-WISE TOP 5 MUST-KNOW POINTS

### 🟦 UNIT 1: Digital Image Fundamentals
1. **f(x, y) = i(x, y) · r(x, y)** — image formation model
2. **Sampling** = spatial; **Quantization** = amplitude (L = 2^k)
3. **Neighborhoods:** N₄, N_D, N₈; **Adjacency:** 4, 8, m
4. **Distances:** Euclidean (D_e), City-block (D₄), Chessboard (D₈)
5. **Low sampling** → aliasing; **Low quantization** → false contouring

### 🟩 UNIT 2: Spatial Domain Enhancement
1. **General form:** g(x, y) = T[f(x, y)]
2. **Transformations:** Negative (s=L-1-r), Log (s=c·log(1+r)), Gamma (s=c·r^γ)
3. **Histogram equalization:** s_k = (L-1)·cdf(r_k)
4. **Smoothing filters:** Mean, Gaussian (linear); Median (non-linear)
5. **Sharpening filters:** Sobel/Prewitt (1st deriv), Laplacian (2nd deriv)

### 🟨 UNIT 3: Image Restoration
1. **Degradation model:** g = h * f + η
2. **Noise PDFs:** Gaussian, Rayleigh, Erlang, Exponential, Uniform, Salt-and-Pepper
3. **Filter selection:** Median↔S&P, Max↔pepper, Min↔salt
4. **Inverse filter:** F̂ = G/H (amplifies noise)
5. **Wiener filter:** F̂ = [H*/(|H|² + S_η/S_f)]·G — optimal MSE

### 🟧 UNIT 4: Color & Compression
1. **Color models:** RGB (additive), CMY (subtractive), HSI (perceptual)
2. **RGB→HSI:** I=(R+G+B)/3, S=1−3·min/(R+G+B), H via arccos
3. **Lossless** (PNG, GIF) vs **Lossy** (JPEG, MPEG)
4. **JPEG steps:** RGB→YCbCr→Subsample→8×8 DCT→Quantize→Zigzag→RLE→Huffman
5. **VQ codebook:** Built via LBG/K-means

### 🟪 UNIT 5: Morphological Processing
1. **Dilation (⊕):** grows objects; **Erosion (⊖):** shrinks objects
2. **Opening:** A ∘ B = (A ⊖ B) ⊕ B — removes salt noise
3. **Closing:** A • B = (A ⊕ B) ⊖ B — removes pepper noise
4. **Hit-or-miss:** A ⊛ B = (A ⊖ B₁) ∩ (A^c ⊖ B₂) — pattern detection
5. **Algorithms:** Boundary (A − A⊖B), hole filling, connected components

---

## 🔁 6. ALL DIFFERENCE / COMPARISON TABLES

### 6.1 Spatial Domain vs Frequency Domain

| Feature | Spatial | Frequency |
|---|---|---|
| Operates on | Pixels | DFT/DCT coefficients |
| Transform needed | No | Yes |
| Examples | Mean filter, Sobel | Ideal LPF, Butterworth |
| Speed | Fast (small kernels) | Fast (FFT) |

### 6.2 Lowpass vs Highpass vs Bandpass

| Filter | Passes | Blocks | Effect |
|---|---|---|---|
| LPF | Low freq | High freq | Smoothing |
| HPF | High freq | Low freq | Edge enhance |
| BPF | Mid freq | Both extremes | Edge with thickness |

### 6.3 Lossless vs Lossy Compression

| Feature | Lossless | Lossy |
|---|---|---|
| Recovery | Exact | Approximate |
| CR | 2-5× | 10-100× |
| Examples | PNG, GIF | JPEG, MPEG |
| Use | Medical, legal | Web, video |

### 6.4 Smoothing vs Sharpening

| Feature | Smoothing | Sharpening |
|---|---|---|
| Type | Low-pass | High-pass |
| Effect | Blur, denoise | Edge enhance |
| Math | Average | Derivatives |
| Kernels | Mean, Gaussian, Median | Sobel, Laplacian |

### 6.5 DFT vs DCT vs WHT

| Feature | DFT | DCT | WHT |
|---|---|---|---|
| Basis | Sinusoid | Cosine | ±1 |
| Output | Complex | Real | Real |
| Energy compaction | Moderate | High | Low |
| Use | Filtering | JPEG | Fast |

### 6.6 Erosion vs Dilation

| Feature | Erosion | Dilation |
|---|---|---|
| Effect | Shrink | Grow |
| Boundary | Inward | Outward |
| Holes | Enlarge | Fill / shrink |
| Use | Remove noise | Fill gaps |

### 6.7 Global vs Local Thresholding

| Feature | Global | Local |
|---|---|---|
| Threshold | Single T | Varies spatially |
| Speed | Faster | Slower |
| Use | Uniform lighting | Variable lighting |
| Example | Otsu | Niblack |

### 6.8 Image Enhancement vs Image Restoration

| Feature | Enhancement | Restoration |
|---|---|---|
| Goal | Subjective | Objective |
| Approach | Heuristic | Mathematical |
| Knowledge | Visual | Model (H, η) |

### 6.9 Histogram Equalization vs Specification

| Feature | Equalization | Specification |
|---|---|---|
| Output | Uniform | User-defined |
| Function | T = (L−1)·cdf | G⁻¹(T) |
| Flexibility | Low | High |

### 6.10 Opening vs Closing

| Feature | Opening | Closing |
|---|---|---|
| Sequence | Erode → Dilate | Dilate → Erode |
| Removes | Salt | Pepper |
| Smooths | Outside | Inside |

### 6.11 4-conn vs 8-conn vs m-conn

| Type | Diagonal? | Path Ambiguity? |
|---|---|---|
| 4-conn | No | None |
| 8-conn | Yes | Yes |
| m-conn | Conditional | Resolved |

### 6.12 Mean vs Median Filter

| Feature | Mean | Median |
|---|---|---|
| Type | Linear | Non-linear |
| Best noise | Gaussian | Salt-and-pepper |
| Edges | Poor | Excellent |

### 6.13 Sampling vs Quantization

| Feature | Sampling | Quantization |
|---|---|---|
| Acts on | Coords (x, y) | Amplitude f |
| Affects | Spatial resolution | Intensity resolution |
| Problem | Aliasing | False contouring |

### 6.14 RGB vs HSI

| Feature | RGB | HSI |
|---|---|---|
| Basis | Light primaries | Perception |
| Decoupled I | No | Yes |
| Use | Display | Processing |

---

## ⚙️ 7. ALGORITHMS — QUICK STEPS FORMAT

### 7.1 Histogram Equalization (5 steps)
1. Compute h(r_k) = n_k
2. Normalize: p(r_k) = n_k / MN
3. Compute cdf(r_k) = Σ p(r_j)
4. s_k = round((L−1) · cdf(r_k))
5. Replace r with s

### 7.2 Sobel Edge Detection (5 steps)
1. Apply G_x mask
2. Apply G_y mask
3. Compute magnitude |∇f|
4. Compute direction θ
5. Threshold to get edges

### 7.3 Canny Edge Detection (5 steps)
1. Gaussian smoothing
2. Compute gradient (Sobel)
3. Non-maximum suppression
4. Double thresholding (high & low)
5. Edge tracking by hysteresis

### 7.4 JPEG Compression (8 steps)
1. RGB → YCbCr
2. Chrominance subsample 4:2:0
3. Split into 8×8 blocks
4. Apply 2D-DCT
5. Quantize
6. Zigzag scan
7. RLE
8. Huffman code

### 7.5 Hole Filling (4 steps)
1. Find seed inside hole (X_0 = {p})
2. X_k = (X_{k-1} ⊕ B) ∩ A^c
3. Repeat until X_k = X_{k-1}
4. Output: A ∪ X_k

### 7.6 Connected Component Extraction (4 steps)
1. Pick seed in component
2. X_k = (X_{k-1} ⊕ B) ∩ A
3. Repeat until X_k = X_{k-1}
4. Output: X_k

### 7.7 Boundary Extraction (3 steps)
1. Erode A by B
2. β(A) = A − (A ⊖ B)
3. Output boundary

### 7.8 LBG Codebook (5 steps)
1. Initialize K codewords
2. Assign each training vector to nearest codeword
3. Recompute centroids
4. Compute distortion change
5. If converged, stop; else go to 2

### 7.9 Huffman Coding (6 steps)
1. List symbols with frequencies
2. Sort by frequency
3. Combine two smallest
4. Repeat until single tree
5. Assign 0/1 to branches
6. Read code root → leaf

### 7.10 Histogram Matching (5 steps)
1. Compute CDF_input
2. Compute CDF_desired
3. For each input r, compute s = CDF_input(r)
4. Find z such that CDF_desired(z) = s
5. Replace input r with z

---

## 📊 8. STANDARD VALUES TO REMEMBER

| Parameter | Typical Value |
|---|---|
| **Standard image sizes** | 256×256, 512×512, 1024×768, 1920×1080 (Full HD), 3840×2160 (4K) |
| **Standard kernel sizes** | 3×3, 5×5, 7×7 (odd, square) |
| **Bit depths** | 1 (binary), 4, 8 (standard gray), 16, 24 (true color), 32 |
| **Gray levels (L)** | 2, 16, 256, 65536 |
| **JPEG block size** | 8×8 |
| **JPEG CR** | 10:1 to 50:1 (typical) |
| **PNG CR** | 2:1 to 5:1 (lossless) |
| **Standard subsampling** | 4:2:0, 4:2:2, 4:4:4 |
| **Gray scale range (8-bit)** | 0 (black) to 255 (white) |
| **CRT Gamma** | ≈ 2.2 |
| **Pre-correction Gamma** | 1/2.2 ≈ 0.45 |
| **Common threshold** | 128 (middle), Otsu (computed) |
| **DPI for print** | 300 |
| **DPI for screen** | 72-96 |
| **Visible wavelength** | 400-700 nm |
| **Reflectance range** | 0 to 1 |
| **Common SE** | 3×3 square, 3×3 cross |
| **NSR (Wiener)** | S_η / S_f |

---

## 🧠 9. MNEMONICS & MEMORY TRICKS

- **"f = i × r"** — Image formation: brightness = light × surface
- **"MR. FAB SIR"** — DIP fields: Medical, Remote sensing, Forensics, Astronomy, Biometrics, Security, Industrial, Robotics
- **"AERCWCMSRR"** — 10 fundamental steps: Acquisition, Enhancement, Restoration, Color, Wavelets, Compression, Morphology, Segmentation, Representation, Recognition
- **"Sample where, Quantize how-much"** — Sampling = location, Quantization = value
- **"L = 2^k"** — Number of gray levels
- **"MAX kills pepper, MIN kills salt"** — Order-statistic filter rules
- **"DILATE = grow, ERODE = eat"** — Morphology basic
- **"Open = Erode then Dilate (smooth out specks)"** — Opening order
- **"Close = Dilate then Erode (close gaps)"** — Closing order
- **"YCbCr → Subsample → DCT → Quantize → Zigzag → RLE → Huffman"** — JPEG pipeline (8 steps)
- **"G_x detects vertical, G_y detects horizontal"** — Sobel directions
- **"Wiener = inverse + noise-aware"** — Wiener filter intuition
- **"Hue = which color, Saturation = how pure, Intensity = how bright"** — HSI components
- **"Salt = bright = 255, Pepper = dark = 0"** — Salt-and-pepper noise
- **"DCT loves 8×8"** — JPEG uses 8×8 blocks
- **"Histogram Equalization = scale by CDF"** — HE rule
- **"Gamma < 1 brightens, Gamma > 1 darkens"** — Power-law rule

---

## ✅ 10. LAST 30 MINUTES CHECKLIST

### Absolute MUST-revise:

1. **Image Formation:** f(x, y) = i(x, y) · r(x, y)
2. **Sampling vs Quantization:** spatial vs amplitude; aliasing vs false contouring
3. **Histogram Equalization:** s_k = (L−1) · cdf(r_k)
4. **Sobel Masks:** G_x = [-1 0 1; -2 0 2; -1 0 1]; G_y = [-1 -2 -1; 0 0 0; 1 2 1]
5. **Laplacian Mask:** [0 -1 0; -1 4 -1; 0 -1 0]
6. **Median Filter** for salt-and-pepper noise
7. **Degradation Model:** g(x, y) = h(x, y) * f(x, y) + η(x, y)
8. **Wiener Filter:** F̂ = [H*/(|H|² + S_η/S_f)] · G
9. **JPEG Pipeline (8 steps):** RGB→YCbCr→Subsample→8×8→DCT→Quantize→Zigzag→RLE→Huffman
10. **RGB → HSI:** I=(R+G+B)/3, S=1−3·min/(R+G+B), H via arccos formula
11. **Morphology Big Four:** Dilation (⊕), Erosion (⊖), Opening (∘), Closing (•)
12. **Boundary Extraction:** β(A) = A − (A ⊖ B)
13. **DCT** = real-valued, energy-compaction, basis of JPEG
14. **L = 2^k** gray levels
15. **Distance measures:** D_e = √(Δx² + Δy²); D_4 = |Δx| + |Δy|; D_8 = max(|Δx|, |Δy|)

---

## 🎯 EXAM-DAY STRATEGY

1. **Read paper carefully** — 5 min
2. **Mark questions:** Easy = ✓, Medium = ?, Skip = ✗
3. **Start with easy 2-mark questions** (build confidence)
4. **Then 5-mark questions** (~10 min each)
5. **Last: 10-mark essays** (15-20 min each)
6. **Reserve 10 min** for revision at end
7. **Draw diagrams** wherever possible
8. **Use tables for comparisons** (clean, fast)
9. **Always state formulas** before applying
10. **Box final answers** in numerical problems
11. **Don't leave any question blank** — partial credit always helps

---

# 🏆 GOOD LUCK!

**Remember:** Image Processing = **mathematical + visual**. Every formula has a geometric interpretation. Every algorithm follows a clear pipeline. Master 10 key formulas and the rest follows.
