# IMAGE PROCESSING — COMPLETE SYLLABUS NOTES — UNITS 1 TO 5
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6105 | **Sem VI**

---

# 🟦 UNIT – I: INTRODUCTION & DIGITAL IMAGE FUNDAMENTALS

## 📌 1.1 Digital Image Processing — Definition
├── **Definition:** Digital Image Processing (DIP) is the manipulation of a digital image **f(x, y)** using computer algorithms for enhancement, restoration, analysis, compression, or interpretation.
├── **Key Points:**
- Image = 2-D function f(x, y) where x, y = spatial coordinates and f = intensity (gray level)
- Three abstraction levels: low-level (preprocessing), mid-level (segmentation), high-level (interpretation)
- Two processing domains: **Spatial** (pixel-based) and **Frequency** (transform-based)
- Requires **sampling** (spatial discretization) + **quantization** (amplitude discretization)
- Applied across medicine, remote sensing, robotics, forensics, entertainment
├── **Important Terms:**
   - **Pixel:** Smallest addressable picture element
   - **f(x, y):** 2-D image function — intensity at (x, y)
   - **Gray level:** Numerical value of pixel intensity
├── **One-line Exam Answer:** Digital Image Processing is the algorithmic manipulation of a digital image f(x, y) for enhancement, restoration, analysis, or compression.

---

## 📌 1.2 Fields Using Digital Image Processing
├── **Definition:** DIP is applied wherever images are captured, analyzed, transmitted, or interpreted in digital form.
├── **Key Points:**
- **Medical imaging:** X-ray, CT, MRI, ultrasound, microscopy, mammography
- **Remote sensing:** LANDSAT, weather satellites, Mars rovers, drone imagery
- **Industrial automation:** PCB inspection, quality control, defect detection
- **Forensics & security:** Fingerprint, face recognition, ANPR, CCTV
- **Astronomy:** Hubble, James Webb telescope image processing
- **Robotics:** Autonomous vehicles, drones, computer vision
- **Document processing:** OCR, signature verification
- **Entertainment:** CGI in movies, gaming, photo editing
├── **One-line Exam Answer:** DIP is used in medical, remote sensing, industrial, forensic, astronomical, robotic, OCR, and entertainment systems.

---

## 📌 1.3 Fundamental Steps in Digital Image Processing
├── **Definition:** The sequential pipeline of operations applied to a digital image from raw acquisition to final interpretation.
├── **Key Points (10 steps + Knowledge Base):**
1. **Image Acquisition** — capture with sensor (camera, scanner)
2. **Image Enhancement** — improve subjective appearance
3. **Image Restoration** — recover from known degradation
4. **Color Image Processing** — operate on color channels
5. **Wavelets & Multi-resolution** — multi-scale representation
6. **Image Compression** — reduce data size
7. **Morphological Processing** — analyze shapes
8. **Image Segmentation** — partition into regions
9. **Representation & Description** — extract features
10. **Object Recognition** — assign labels / classify
├── **Diagram:**
```
Acquisition → Enhancement → Restoration → Color → Wavelets →
Compression → Morphology → Segmentation → Representation → Recognition
                              ↑
                       [ Knowledge Base ]
```
├── **One-line Exam Answer:** The fundamental steps are Acquisition → Enhancement → Restoration → Color → Wavelets → Compression → Morphology → Segmentation → Representation → Recognition, supported by a knowledge base.

---

## 📌 1.4 Components of an Image Processing System
├── **Definition:** Hardware + software stack required to capture, process, store, display and transmit digital images.
├── **Key Points:**

| Component | Function |
|---|---|
| **Image Sensors** | Convert light → electrical signal (CCD, CMOS) |
| **Specialized Hardware** | Frame grabber, DSP, GPU for fast ops |
| **Computer** | General-purpose PC running DIP software |
| **Image Processing Software** | MATLAB, OpenCV, ImageJ, Photoshop |
| **Mass Storage** | RAM (short-term), HDD/SSD (online), tape/cloud (archival) |
| **Image Display** | Monitor, LCD/LED, projector |
| **Hardcopy Device** | Printer, plotter |
| **Network** | Transmit images between systems |

├── **Diagram:**
```
[Sensor] → [Digitizer] → [Specialized HW] → [Computer + Software]
                                                    ↓
[Storage] ←→ [Display] ←→ [Hardcopy] ←→ [Network]
```
├── **One-line Exam Answer:** A DIP system has sensors, digitizers, specialized hardware, a computer with software, mass storage, display, hardcopy device, and a network.

---

## 📌 1.5 Image Formation Model (Illumination × Reflectance)
├── **Definition:** The intensity of any pixel f(x, y) is the product of illumination i(x, y) falling on the scene and reflectance r(x, y) of the object surface.
├── **Key Points:**
- Formula: **f(x, y) = i(x, y) × r(x, y)**
- **i(x, y)** = illumination (0 < i < ∞) — depends on light source
- **r(x, y)** = reflectance (0 ≤ r ≤ 1) — depends on surface
- r = 0: total absorption (black); r = 1: total reflection (white/snow)
- Range constraint: L_min ≤ f(x, y) ≤ L_max forms the gray scale
├── **Sample Reflectance Values:**

| Surface | r |
|---|---|
| Black velvet | 0.01 |
| Stainless steel | 0.65 |
| White wall | 0.80 |
| Snow | 0.93 |

├── **One-line Exam Answer:** The image formation model is f(x, y) = i(x, y) · r(x, y), where i is illumination and r is reflectance (0 ≤ r ≤ 1).

---

## 📌 1.6 Image Sampling
├── **Definition:** Sampling is the discretization of spatial coordinates (x, y) — converting a continuous image into a grid of pixels.
├── **Key Points:**
- Determines **spatial resolution** of the image
- Higher sampling rate → more pixels → finer detail
- **Nyquist criterion:** sample rate ≥ 2× highest frequency to avoid aliasing
- Low sampling → **aliasing** (moiré, jagged edges) and **pixelation**
- Produces an M × N matrix of pixel positions
├── **One-line Exam Answer:** Sampling discretizes the spatial coordinates of an image and determines its spatial resolution; under-sampling causes aliasing.

---

## 📌 1.7 Image Quantization
├── **Definition:** Quantization is the discretization of intensity (amplitude) values — mapping continuous brightness into L discrete gray levels.
├── **Key Points:**
- For k-bit image: **L = 2^k gray levels**
- Common values: k=1 (binary), k=8 (256 levels), k=24 (color)
- Storage = M × N × k bits
- Too few levels → **false contouring** (visible ridges in smooth regions)
- Determines **intensity (gray-level) resolution**
├── **Sampling vs Quantization:**

| Aspect | Sampling | Quantization |
|---|---|---|
| Acts on | (x, y) coordinates | Amplitude f |
| Affects | Spatial resolution | Intensity resolution |
| Parameter | M × N | L = 2^k |
| Low-value problem | Aliasing | False contouring |

