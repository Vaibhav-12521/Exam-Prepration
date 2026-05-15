# IMAGE PROCESSING — IMPORTANT QUESTIONS (MODEL EXAM ANSWERS)
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6105 | **Sem VI**

> 📝 Answers below are written as if a student is writing them in the exam answer sheet — with full introduction, diagrams, working, tables, and conclusion. Read once, replicate the structure in your exam.

---

# 🔴 TOP 10 MOST LIKELY 5-MARK QUESTIONS

## Q1. Differentiate between Image Enhancement and Image Restoration.

**Answer:**

**Image Enhancement** improves the **subjective appearance** of an image so that it looks better to a human observer. It is a **heuristic** process based on visual perception.

**Image Restoration** is the **objective recovery** of an image from a degraded version using a **mathematical model** of the degradation process.

**Comparison Table:**

| Feature | Image Enhancement | Image Restoration |
|---|---|---|
| **Goal** | Improve subjective appearance | Recover original from degradation |
| **Approach** | Heuristic / visual | Mathematical / model-based |
| **Knowledge needed** | Visual preference | Degradation function H, noise η |
| **Techniques** | Histogram, sharpen, gamma | Inverse filter, Wiener, CLS |
| **Output** | "Looks better" image | "Closer to original" image |

**Examples:**
- Enhancement: Brightening a dark night photo with γ = 0.5
- Restoration: Deblurring a motion-blurred satellite image with Wiener filter

**Mathematical contrast:**
- Enhancement: g = T[f]
- Restoration: g = h * f + η; estimate f̂ ≈ f

**Conclusion:** Enhancement is subjective; restoration is objective and model-based.

---

## Q2. Explain Sobel Operator with mathematical formulas.

**Answer:**

The **Sobel operator** detects edges using **first-derivative approximations** of the image gradient.

**Masks:**
```
G_x = [-1  0  1]      G_y = [-1 -2 -1]
      [-2  0  2]            [ 0  0  0]
      [-1  0  1]            [ 1  2  1]
```

- G_x detects vertical edges
- G_y detects horizontal edges

**Edge Magnitude:** |∇f| = √(G_x² + G_y²) ≈ |G_x| + |G_y|

**Edge Direction:** θ = arctan(G_y / G_x)

**Procedure:**
1. Apply G_x mask → response at each pixel
2. Apply G_y mask → response at each pixel
3. Compute magnitude using formula
4. Compute direction using arctan
5. Threshold magnitude to obtain edge map

**Worked Example (3×3 patch):**
```
f = 50  60  70
    55  65  75
    60  70  80

G_x = 80, G_y = 40
|∇f| = √(80² + 40²) = √8000 ≈ 89.4
θ = arctan(0.5) ≈ 26.6°
```

**Conclusion:** Sobel computes gradient magnitude and direction using two 3×3 masks; widely used in edge detection pipelines.

---

## Q3. Explain Histogram Equalization step-by-step.

**Answer:**

**Histogram Equalization (HE)** is an automatic contrast-enhancement method that maps pixel intensities through their CDF to produce an approximately uniform output histogram.

**Algorithm:**
1. Compute histogram: h(r_k) = n_k for k = 0..L−1
2. Normalize: p_r(r_k) = n_k / MN
3. Compute CDF: cdf(r_k) = Σ_{j=0..k} p_r(r_j)
4. Map pixels: s_k = round((L − 1) · cdf(r_k))
5. Replace each pixel r with s.

**Formula:** s_k = T(r_k) = (L − 1) · Σ p_r(r_j)

**Numerical Example (3-bit, 64 pixels):**

| r_k | n_k | p_r | cdf | (L-1)·cdf | s_k |
|---|---|---|---|---|---|
| 0 | 8 | 0.125 | 0.125 | 0.875 | 1 |
| 1 | 10 | 0.156 | 0.281 | 1.97 | 2 |
| 2 | 10 | 0.156 | 0.437 | 3.06 | 3 |
| 3 | 2 | 0.031 | 0.469 | 3.28 | 3 |
| 4 | 12 | 0.187 | 0.656 | 4.59 | 5 |
| 5 | 16 | 0.250 | 0.906 | 6.34 | 6 |
| 6 | 4 | 0.063 | 0.969 | 6.78 | 7 |
| 7 | 2 | 0.031 | 1.000 | 7.00 | 7 |