├── **One-line Exam Answer:** Quantization discretizes intensity into L = 2^k discrete gray levels; too few levels produces false contouring.

---

## 📌 1.8 False Contouring
├── **Definition:** False contouring is a visible-ridge artifact in smooth-gradient regions of an image caused by insufficient quantization levels.
├── **Key Points:**
- Occurs when smooth intensity changes are forced into few discrete steps
- Most visible in uniform / smooth regions (skin, sky)
- Human eye is highly sensitive to artificial ridges
- Typically appears below 6 bits (64 levels)
- Solutions: increase quantization levels, apply dithering or error diffusion
├── **One-line Exam Answer:** False contouring is the appearance of visible ridges in smooth gradient regions caused by insufficient quantization levels; reduced by more bits or dithering.

---

## 📌 1.9 Pixel Neighborhoods (4-, Diagonal, 8-)
├── **Definition:** Geometric relationships between a pixel p(x, y) and its surrounding pixels — basis for all neighborhood operations.
├── **Key Points:**
- **N₄(p):** 4 horizontal/vertical neighbors
- **N_D(p):** 4 diagonal neighbors
- **N₈(p):** all 8 surrounding pixels = N₄ ∪ N_D
- Border pixels have fewer neighbors — special handling required
- Used in connectivity, path finding, distance computation, segmentation
├── **Diagram:**
```
   N4 (+ shape)        ND (X shape)         N8 (full square)
       [N]            [NW]   [NE]          [NW] [N] [NE]
   [W] [p] [E]            [p]               [W] [p] [E]
       [S]            [SW]   [SE]          [SW] [S] [SE]
```
├── **One-line Exam Answer:** A pixel's neighbors are N₄ (4 horizontal/vertical), N_D (4 diagonal), and N₈ (all 8 surrounding pixels).

---

## 📌 1.10 Pixel Adjacency (4-, 8-, m-connectivity)
├── **Definition:** Two pixels are connected if they are spatial neighbors AND their gray-level values belong to a similarity set V.
├── **Key Points:**
- **4-adjacency:** q ∈ N₄(p) AND values in V
- **8-adjacency:** q ∈ N₈(p) AND values in V
- **m-adjacency (mixed):** q ∈ N₄(p) OR (q ∈ N_D(p) AND N₄(p) ∩ N₄(q) ∩ V = ∅)
- 8-adjacency can create multiple paths — ambiguous
- m-adjacency was introduced to eliminate this path ambiguity
├── **Comparison:**

| Type | Diagonal allowed | Ambiguity |
|---|---|---|
| 4-adjacency | No | None |
| 8-adjacency | Yes | Possible |
| m-adjacency | Conditional | Resolved |

├── **One-line Exam Answer:** Pixels are 4-, 8-, or m-adjacent based on neighborhood and similarity; m-adjacency resolves the path ambiguity of 8-adjacency.

---

## 📌 1.11 Distance Measures Between Pixels
├── **Definition:** Mathematical methods to measure how far apart two pixels p(x, y) and q(s, t) are in a digital image grid.
├── **Key Points & Formulas:**
- **Euclidean (D_e):** D_e = √((x − s)² + (y − t)²) — true geometric distance
- **City-block (D₄):** D₄ = |x − s| + |y − t| — Manhattan distance
- **Chessboard (D₈):** D₈ = max(|x − s|, |y − t|) — king's move
- All satisfy: positivity, symmetry, triangle inequality
├── **Worked Example for p(2, 3), q(5, 7):**
```
D_e = √((2-5)² + (3-7)²) = √(9 + 16) = √25 = 5
D₄  = |2-5| + |3-7|     = 3 + 4 = 7
D₈  = max(|2-5|, |3-7|) = max(3, 4) = 4
```
├── **One-line Exam Answer:** Distance between two pixels can be Euclidean, City-block (D₄), or Chessboard (D₈) depending on application.

---

# 🟩 UNIT – II: IMAGE ENHANCEMENT IN THE SPATIAL DOMAIN

## 📌 2.1 Spatial Domain
├── **Definition:** The spatial domain is the image plane itself; enhancement is performed by direct manipulation of pixels rather than through transforms.
├── **Key Points:**
- General formulation: **g(x, y) = T[f(x, y)]**
- T can be point operation (one pixel) or mask operation (neighborhood)
- No Fourier transform involved
- Faster than frequency domain for small kernels
- Examples: histogram equalization, convolution, gamma correction
├── **Spatial vs Frequency Domain:**

| Feature | Spatial | Frequency |
|---|---|---|
| Operates on | Pixels directly | Fourier coefficients |
| Transform | Not needed | DFT / DCT required |
| Examples | Mean filter, Sobel | Ideal LPF, Butterworth |
| Speed | Fast (small kernels) | Fast (FFT) |

├── **One-line Exam Answer:** The spatial domain is the image plane where enhancement is performed by direct pixel manipulation via g(x, y) = T[f(x, y)].

---

## 📌 2.2 Basic Gray-Level Transformations
├── **Definition:** Point operations s = T(r) mapping each input intensity r to an output intensity s using a global mathematical function.
├── **Key Points & Formulas:**

| Transform | Formula | Purpose |
|---|---|---|
| **Identity** | s = r | No change |
| **Negative** | s = L − 1 − r | Invert gray levels (X-ray) |
| **Log** | s = c · log(1 + r) | Compress dynamic range |
| **Inverse log** | s = c · (e^r − 1) | Expand compressed values |
| **Power-law / Gamma** | s = c · r^γ | Gamma correction |
| **Threshold** | s = 0 if r<T else L−1 | Binary image |

├── **One-line Exam Answer:** Basic gray-level transformations s = T(r) include identity, negative, log, power-law (gamma), and threshold mappings.

---

## 📌 2.3 Image Negative
├── **Definition:** Negative transformation reverses gray levels — dark pixels become light and vice versa — using s = L − 1 − r.
├── **Key Points:**
- For 8-bit images: **s = 255 − r**
- Enhances white/gray detail in dark backgrounds
- Used heavily in mammograms, X-rays, MRI
- Reversible — applying twice gives the original
- Pure point operation, O(MN) complexity
├── **Lookup Example:**

| r (input) | s = 255 − r |
|---|---|
| 0 | 255 |
| 100 | 155 |
| 200 | 55 |
| 255 | 0 |

├── **One-line Exam Answer:** Negative transformation s = L − 1 − r inverts gray levels and is used to enhance white/gray details in dark backgrounds such as X-rays.

---

## 📌 2.4 Log Transformation
├── **Definition:** Compresses the dynamic range of an image by mapping a wide range of input values into a narrower output range via the logarithm.
├── **Key Points:**
- Formula: **s = c · log(1 + r)**
- Expands dark pixels and compresses bright pixels
- c chosen so max output = 255 (8-bit)
- Used for displaying **Fourier magnitude spectra** with very wide range
- Mimics human eye's logarithmic intensity perception
├── **One-line Exam Answer:** Log transformation s = c · log(1 + r) compresses dynamic range, expanding dark pixels and compressing bright ones — used for displaying Fourier spectra.

---

## 📌 2.5 Power-law (Gamma) Transformation
├── **Definition:** s = c · r^γ provides flexible contrast control by changing γ — used for gamma correction in displays.
├── **Key Points:**
- γ < 1 brightens dark image (boost shadows)
- γ > 1 darkens bright image (compress shadows)
- γ = 1 is the identity transformation
- CRT monitors have natural γ ≈ 2.2, so capture pre-applies γ ≈ 1/2.2
- Foundation of gamma correction in cameras, TVs, monitors
├── **Use Cases:**

| Gamma | Effect | Use |
|---|---|---|
| < 1 | Brighten | MRI dark images |
| > 1 | Darken | Reduce glare |
| = 2.2 | CRT correction | Display |

├── **One-line Exam Answer:** Power-law transformation s = c · r^γ is used for gamma correction; γ<1 brightens and γ>1 darkens an image.

---

## 📌 2.6 Histogram of an Image
├── **Definition:** A histogram plots the count of pixels n_k against each gray level r_k: h(r_k) = n_k.
├── **Key Points:**
- Normalized histogram: **p(r_k) = n_k / MN** (probability)
- Σ p(r_k) = 1 over all k = 0..L−1
- Dark image → concentrated on left
- Bright image → concentrated on right
- Low-contrast → narrow peak; high-contrast → spread across full range
- Bimodal histogram suggests object + background (used for thresholding)
├── **Interpretation:**

| Histogram Pattern | Image Quality |
|---|---|
| Concentrated left | Too dark |
| Concentrated right | Too bright |
| Narrow peak | Low contrast |
| Spread across | Good contrast |
| Bimodal | Object + background |

├── **One-line Exam Answer:** A histogram plots pixel count h(r_k) = n_k against gray level and reveals the brightness and contrast distribution of an image.

---

## 📌 2.7 Histogram Equalization (HE)
├── **Definition:** Histogram Equalization is an automatic contrast-enhancement method that maps pixel intensities through their cumulative distribution function (CDF) to produce an approximately uniform output histogram.
├── **Key Points (Algorithm):**
1. Compute histogram **h(r_k) = n_k**
2. Normalize: **p_r(r_k) = n_k / MN**
3. Compute CDF: **cdf(r_k) = Σ p_r(r_j)** for j = 0..k
4. Compute mapping: **s_k = round((L − 1) × cdf(r_k))**
5. Replace each pixel: r_k → s_k
├── **Formula:** **s_k = T(r_k) = (L − 1) · Σ_{j=0..k} p_r(r_j)**
├── **Worked Example (3-bit, 64 pixels):**

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

├── **One-line Exam Answer:** Histogram equalization maps pixels via s_k = (L − 1) · cdf(r_k) to obtain an approximately uniform histogram and maximize global contrast.

---

## 📌 2.8 Histogram Matching (Specification)
├── **Definition:** Histogram matching transforms an image so its output histogram has a user-specified shape — useful when uniform distribution (HE) is not desired.
├── **Key Points (Algorithm):**
1. Compute CDF of input image: s = T(r)
2. Compute CDF of desired histogram: v = G(z)
3. For each s, find z = G⁻¹(s) by inverse mapping
4. Map each input pixel: r → s → z
5. Output has the desired histogram distribution
├── **HE vs Histogram Matching:**

| Feature | Equalization | Matching |
|---|---|---|
| Output | Uniform | User-specified |
| Flexibility | Low (automatic) | High (designer-defined) |
| Steps | 1 CDF mapping | 2 CDFs + inverse |
| Use | General enhancement | Match reference image |

├── **One-line Exam Answer:** Histogram matching produces an image with a user-specified histogram via two CDF mappings and an inverse transformation G⁻¹.

---

## 📌 2.9 Arithmetic Operations on Images
├── **Definition:** Pixel-wise mathematical operations between two images (or an image and a scalar) — addition, subtraction, multiplication, division.
├── **Key Points & Applications:**

| Operation | Formula | Application |
|---|---|---|
| Addition | s = f + g | Noise reduction (averaging), double exposure |
| Subtraction | s = f − g | Motion detection, DSA (medical), background removal |
| Multiplication | s = f · g | Masking (ROI extraction), shading correction |
| Division | s = f / g | Flat-field correction, illumination normalization |

├── **Image Averaging:** ḡ(x, y) = (1/K) · Σ g_i(x, y) — noise variance reduces by 1/K
├── **One-line Exam Answer:** Arithmetic operations between images are used for noise reduction (add/average), motion detection (subtract), masking (multiply), and shading correction (divide).

---

## 📌 2.10 Logical Operations on Binary Images
├── **Definition:** Bitwise Boolean operations (AND, OR, NOT, XOR, NAND, NOR) on binary images for masking, region union, and change detection.
├── **Truth Table:**

| p | q | AND | OR | XOR | NAND | NOR |
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |

├── **Applications:**
   - **AND** — masking, ROI intersection
   - **OR** — region union, combining features
   - **NOT** — complement, invert mask
   - **XOR** — difference / change detection
├── **One-line Exam Answer:** Logical operations (AND, OR, NOT, XOR) on binary images are used for masking, region union/intersection, complement, and difference detection.

---

## 📌 2.11 Spatial Filtering (Convolution)
├── **Definition:** A neighborhood operation where a mask (kernel) is moved across the image and the output pixel is computed as a weighted sum of nearby pixels.
├── **Key Points:**
- Formula: **g(x, y) = Σ Σ w(s, t) · f(x + s, y + t)**
- Two categories: smoothing (low-pass) and sharpening (high-pass)
- Mask size typically 3×3, 5×5, 7×7 (odd, symmetric)
- Boundary handling — zero padding, replicate, mirror
- Procedure: position mask → multiply → sum → place → slide
├── **One-line Exam Answer:** Spatial filtering convolves a mask w with image f to produce g(x, y) = ΣΣ w(s, t)·f(x+s, y+t) — used for smoothing or sharpening.

---

## 📌 2.12 Smoothing (Low-Pass) Filters
├── **Definition:** Smoothing filters blur the image, reduce noise, and remove small details by averaging neighborhood pixels.
├── **Key Points:**
- **Mean (Box) filter** — simple arithmetic average (linear)
- **Gaussian filter** — weighted average (linear, less blur)
- **Median filter** — non-linear, sorts and picks middle (excellent for salt-and-pepper)
- Larger kernel → more smoothing but more edge blur
- Used as preprocessing for segmentation / edge detection
├── **Common Masks:**
```
3×3 Mean (1/9):           3×3 Gaussian (1/16):
  1 1 1                      1 2 1
  1 1 1                      2 4 2
  1 1 1                      1 2 1
```
├── **Smoothing Comparison:**