**Why HE enhances contrast:**
- Stretches narrow histograms across full range
- Maps frequent gray levels to wider output ranges
- Approximately uniform output → max global contrast

**Conclusion:** HE applies s_k = (L − 1) · cdf(r_k) to maximize global contrast automatically.

---

## Q4. Explain Median Filter and its advantage for Salt-and-Pepper noise.

**Answer:**

The **Median Filter** is a non-linear order-statistic filter that replaces each pixel with the median value of its neighborhood.

**Formula:** f̂(x, y) = median { g(s, t) : (s, t) ∈ S_xy }

**Algorithm:**
1. Place mask (e.g., 3×3) over each pixel
2. Sort the m × n neighborhood values
3. Replace center pixel with the middle (median) value
4. Move to next pixel and repeat

**Advantage for Salt-and-Pepper:**
- Salt (255) and pepper (0) are outliers at extreme ends
- After sorting, they appear at the ends of the list
- Median = middle value → outliers discarded
- Edges preserved much better than mean filter

**3×3 Example with pepper:**
```
Neighborhood:  50, 60, 70, 55, 0, 75, 60, 70, 80
Sorted:        0, 50, 55, 60, 60, 70, 70, 75, 80
Median (5th):  60 ← replaces center
```

**Mean vs Median:**

| Property | Mean | Median |
|---|---|---|
| Type | Linear | Non-linear |
| Best for | Gaussian | Salt-and-pepper |
| Edge preservation | Poor | Excellent |
| Outliers | Affect average | Discarded |

**Conclusion:** Median filter optimally removes salt-and-pepper noise by discarding outliers while preserving edges.

---

## Q5. Explain JPEG Compression Algorithm step-by-step.

**Answer:**

**JPEG** is the most widely used lossy compression standard for photographic images, based on the **8×8 DCT**.

**8-Step Algorithm:**
1. **Color Conversion** — RGB → YCbCr
2. **Chrominance Subsampling** — 4:2:0
3. **Block Splitting** — divide image into 8×8 blocks
4. **DCT** — apply 2D-DCT to each block
5. **Quantization** — divide by Q-table (LOSSY STEP)
6. **Zigzag Scan** — reorder coefficients (DC → high freq)
7. **Run-Length Encoding (RLE)** — encode runs of zeros
8. **Huffman Coding** — entropy-code remaining values

**Pipeline:**
```
RGB → YCbCr → Subsample(4:2:0) → 8×8 Blocks → DCT →
Quantize → Zigzag → RLE → Huffman → JPEG file
```

**DCT Formula:**
F(u, v) = (1/4) · C(u) · C(v) · ΣΣ f(x, y) · cos[(2x+1)uπ/16] · cos[(2y+1)vπ/16]
where C(u) = 1/√2 for u=0; 1 otherwise

**Compression Ratio:** 10:1 to 50:1 with little visible loss.

**Conclusion:** JPEG pipeline: RGB → YCbCr → Subsample → 8×8 DCT → Quantize → Zigzag → RLE → Huffman.

---

## Q6. Explain RGB to HSI conversion with formulas.

**Answer:**

**RGB** is an additive color model; **HSI** is a perceptual model decoupling color from brightness.

**Conversion Formulas (RGB → HSI):**

```
I = (R + G + B) / 3

S = 1 − [ 3 · min(R, G, B) / (R + G + B) ]

θ = arccos { [½((R−G) + (R−B))] / √((R−G)² + (R−B)(G−B)) }

H = θ        if B ≤ G
H = 360 − θ  if B > G
```

**Components:**
- H (Hue) — angle 0°–360° (dominant color)
- S (Saturation) — 0 (gray) to 1 (pure)
- I (Intensity) — 0 (black) to 1 (white)

**Challenges in HSI → RGB:**
- Hue undefined when S = 0 (pure gray)
- Numerical instability near S = 0
- Out-of-gamut requires clipping
- Sector boundary errors at H = 0°, 120°, 240°

**Worked Example:** R=0.6, G=0.2, B=0.4
- I = 0.4
- S = 0.5
- θ ≈ 30°; B > G → H = 360 − 30 = 330°