| Filter | Type | Best for | Edge Preservation |
|---|---|---|---|
| Mean (Box) | Linear | Gaussian noise | Poor |
| Gaussian | Linear | Gaussian noise | Better |
| Median | Non-linear | Salt-and-pepper | Excellent |

├── **One-line Exam Answer:** Smoothing filters (mean, Gaussian, median) blur the image and reduce noise; median preserves edges best.

---

## 📌 2.13 Sharpening (High-Pass) Filters
├── **Definition:** Sharpening filters enhance edges and fine details by emphasizing intensity discontinuities using derivatives.
├── **Key Points:**
- **First derivative:** Sobel, Prewitt (gradient operators)
- **Second derivative:** Laplacian (isotropic)
- **Gradient magnitude:** |∇f| = √(G_x² + G_y²)
- **Gradient direction:** θ = arctan(G_y / G_x)
- Sharpened image = original + edge response
├── **Sobel Operators (3×3):**
```
G_x = [-1  0  1]      G_y = [-1 -2 -1]
      [-2  0  2]            [ 0  0  0]
      [-1  0  1]            [ 1  2  1]
```
├── **Laplacian Mask:**
```
∇²f = f(x+1,y) + f(x-1,y) + f(x,y+1) + f(x,y-1) - 4·f(x,y)

      [ 0 -1  0]
Mask: [-1  4 -1]
      [ 0 -1  0]
```
├── **One-line Exam Answer:** Sharpening filters use derivatives — Sobel/Prewitt (first-order gradient) detect edges and Laplacian (second-order) enhances all-direction discontinuities.

---

## 📌 2.14 Combining Spatial Enhancement Methods
├── **Definition:** Real enhancement often chains multiple techniques sequentially to handle complex image-quality problems.
├── **Key Points (Skeletal Image Pipeline):**
1. Apply **Laplacian** to sharpen edges
2. Apply **Sobel gradient** to produce edge mask
3. **Smooth** the Sobel image (5×5 box) for cleaner mask
4. **Multiply** Laplacian result × smoothed mask
5. **Add** the result to original
6. Apply **power-law (gamma) transform** for dynamic range
├── **One-line Exam Answer:** Combining spatial methods (Laplacian + Sobel + smoothing + gamma) chains operations to enhance edges, reduce noise, and stretch dynamic range.

---

# 🟨 UNIT – III: IMAGE RESTORATION

## 📌 3.1 Image Restoration vs Image Enhancement
├── **Definition:** Image restoration is the objective recovery of an image from a degraded version using a mathematical model of the degradation, whereas enhancement is the subjective improvement of appearance.
├── **Key Points:**

| Feature | Image Enhancement | Image Restoration |
|---|---|---|
| Goal | Subjective appearance | Recover original from degradation |
| Approach | Heuristic / visual | Mathematical / objective |
| Knowledge needed | Visual preference | Degradation function H, noise η |
| Techniques | Histogram, sharpen, gamma | Inverse filter, Wiener, CLS |
| Output | "Looks better" | "Closer to original" |

├── **Examples:**
   - Enhancement: brightening a dark photo using gamma
   - Restoration: deblurring a motion-blurred satellite image with Wiener filter
├── **One-line Exam Answer:** Enhancement subjectively improves image appearance while restoration mathematically reverses a known degradation to recover the original.

---

## 📌 3.2 Image Degradation / Restoration Model
├── **Definition:** A model that expresses the degraded image g(x, y) as the convolution of the original image f(x, y) with a degradation function h(x, y) plus additive noise η(x, y).
├── **Key Points & Formulas:**
- **Spatial domain:** g(x, y) = h(x, y) * f(x, y) + η(x, y)
- **Frequency domain:** G(u, v) = H(u, v) · F(u, v) + N(u, v)
- f(x, y) = original image (unknown, to recover)
- h(x, y) = degradation function (PSF)
- η(x, y) = additive noise
- Restoration goal: estimate **f̂(x, y) ≈ f(x, y)**
├── **Block Diagram:**
```
                          η(x, y) noise
                              ↓
  f(x,y) → [ H(degrad.) ] → ⊕ → g(x,y) → [Restoration Filter] → f̂(x,y)
```
├── **One-line Exam Answer:** The degradation model is g(x, y) = h(x, y) * f(x, y) + η(x, y) — degraded image equals original convolved with degradation function plus noise.

---

## 📌 3.3 Noise Models
├── **Definition:** Mathematical descriptions of probability density functions (PDFs) governing noise that contaminates digital images.
├── **Key Points & PDFs:**
- **Gaussian:** p(z) = (1/σ√2π) · exp(−(z − μ)² / 2σ²) → sensor / electronic noise
- **Rayleigh:** p(z) = (2/b)(z − a) · exp(−(z − a)²/b) → range imaging
- **Erlang (Gamma):** p(z) = (a^b · z^(b−1) / (b−1)!) · exp(−az) → laser imaging
- **Exponential:** p(z) = a · exp(−az) → laser imaging
- **Uniform:** p(z) = 1/(b − a) for a ≤ z ≤ b → simulation
- **Impulse (Salt-and-Pepper):** p(z) = P_a (z=a), P_b (z=b)
├── **Noise → Best Filter Mapping:**

| Noise | Source | Best Filter |
|---|---|---|
| Gaussian | Sensor / electronic | Mean / Gaussian |
| Salt-and-pepper | Transmission errors | Median |
| Salt only | High-value spikes | Min |
| Pepper only | Low-value spikes | Max |
| Rayleigh | Range imaging | Geometric mean |

├── **One-line Exam Answer:** Common noise PDFs are Gaussian, Rayleigh, Erlang, Exponential, Uniform, and impulse (Salt-and-Pepper) — each requires a specific filter.

---

## 📌 3.4 Mean Filters (Arithmetic, Geometric, Harmonic, Contra-harmonic)
├── **Definition:** Linear and non-linear filters that average neighborhood pixels to reduce noise.
├── **Key Points & Formulas:**
- **Arithmetic Mean:** f̂ = (1/mn) · Σ g(s, t)   → Gaussian noise; blurs edges
- **Geometric Mean:** f̂ = [Π g(s, t)]^(1/mn)   → Gaussian; less blur; fails on zero pixels
- **Harmonic Mean:** f̂ = mn / Σ (1 / g(s, t))   → salt + Gaussian; fails on pepper
- **Contra-harmonic Mean:** f̂ = Σ g^(Q+1) / Σ g^Q   → Q>0 removes pepper; Q<0 removes salt
├── **Mean Filter Summary:**

| Filter | Best for |
|---|---|
| Arithmetic | Gaussian / uniform noise |
| Geometric | Gaussian noise (better detail) |
| Harmonic | Salt + Gaussian noise |
| Contra-harmonic Q>0 | Pepper noise |
| Contra-harmonic Q<0 | Salt noise |

├── **One-line Exam Answer:** Mean filters include arithmetic, geometric, harmonic, and contra-harmonic — each suited to different noise types.

---

## 📌 3.5 Order-Statistic Filters (Median, Max, Min, Midpoint)
├── **Definition:** Non-linear filters whose output depends on ranking (sorting) the values in the neighborhood.
├── **Key Points & Formulas:**
- **Median:** f̂ = median { g(s, t) } → best for salt-and-pepper
- **Max:** f̂ = max { g(s, t) } → removes pepper; brightens
- **Min:** f̂ = min { g(s, t) } → removes salt; darkens
- **Midpoint:** f̂ = ½(max + min) → Gaussian, uniform
- **Alpha-trimmed mean** — trim extremes then average; mixed noise
├── **Order-Statistic Filter Summary:**

| Filter | Removes | Side Effect |
|---|---|---|
| Median | Salt-and-pepper | Slight smoothing |
| Max | Pepper | Brightens |
| Min | Salt | Darkens |
| Midpoint | Gaussian / uniform | Mild blur |

├── **One-line Exam Answer:** Order-statistic filters rank neighborhood pixels — median removes salt-and-pepper, max removes pepper, min removes salt.

---

## 📌 3.6 Motion Blur Degradation
├── **Definition:** A degradation caused by relative motion between the camera and the scene during exposure — modeled as a convolution with a linear PSF.
├── **Key Points & Formulas:**
- **Spatial PSF (1D motion length L):** h(x, y) = 1/L for 0 ≤ x ≤ L, y = 0; else 0
- **Frequency domain:** H(u, v) = (T / π(ua + vb)) · sin(π(ua + vb)) · exp(−jπ(ua + vb))
- Parameters: length L, angle θ, exposure T
- Causes: camera shake, object motion, long exposure, vibration
- Restoration: inverse filter (no noise) or Wiener filter (with noise)
├── **One-line Exam Answer:** Motion blur is caused by relative motion during exposure and is modeled as a convolution with a linear PSF of length L and angle θ.

---

## 📌 3.7 Prior Knowledge in Restoration
├── **Definition:** Information about the degradation function, noise, scene, or imaging system known in advance — used to choose and parameterize restoration filters.
├── **Key Points:**
- Without prior knowledge → blind deconvolution (hard, iterative)
- With knowledge of H → enables inverse / Wiener filtering
- With knowledge of noise PDF → enables noise-specific filters
- Sources: optical system, atmosphere model, motion sensors, calibration
- More knowledge → better restoration accuracy
├── **One-line Exam Answer:** Prior knowledge of the degradation function and noise statistics enables effective restoration via inverse, Wiener, or constrained least-squares filtering.

---

## 📌 3.8 Inverse Filter vs Wiener Filter
├── **Definition:** Inverse filter directly divides spectra (F̂ = G/H); Wiener filter is the optimum mean-square-error solution that balances inversion against noise suppression.
├── **Key Formulas:**
- **Inverse filter:** F̂(u, v) = G(u, v) / H(u, v)
- **Wiener filter:** F̂(u, v) = [H*(u, v) / (|H(u, v)|² + S_η/S_f)] · G(u, v)
├── **Inverse vs Wiener Comparison:**

| Feature | Inverse | Wiener |
|---|---|---|
| Knowledge needed | H | H + S_η + S_f |
| Noise handling | Amplifies | Optimally suppresses |
| Best when | Noise = 0 | Noise present |
| Failure mode | Blows up at H ≈ 0 | Smoothly handles all freq |

├── **Note:** When noise → 0, Wiener filter reduces to the inverse / pseudo-inverse filter.
├── **One-line Exam Answer:** Inverse filter (F̂ = G/H) amplifies noise; Wiener filter is optimal in MSE sense and balances inversion against noise suppression.

---

# 🟧 UNIT – IV: COLOR IMAGE PROCESSING & IMAGE COMPRESSION

## 📌 4.1 Color Fundamentals
├── **Definition:** Color is the human perception of light wavelengths in the visible spectrum (400–700 nm), characterized by brightness, hue, and saturation.
├── **Key Points:**
- Visible spectrum: 400 nm (violet) – 700 nm (red)
- **Additive primaries** = R, G, B (used for light: monitors, sensors)
- **Subtractive primaries** = C, M, Y (used for pigments: printing)
- Three attributes: brightness (intensity), hue (dominant wavelength), saturation (purity)
- Tri-stimulus theory: retina has S, M, L cones
├── **Color Primaries:**

| Type | Primaries | Use |
|---|---|---|
| Additive | R G B | Monitors, lights |
| Subtractive | C M Y(K) | Printing, paint |

├── **One-line Exam Answer:** Color has three attributes — brightness, hue, saturation; additive primaries are RGB (light), subtractive are CMY (pigment).

---

## 📌 4.2 RGB Color Model
├── **Definition:** A 3-D color model that represents colors as additive combinations of Red, Green, and Blue primaries, visualized as a unit cube.
├── **Key Points:**
- Used in monitors, cameras, image sensors
- Each axis 0–1 (or 0–255 in 8-bit)
- Black at (0, 0, 0); White at (1, 1, 1)
- Main diagonal = gray line
- 24-bit RGB → 256³ = 16.7 million colors
├── **Cube Vertices:**

| Color | R | G | B |
|---|---|---|---|
| Black | 0 | 0 | 0 |
| Red | 1 | 0 | 0 |
| Green | 0 | 1 | 0 |
| Blue | 0 | 0 | 1 |
| Yellow | 1 | 1 | 0 |
| Cyan | 0 | 1 | 1 |
| Magenta | 1 | 0 | 1 |
| White | 1 | 1 | 1 |

├── **Diagram:**
```
       White (1,1,1)
       /|
   Yellow ── Cyan
    /|     /|
 Red ── Magenta ── Blue
   \  |   /
   Black (0,0,0)
```
├── **One-line Exam Answer:** The RGB color model represents colors as additive combinations of Red, Green, and Blue primaries, visualized as a unit cube.

---

## 📌 4.3 HSI Color Model
├── **Definition:** A perceptual color model that decouples color into Hue (dominant wavelength), Saturation (purity), and Intensity (brightness) — closer to human vision.
├── **Key Points:**
- H — angle 0°–360° around color circle
- S — 0 (gray) to 1 (pure color)
- I — 0 (black) to 1 (white)
- Decouples color from brightness → ideal for image processing
- Used in segmentation, object recognition, color manipulation
├── **RGB → HSI Conversion Formulas:**
```
I = (R + G + B) / 3
S = 1 − [3 · min(R, G, B) / (R + G + B)]
θ = arccos { [½((R−G) + (R−B))] / √((R−G)² + (R−B)(G−B)) }
H = θ        if B ≤ G
H = 360 − θ  if B > G
```
├── **RGB vs HSI:**