**Conclusion:** RGB → HSI gives I = (R+G+B)/3, S = 1 − 3·min/(R+G+B), H via arccos.

---

## Q7. Explain Dilation and Erosion with examples.

**Answer:**

**Dilation (A ⊕ B):** A ⊕ B = { z | (B̂)_z ∩ A ≠ ∅ } — expands binary objects.

**Erosion (A ⊖ B):** A ⊖ B = { z | B_z ⊆ A } — shrinks binary objects.

**Dilation Example:**
```
A:                  A ⊕ B:
0 0 0 0 0           0 0 0 0 0
0 0 0 0 0           0 1 1 1 0
0 0 1 0 0    →      0 1 1 1 0
0 0 0 0 0           0 1 1 1 0
0 0 0 0 0           0 0 0 0 0
```

**Erosion Example:**
```
A:                  A ⊖ B:
0 0 0 0 0           0 0 0 0 0
0 1 1 1 0           0 0 0 0 0
0 1 1 1 0    →      0 0 1 0 0
0 1 1 1 0           0 0 0 0 0
0 0 0 0 0           0 0 0 0 0
```

| Op | Effect | Boundary | Use |
|---|---|---|---|
| Dilation | Grow | Outward | Fill gaps |
| Erosion | Shrink | Inward | Remove noise |

**Properties:**
- Dilation is commutative; erosion is NOT
- Duality: (A ⊖ B)^c = A^c ⊕ B̂

**Conclusion:** Dilation expands objects; erosion shrinks objects — foundation of all morphology.

---

## Q8. Compare Smoothing and Sharpening Filters.

**Answer:**

| Feature | Smoothing | Sharpening |
|---|---|---|
| **Frequency response** | Low-pass | High-pass |
| **Effect** | Blurs, reduces noise | Enhances edges |
| **Math basis** | Average | Derivatives |
| **Kernels** | Mean, Gaussian, Median | Sobel, Prewitt, Laplacian |
| **Edge effect** | Blurred | Enhanced |
| **Noise effect** | Reduces | Amplifies |
| **Use** | Pre-processing, denoise | Edge detection |

**Smoothing Mask Example (3×3 Mean):**
```
       1 1 1
1/9 × [1 1 1]
       1 1 1
```

**Sharpening Mask Example (Laplacian):**
```
 0 -1  0
-1  4 -1
 0 -1  0
```

**Conclusion:** Smoothing averages pixels (LP, blurs noise); sharpening uses derivatives (HP, enhances edges).

---

## Q9. Explain Image Degradation/Restoration model with block diagram.

**Answer:**

**Spatial Domain:** g(x, y) = h(x, y) * f(x, y) + η(x, y)
**Frequency Domain:** G(u, v) = H(u, v) · F(u, v) + N(u, v)

**Block Diagram:**
```
                      η(x, y) noise
                          ↓
   f(x, y) → [ H ] → ⊕ → g(x, y) → [Restoration Filter] → f̂(x, y)
```

**Components:**
- f(x, y) — original (unknown)
- H — degradation function (PSF)
- η — additive noise
- g — observed degraded image
- f̂ — estimate of original

**Restoration Approaches:**

| Filter | Knowledge Needed | Behavior |
|---|---|---|
| Inverse | H | Simple division; amplifies noise |
| Pseudo-inverse | H | Threshold limit |
| Wiener | H + S_η + S_f | Optimal MSE |
| Constrained LS | H + smoothness | Robust |

**Conclusion:** Model g = h * f + η underlies all restoration filters.

---

## Q10. Explain Image Formation Model (illumination × reflectance).

**Answer:**

**Formula:** f(x, y) = i(x, y) × r(x, y)

**Components:**
- i(x, y) — illumination from source (0 < i < ∞)
- r(x, y) — reflectance of surface (0 ≤ r ≤ 1)

**Sample Values:**

| Surface | r |
|---|---|
| Black velvet | 0.01 |
| White wall | 0.80 |
| Snow | 0.93 |

| Source | i (lm/m²) |
|---|---|
| Sunlight | 90,000 |
| Office | 1,000 |
| Moonlight | 0.1 |

**Examples:**
- Snow in sunlight: f = 90,000 × 0.93 = 83,700
- Black coal in sunlight: f = 90,000 × 0.01 = 900