| Feature | RGB | HSI |
|---|---|---|
| Basis | Light primaries | Human perception |
| Intensity decoupled | No | Yes |
| Hardware | Display, sensor | Processing, editing |
| Geometry | Cube | Cone / cylinder |

├── **One-line Exam Answer:** HSI represents color in terms of Hue (dominant wavelength), Saturation (purity), and Intensity (brightness) — useful for processing as it matches human perception.

---

## 📌 4.4 Pseudocoloring
├── **Definition:** Pseudocoloring assigns colors to gray-level values of a monochrome image to make features more visible — humans distinguish thousands of colors but only ~24 gray shades.
├── **Key Points:**
- **Intensity slicing** — divide gray range into intervals, assign colors
- **Gray-to-color transforms** — three independent f_R, f_G, f_B functions
- Applications: medical (CT/MRI), thermal imaging, astronomy, weather radar
- Not "true color" — purely a visualization aid
├── **One-line Exam Answer:** Pseudocoloring maps gray levels to colors via intensity slicing or independent R/G/B transformations to enhance visualization.

---

## 📌 4.5 Color Quantization
├── **Definition:** Color quantization reduces the number of distinct colors in an image (e.g., from 16.7M to 256) to fit limited displays or file formats.
├── **Key Points:**
- Required for **GIF** (256-color max), older 8-bit displays, embedded systems
- Algorithms: uniform quantization, median-cut, octree, K-means clustering
- Trade-off: smaller palette → smaller file but color banding
- Used in image compression (vector quantization)
├── **Algorithm Comparison:**

| Algorithm | Approach | Quality |
|---|---|---|
| Uniform | Equal subdivision | Low |
| Median-cut | Recursive split at median | Good |
| Octree | Tree-based subdivision | Good |
| K-means | Clustering | Best (slower) |

├── **One-line Exam Answer:** Color quantization reduces an image's color palette using algorithms like median-cut or K-means — used in GIF and limited-display systems.

---

## 📌 4.6 Color Constancy
├── **Definition:** Color constancy is the ability of a vision system to perceive consistent colors of objects despite changes in illumination.
├── **Key Points:**
- Without constancy, white paper looks yellow under tungsten light
- Implemented in cameras as auto white-balance (AWB)
- Algorithms: gray-world, white-patch (Retinex), Bayesian, ML
- Critical for object recognition and machine vision
- Modern AI cameras learn illumination from training data
├── **One-line Exam Answer:** Color constancy ensures consistent color perception under different lighting and is implemented via white balance, gray-world assumption, Retinex, or ML methods.

---

## 📌 4.7 Image Compression Fundamentals
├── **Definition:** Image compression reduces the data size needed to represent an image by exploiting redundancies in the data.
├── **Key Points:**
- Four redundancy types: coding, spatial (interpixel), temporal, psycho-visual
- Compression Ratio: **CR = original size / compressed size**
- Two categories: lossless (exact recovery) and lossy (approximate)
- Required for storage, transmission, streaming, mobile devices
- Lossless CR ~ 2:1 – 5:1; lossy CR ~ 10:1 – 100:1
├── **Redundancy Types:**

| Type | Cause | Removed By |
|---|---|---|
| Coding | Equal-length codes | Huffman, Arithmetic |
| Spatial | Pixel correlation | RLE, predictive |
| Temporal | Frame similarity | Motion compensation |
| Psycho-visual | Imperceptible info | Quantization |

├── **One-line Exam Answer:** Image compression reduces data size by removing coding, spatial, temporal, and psycho-visual redundancies.

---

## 📌 4.8 Lossless vs Lossy Compression
├── **Definition:** Lossless compression reconstructs the original exactly; lossy compression sacrifices some quality for higher compression.
├── **Key Comparison:**

| Feature | Lossless | Lossy |
|---|---|---|
| Recovery | Bit-exact | Approximate |
| Compression ratio | 2:1 – 5:1 | 10:1 – 100:1 |
| Examples | PNG, GIF, TIFF | JPEG, MPEG, WebP |
| Techniques | Huffman, RLE, LZW, Arithmetic | DCT, wavelet, VQ |
| Use cases | Medical, legal, archival | Web, video, streaming |

├── **Quality Metrics:**
   - **MSE** = (1/MN) · Σ(f − f̂)²
   - **PSNR** = 10 · log₁₀(255² / MSE) dB
├── **One-line Exam Answer:** Lossless compression recovers data exactly (PNG, GIF); lossy compression sacrifices some quality for higher compression (JPEG, MPEG).

---

## 📌 4.9 Lossless Compression Techniques
├── **Definition:** Methods that exactly recover the original image data by exploiting coding and spatial redundancy.
├── **Key Points:**

| Technique | Approach | Used in |
|---|---|---|
| **Huffman** | Variable-length prefix code | JPEG, PNG |
| **RLE** | Replace runs with (count, value) | BMP, FAX |
| **LZW** | Dictionary-based substring coding | GIF, TIFF |
| **Arithmetic** | Encodes message as single number | JPEG 2000 |
| **DPCM** | Predict + encode error | Lossless JPEG |

├── **RLE Example:** AAAAABBBCCDA → 5A 3B 2C 1D 1A
├── **One-line Exam Answer:** Lossless techniques include Huffman (variable-length coding), RLE (run-length), LZW (dictionary), Arithmetic, and DPCM (predictive).

---

## 📌 4.10 Lossy Predictive Coding (DPCM)
├── **Definition:** Predicts each pixel from past pixels and quantizes the prediction error for compression.
├── **Key Points (Algorithm):**
1. Predict the pixel: **f̂(n) = a₁f(n−1) + a₂f(n−2) + ...**
2. Compute error: **e(n) = f(n) − f̂(n)**
3. Quantize the error: **ê(n) = Q(e(n))**
4. Encode the quantized error
5. Decoder reconstructs by predictor + adding ê(n)
├── **Trade-off:** Smaller quantization step → better quality but larger file
├── **One-line Exam Answer:** Lossy predictive coding (DPCM) predicts pixels from neighbors and quantizes the prediction error to achieve compression.

---

## 📌 4.11 Vector Quantization (VQ)
├── **Definition:** A compression technique that maps groups (vectors) of pixels to a small codebook of representative vectors and stores only their indices.
├── **Key Points:**
- Codebook generated using LBG (Linde-Buzo-Gray) or K-means algorithm
- Encoding: divide image into blocks, find nearest codeword, store index
- Decoding: lookup codeword by index, reassemble
- CR depends on codebook size (e.g., 16-pixel block + 8-bit index = 16× compression)
- Applications: image, speech, video compression
├── **LBG Algorithm:**
1. Initialize K codewords
2. Assign each training vector to nearest codeword (Euclidean)
3. Recompute codeword centroids
4. Iterate until distortion converges
├── **One-line Exam Answer:** Vector quantization maps image blocks to indices in a codebook built via LBG / K-means clustering.