**Range:** L_min ≤ f(x, y) ≤ L_max

**Conclusion:** Image formation model f = i × r separates physics of light (illumination) from surface properties (reflectance).

---

# 🟠 TOP 10-MARK QUESTIONS

## Q11. Discuss components of a digital image processing system.

**Answer:**

A DIP system has 8 interlinked components:

1. **Image Sensors** — CCD/CMOS, convert light to electrical signal
2. **Specialized Hardware** — frame grabber, ALU, GPU
3. **Computer (Host)** — general-purpose PC
4. **Image Processing Software** — MATLAB, OpenCV, ImageJ
5. **Mass Storage** — RAM, HDD/SSD, tape/cloud
6. **Image Display** — Monitor, LCD/LED, projector
7. **Hardcopy Device** — printer, plotter
8. **Network** — transmit images remotely

**Block Diagram:**
```
[Image Sensor]→[Specialized HW]→[Computer]→[DIP Software]
                                          ↓
[Mass Storage]↔[Display]↔[Hardcopy]↔[Network]
                          ↑
                  [Knowledge Base]
```

**Knowledge base** spans all components.

**Conclusion:** DIP integrates sensors, specialized hardware, computer with software, mass storage, display, hardcopy, and network.

---

## Q12. Compare four noise removal filters (Arithmetic, Geometric, Median, Contra-harmonic).

**Answer:**

| Feature | Arithmetic Mean | Geometric Mean | Median | Contra-Harmonic |
|---|---|---|---|---|
| **Formula** | (1/mn)·Σg | (Πg)^(1/mn) | sort & take middle | Σg^(Q+1)/Σg^Q |
| **Type** | Linear | Non-linear | Non-linear | Non-linear |
| **Best for** | Gaussian | Gaussian (less blur) | Salt-and-pepper | Q>0 pepper, Q<0 salt |
| **Edge preservation** | Poor | Better | Excellent | Moderate |
| **Failure mode** | Blurs edges | Zero pixel kills product | Slower | Wrong Q amplifies wrong noise |

**Best for Salt-and-Pepper:** Median (outliers discarded).

**Why others fail:**
- Mean → blurs noise
- Geometric → zero pepper kills product
- Contra-harmonic → only one type per Q

**Conclusion:** For salt-and-pepper noise, median filter is optimal.

---

## Q13. Explain Wiener filter in detail with comparison.

**Answer:**

**Wiener Filter Formula:**
F̂(u, v) = [ H*(u, v) / (|H(u, v)|² + S_η/S_f) ] · G(u, v)

**Behavior:**
- NSR → 0 (no noise): Wiener → inverse filter
- NSR large: suppresses frequency

**Comparison with Inverse:**

| Feature | Inverse | Wiener |
|---|---|---|
| Knowledge | H | H + S_η + S_f |
| Noise | Amplifies | Suppresses optimally |
| Best when | No noise | Noise present |
| Failure | Blows up at H ≈ 0 | Smooth handling |

**Conclusion:** Wiener filter is optimal MSE restoration; reduces to inverse filter when noise = 0.

---

## Q14. Explain DCT — formula, properties, JPEG.

**Answer:**

**Discrete Cosine Transform (DCT)** is a real-valued frequency transform — foundation of JPEG, MPEG.

**2D DCT Formula:**
F(u, v) = (1/4)·C(u)·C(v) · ΣΣ f(x, y) · cos[(2x+1)uπ/16] · cos[(2y+1)vπ/16]

**Properties:**
- Real output
- Energy compaction
- Separable
- Orthogonal
- Near-KLT in energy

**Use in JPEG:**
- Applied to 8×8 blocks
- Concentrates energy in DC + low frequencies
- High frequencies become zero after quantization

| Feature | DFT | DCT |
|---|---|---|
| Output | Complex | Real |
| Basis | Sinusoids | Cosines |
| Energy compaction | Moderate | High |

**Conclusion:** DCT decomposes images into cosine basis; foundation of JPEG/MPEG.

---

## Q15. Explain morphological algorithms — boundary, hole filling, connected components.

**Answer:**

**(1) Boundary Extraction:** β(A) = A − (A ⊖ B)