---

## 📌 4.12 JPEG Compression Standard
├── **Definition:** JPEG (Joint Photographic Experts Group) is the most widely used lossy compression standard for photographic images, based on the 8×8 DCT.
├── **Key Points (8-Step Algorithm):**
1. **Color conversion** — RGB → YCbCr
2. **Chrominance subsampling** — 4:2:0 (halve Cb, Cr resolution)
3. **Block splitting** — divide image into 8×8 blocks
4. **DCT** — apply 2D-DCT to each 8×8 block
5. **Quantization** — divide DCT coefficients by Q-table (LOSSY step)
6. **Zigzag scan** — reorder 64 coefficients (DC → low → high freq)
7. **Run-length encoding** — encode runs of zeros
8. **Huffman coding** — entropy-code remaining values
├── **Diagram:**
```
RGB → YCbCr → Subsample(4:2:0) → 8×8 Blocks → DCT →
Quantize → Zigzag → RLE → Huffman → JPEG file
```
├── **DCT Formula:**
F(u, v) = (1/4) · C(u) · C(v) · ΣΣ f(x, y) · cos[(2x+1)uπ/16] · cos[(2y+1)vπ/16]
where C(u) = 1/√2 for u=0; 1 otherwise
├── **CR achieved:** 10:1 – 50:1 with minimal visible loss
├── **One-line Exam Answer:** JPEG pipeline: RGB → YCbCr → Subsample → 8×8 DCT → Quantize → Zigzag → RLE → Huffman; achieves 10:1 – 50:1 compression.

---

# 🟪 UNIT – V: MORPHOLOGICAL IMAGE PROCESSING

## 📌 5.1 Morphological Image Processing — Preliminaries
├── **Definition:** Morphological image processing uses set theory to analyze and process shapes in images, primarily binary images but extendable to grayscale.
├── **Key Points:**
- Two basic operations: dilation (⊕) and erosion (⊖)
- Two composite operations: opening (∘) and closing (•)
- Operations use a structuring element (SE) as a probe
- Binary image = set of foreground pixels in Z²
- Applications: boundary extraction, noise removal, skeletonization, OCR
├── **Set Operations Used:**

| Operation | Symbol |
|---|---|
| Union | A ∪ B |
| Intersection | A ∩ B |
| Complement | A^c |
| Difference | A − B |
| Reflection | B̂ |
| Translation | (A)_z |

├── **One-line Exam Answer:** Morphological image processing applies set-theoretic operations (dilation, erosion, opening, closing, hit-or-miss) to analyze image shapes.

---

## 📌 5.2 Structuring Element (SE)
├── **Definition:** A structuring element is a small binary mask used as a probe to investigate the structure of a larger image.
├── **Key Points:**
- Has a defined origin (typically the center)
- Common shapes: 3×3 square, cross (+), disk, line
- Choice of SE determines the effect of the operation
- SE is reflected (B̂) in erosion and hit-or-miss operations
- 3×3 square is most common
├── **Examples:**
```
3×3 Square:          Cross (+):           Disk (5×5):
1 1 1                0 1 0                0 1 1 1 0
1 1 1                1 1 1                1 1 1 1 1
1 1 1                0 1 0                1 1 1 1 1
                                          1 1 1 1 1
                                          0 1 1 1 0
```
├── **One-line Exam Answer:** A structuring element is a small mask (square, cross, disk) with a defined origin, used as a probe in morphological operations.

---

## 📌 5.3 Dilation
├── **Definition:** Dilation of set A by structuring element B, denoted A ⊕ B, expands binary objects by adding pixels where B intersects A.
├── **Key Points & Formula:**
- **Formula:** A ⊕ B = { z | (B̂)_z ∩ A ≠ ∅ }
- Effects: grows / thickens objects, fills small holes, connects nearby parts
- Properties: commutative, associative
- Dual to erosion via complement: (A ⊖ B)^c = A^c ⊕ B̂
- Applications: bridge small gaps, thicken thin features, OCR preprocessing
├── **Example (1 pixel dilated by 3×3 SE → 3×3 block):**
```
A:                A ⊕ B:
0 0 0 0 0         0 0 0 0 0
0 0 0 0 0         0 1 1 1 0
0 0 1 0 0    →    0 1 1 1 0
0 0 0 0 0         0 1 1 1 0
0 0 0 0 0         0 0 0 0 0
```
├── **One-line Exam Answer:** Dilation A ⊕ B grows binary objects, fills small holes, and connects nearby parts using SE B.

---

## 📌 5.4 Erosion
├── **Definition:** Erosion of set A by structuring element B, denoted A ⊖ B, shrinks binary objects by keeping only pixels where B fully fits inside A.
├── **Key Points & Formula:**
- **Formula:** A ⊖ B = { z | B_z ⊆ A }
- Effects: shrinks / thins objects, removes small noise specks, eliminates thin connections
- NOT commutative
- Dual to dilation: (A ⊖ B)^c = A^c ⊕ B̂
- Applications: noise removal, separate touching objects, find boundaries
├── **Example (3×3 block eroded → single pixel):**
```
A:                A ⊖ B:
0 0 0 0 0         0 0 0 0 0
0 1 1 1 0         0 0 0 0 0
0 1 1 1 0    →    0 0 1 0 0
0 1 1 1 0         0 0 0 0 0
0 0 0 0 0         0 0 0 0 0
```
├── **One-line Exam Answer:** Erosion A ⊖ B shrinks objects, removes small noise specks, and eliminates thin features; dual to dilation.

---

## 📌 5.5 Opening
├── **Definition:** Opening of A by B (A ∘ B) is erosion followed by dilation — smooths contours, removes small bright objects, and breaks thin connections.
├── **Key Points & Formula:**
- **Formula:** A ∘ B = (A ⊖ B) ⊕ B
- Effects: removes small bright objects, smooths outer contours, preserves overall size
- Anti-extensive: A ∘ B ⊆ A
- Idempotent: (A ∘ B) ∘ B = A ∘ B
- Applications: salt-noise removal, object outline smoothing, granulometry
├── **One-line Exam Answer:** Opening A ∘ B = (A ⊖ B) ⊕ B — erodes then dilates; removes small bright objects, smooths contours, removes salt noise.

---

## 📌 5.6 Closing
├── **Definition:** Closing of A by B (A • B) is dilation followed by erosion — fills small holes inside objects, connects nearby objects, and smooths concave contours.
├── **Key Points & Formula:**
- **Formula:** A • B = (A ⊕ B) ⊖ B
- Effects: fills small holes, connects nearby objects, smooths concave contours, preserves overall shape
- Extensive: A ⊆ A • B
- Idempotent: (A • B) • B = A • B
- Applications: pepper-noise removal, fill gaps in characters (OCR)
├── **Opening vs Closing:**