Algorithm:
1. Erode A by B
2. Subtract eroded from original
3. Output = boundary pixels

**(2) Hole Filling:** X_k = (X_{k-1} ⊕ B) ∩ A^c

Algorithm:
1. Pick seed inside hole; X_0 = {p}
2. Dilate X by B
3. Intersect with complement of A
4. Repeat until convergence
5. Final = A ∪ X_k

**(3) Connected Components:** X_k = (X_{k-1} ⊕ B) ∩ A

Algorithm:
1. Pick seed pixel inside component
2. Dilate X by B
3. Intersect with A (not A^c)
4. Repeat until convergence
5. X_k = one component

**Applications:**

| Algorithm | Application |
|---|---|
| Boundary | Object outlines |
| Hole filling | OCR, shape analysis |
| Connected components | Region labeling, blob detection |

**Conclusion:** All three are iterative dilation/erosion with set ops.

---

# 🟡 TOP 2-MARK QUESTIONS (One-line answers)

**Q16.** What is image processing? — Algorithmic manipulation of digital image f(x, y).

**Q17.** Define pixel. — Smallest addressable unit (position + intensity).

**Q18.** Define sampling. — Discretization of spatial coordinates.

**Q19.** Define quantization. — Discretization of intensity into L = 2^k levels.

**Q20.** What is image resolution? — Spatial (sampling) and intensity (quantization).

**Q21.** What is histogram? — Pixel count vs gray level: h(r_k) = n_k.

**Q22.** What is convolution? — g = w * f over neighborhood.

**Q23.** What is Laplacian? — Second-derivative operator for sharpening.

**Q24.** What is RGB? — Additive color model with Red, Green, Blue.

**Q25.** What is HSI? — Perceptual model with Hue, Saturation, Intensity.

**Q26.** What is image compression? — Reduces data size via redundancy removal.

**Q27.** What is structuring element (SE)? — Small mask used as probe in morphology.

**Q28.** What is dilation? — A ⊕ B grows binary objects.

**Q29.** What is erosion? — A ⊖ B shrinks binary objects.

**Q30.** What is opening? — A ∘ B = (A ⊖ B) ⊕ B; removes salt noise.

**Q31.** What is closing? — A • B = (A ⊕ B) ⊖ B; removes pepper noise.

**Q32.** Define DCT. — Real cosine transform with energy compaction; basis of JPEG.

**Q33.** Define hue. — Dominant wavelength of color (0°–360°).

**Q34.** Define saturation. — Purity of color (0 gray, 1 pure).

**Q35.** Define median filter. — Replace pixel with median; best for salt-and-pepper.

**Q36.** What is false contouring? — Visible ridges from insufficient quantization levels.

**Q37.** What is aliasing? — Artifact from undersampling — high freq folds to low.

---

# 🟢 TOP NUMERICAL PROBLEMS

## N1. Apply Sobel operator to 3×3 patch.

**Given:** f = | 50 60 70 |
              | 55 65 75 |
              | 60 70 80 |

**G_x = 80, G_y = 40**

|∇f| = √(80² + 40²) = √8000 ≈ **89.4**

θ = arctan(40/80) ≈ **26.6°**

---

## N2. Histogram equalization for 3-bit image.

n_k = [8, 10, 10, 2, 12, 16, 4, 2]

| r_k | cdf | s_k |
|---|---|---|
| 0 | 0.125 | 1 |
| 1 | 0.281 | 2 |
| 2 | 0.437 | 3 |
| 3 | 0.469 | 3 |
| 4 | 0.656 | 5 |
| 5 | 0.906 | 6 |
| 6 | 0.969 | 7 |
| 7 | 1.000 | 7 |

---

## N3. Negative of pixel.

f = 100, L = 256 → **s = 255 − 100 = 155**

---

## N4. Distance measures between p(2, 3), q(5, 7).

D_e = √((2-5)² + (3-7)²) = √25 = **5**
D_4 = |2-5| + |3-7| = 3 + 4 = **7**
D_8 = max(3, 4) = **4**

---

## N5. RGB to HSI conversion (R=0.6, G=0.2, B=0.4).

I = 0.4
S = 1 − 3·0.2/1.2 = 0.5
θ ≈ 30°; B > G → **H = 330°**

---

## N6. 3×3 mean filter.

patch = | 100 110 120 |
        |  90 100 130 |
        |  80  90 100 |

f̂(2,2) = 920/9 ≈ **102**

---

## N7. 3×3 median filter with pepper noise.

patch = | 50 60 70 |
        | 55  0 75 |
        | 60 70 80 |

Sorted: 0, 50, 55, 60, 60, 70, 70, 75, 80
Median: **60** (pepper removed)

---

## N8. Laplacian.

patch = | 100 100 100 |
        | 100 150 100 |
        | 100 100 100 |

∇²f = 100·4 − 4·150 = −200 (bright peak detected)

---

## N9. Dilation of binary image.

A (single pixel) → A ⊕ B (3×3 SE) → 3×3 block.

---

## N10. Erosion of 3×3 block.

A (3×3 block) → A ⊖ B (3×3 SE) → only center pixel survives.

---

# 🔵 TOP ALGORITHM-WRITE QUESTIONS

## A1. Histogram Equalization
1. Compute h(r_k) = n_k
2. Normalize p_r(r_k) = n_k / MN
3. Compute cdf(r_k)
4. s_k = round((L−1) · cdf(r_k))
5. Replace each pixel.

## A2. JPEG Encoding
1. RGB → YCbCr
2. Chrominance subsampling
3. 8×8 block split
4. 2D-DCT
5. Quantize
6. Zigzag scan
7. RLE
8. Huffman encode

## A3. LBG Codebook Generation
1. Initialize K codewords
2. Assign each training vector to nearest codeword
3. Recompute centroids
4. Compute distortion
5. Iterate until convergence

## A4. Hole Filling
1. Pick seed inside hole; X_0 = {p}
2. X_k = (X_{k-1} ⊕ B) ∩ A^c
3. Repeat until convergence
4. A ∪ X_k = filled image

## A5. Connected Components
1. Pick seed inside component
2. X_k = (X_{k-1} ⊕ B) ∩ A
3. Repeat until convergence
4. X_k = one component

## A6. Sobel Edge Detection
1. Apply G_x mask
2. Apply G_y mask
3. Compute magnitude
4. Compute direction
5. Threshold to obtain edges

## A7. Huffman Coding
1. List symbols + frequencies
2. Sort by frequency
3. Combine two smallest
4. Repeat until single tree
5. Assign 0/1 to branches
6. Read code root → leaf

## A8. Boundary Extraction
1. Take binary image A
2. Choose 3×3 SE B
3. Erode A by B
4. β(A) = A − (A ⊖ B)
5. Output boundary

---

# 🟣 TOP DIAGRAM QUESTIONS

## D1. Image Processing Pipeline
```
Acquisition → Enhancement → Restoration → Color → Wavelets →
Compression → Morphology → Segmentation → Representation → Recognition
                          ↑ Knowledge Base ↑
```

## D2. Image Degradation/Restoration
```
                      η(x, y) noise
                          ↓
   f(x, y) → [ H ] → ⊕ → g(x, y) → [Restoration Filter] → f̂(x, y)
```

## D3. RGB Color Cube
```
        White (1, 1, 1)
        /|
   Yellow ── Cyan
    /|     /|
 Red ── Magenta ── Blue
   \  |   /
   Black (0, 0, 0)
```

## D4. JPEG Compression Pipeline
```
RGB → YCbCr → Subsample(4:2:0) → 8×8 Blocks → DCT →
Quantize → Zigzag → RLE → Huffman → JPEG file
```

## D5. Pixel Neighborhoods
```
N4 (+ shape):       N8 (full):
    [N]            [NW] [N] [NE]
[W] [p] [E]        [W]  [p] [E]
    [S]            [SW] [S] [SE]
```

---

# 🎯 TOP 10 MUST-PREPARE QUESTIONS

1. Image enhancement vs restoration
2. Histogram equalization step-by-step
3. Sobel operator with formulas
4. Median filter for salt-and-pepper
5. JPEG compression algorithm
6. RGB to HSI conversion formulas
7. Dilation and erosion with examples
8. Image degradation model (g = h*f + η)
9. Image formation model (f = i × r)
10. Opening and closing operations

---

# END OF IMPORTANT QUESTIONS