| Feature | Opening (A ∘ B) | Closing (A • B) |
|---|---|---|
| Sequence | Erode → Dilate | Dilate → Erode |
| Removes | Small bright objects | Small dark holes |
| Effect | Smooth outer contour | Smooth inner contour |
| Noise removed | Salt (bright specks) | Pepper (dark specks) |

├── **One-line Exam Answer:** Closing A • B = (A ⊕ B) ⊖ B — dilates then erodes; fills small holes and removes pepper noise.

---

## 📌 5.7 Hit-or-Miss Transformation (HMT)
├── **Definition:** A morphological operation that detects specific shapes / patterns in a binary image using TWO disjoint structuring elements — one for foreground (hit) and one for background (miss).
├── **Key Points & Formula:**
- **Formula:** A ⊛ B = (A ⊖ B₁) ∩ (A^c ⊖ B₂)
- B₁ = foreground pattern (must fit inside A)
- B₂ = background pattern (must fit inside A^c)
- B₁ and B₂ must be disjoint
- Applications: corner detection, isolated point detection, line endpoint detection, thinning, skeletonization
├── **Top-Left Corner Detection Example:**
```
B₁ (foreground hit):     B₂ (background miss):
0 0 0                    1 1 1
0 1 1                    1 0 0
0 1 1                    1 0 0
```
├── **One-line Exam Answer:** Hit-or-miss A ⊛ B = (A ⊖ B₁) ∩ (A^c ⊖ B₂) detects specific shapes using a foreground-hit and background-miss SE pair.

---

## 📌 5.8 Basic Morphological Algorithms
├── **Definition:** Composite morphological algorithms built on dilation and erosion for shape analysis.
├── **Algorithm Reference Table:**

| Algorithm | Formula | Purpose |
|---|---|---|
| **Boundary extraction** | β(A) = A − (A ⊖ B) | Find object edges |
| **Hole filling** | X_k = (X_{k-1} ⊕ B) ∩ A^c | Fill regions |
| **Connected components** | X_k = (X_{k-1} ⊕ B) ∩ A | Label regions |
| **Convex hull** | Iterative dilation with corner SEs | Smallest convex set |
| **Thinning** | A ⊗ B = A − (A ⊛ B) | Skeletons |
| **Thickening** | A ⊙ B = A ∪ (A ⊛ B) | Reverse of thinning |
| **Skeleton** | Successive thinning | Medial axis |
| **Pruning** | Remove short branches | Clean skeleton |

├── **One-line Exam Answer:** Basic morphological algorithms — boundary extraction, hole filling, connected components, convex hull, thinning, skeleton, pruning — are all built from dilation and erosion.

---

# 🟫 BONUS — IMAGE TRANSFORMS (Supplementary)

## 📌 6.1 Discrete Fourier Transform (DFT)
├── **Definition:** The DFT decomposes a digital image into its frequency components using sinusoidal basis functions.
├── **Key Points:**
- **Forward 2D-DFT:** F(u, v) = ΣΣ f(x, y) · exp[−j2π(ux/M + vy/N)]
- **Inverse:** f(x, y) = (1/MN) ΣΣ F(u, v) · exp[+j2π(ux/M + vy/N)]
- Output is complex (magnitude + phase)
- Implemented efficiently as FFT with O(N log N) complexity
- Applications: filtering, restoration, compression
├── **One-line Exam Answer:** DFT transforms an image to the frequency domain using complex sinusoidal basis and is implemented efficiently as FFT.

---

## 📌 6.2 Discrete Cosine Transform (DCT)
├── **Definition:** The DCT decomposes an image into real-valued cosine basis functions — the foundation of JPEG and MPEG.
├── **Key Points:**
- **2D DCT (8×8 block):**
   F(u, v) = (1/4) · C(u) · C(v) · ΣΣ f(x, y) · cos[(2x+1)uπ/16] · cos[(2y+1)vπ/16]
   where C(u) = 1/√2 for u=0; 1 otherwise
- Real-valued output (vs complex DFT)
- Energy compaction — concentrates info in low-frequency coefficients
- Separable: row DCT then column DCT
- Used in JPEG, MPEG, H.26x video codecs
├── **DFT vs DCT:**

| Feature | DFT | DCT |
|---|---|---|
| Output | Complex | Real |
| Basis | Sinusoid | Cosine |
| Energy compaction | Moderate | High |
| Use | Filtering | JPEG, MPEG |

├── **One-line Exam Answer:** DCT decomposes an image into real cosine basis with strong energy compaction — foundation of JPEG and MPEG compression.

---

## 📌 6.3 Walsh-Hadamard Transform (WHT)
├── **Definition:** A transform using ±1 valued orthogonal basis functions — extremely fast as it requires no multiplications.
├── **Key Points:**
- Hadamard matrix order 2: H₂ = ½ · [[1, 1], [1, −1]]
- All basis values are +1 or −1
- No multiplication required → very fast
- Less energy compaction than DCT
- Used in fast/simple compression, early video standards
├── **One-line Exam Answer:** The Walsh-Hadamard Transform uses ±1 orthogonal basis functions for fast image decomposition without multiplications.

---

## 📌 6.4 Haar Transform
├── **Definition:** The Haar Transform is the simplest wavelet transform using rectangular basis functions — captures both spatial location and frequency.
├── **Key Points:**
- Simplest wavelet — rectangular basis
- Multi-resolution analysis capability
- Captures localized features (unlike DFT)
- O(N) fast implementation
- Foundation of JPEG 2000
├── **One-line Exam Answer:** The Haar Transform is the simplest wavelet using rectangular basis functions, supporting multi-resolution analysis used in JPEG 2000.

---

## 📌 6.5 Karhunen-Loève Transform (KLT / PCA)
├── **Definition:** The KLT decorrelates pixels by projecting them onto eigenvectors of the image covariance matrix — optimal in mean-square-error sense.
├── **Key Points (Algorithm):**
1. Compute mean **m_x** of pixel vectors
2. Compute covariance matrix **C_x**
3. Compute eigenvectors of C_x
4. Form transform matrix **A** with eigenvectors as rows
5. Transform: **y = A(x − m_x)**
6. Inverse: **x = Aᵀy + m_x**
├── **Properties:**
- Optimal MSE — best energy compaction
- Data-dependent — different basis per image
- Computationally expensive (eigen decomposition)
- Used in face recognition (Eigenfaces), compression theory
├── **KLT vs DCT:**

| Feature | KLT | DCT |
|---|---|---|
| Optimality | Optimal MSE | Near-optimal |
| Basis | Data-dependent | Fixed |
| Computation | Expensive | Fast |
| Use | Theory, PCA | Standard codecs |

├── **One-line Exam Answer:** The KL Transform (PCA) projects pixels onto eigenvectors of the covariance matrix and is optimal in MSE but data-dependent and computationally expensive.

---

# END OF SYLLABUS NOTES
