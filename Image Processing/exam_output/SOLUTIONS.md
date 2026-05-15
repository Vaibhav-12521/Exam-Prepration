# IMAGE PROCESSING – PROBLEM SET SOLUTIONS
**Course:** BCA / B.Sc(IT) | **Subject Code:** UCS6105 | **Semester:** VI

This document solves **every** question from Mid-Term Set I, Mid-Term Set II, DIT 1, DIT 2, and Problem Sets I–V.

---

## ====== MID-TERM EXAMINATION — SET I (25/03/2026, 2 hrs, 40 marks) ======

### Q1. What is a 4-neighbor of a pixel?

The **4-neighbor N₄(p)** of pixel p(x, y) is one of the four pixels directly adjacent horizontally or vertically:

- Coordinates: (x−1, y), (x+1, y), (x, y−1), (x, y+1)

```
    [N]
[W] [p] [E]
    [S]
```

4-neighbors exclude diagonal pixels. Used in 4-connectivity, region growing, and boundary algorithms.

**Exam Tip:** Always draw the + shape and label coordinates of the four neighbors.

---

### Q2. Characteristics of an edge in a digital image

An **edge** is a set of connected pixels lying on the boundary between two regions of significantly different intensity.

**Characteristics:**
- Sharp **intensity change** (high gradient magnitude)
- **Local feature** — exists in a small spatial extent
- Has a **direction** perpendicular to the gradient
- Detected by **first-derivative** (Sobel, Prewitt) or **second-derivative** (Laplacian)
- Four ideal profiles: **step, ramp, line, roof**

Edges carry critical structural information used in segmentation, recognition, and tracking.

**Exam Tip:** Mention "high gradient + direction perpendicular to gradient" + four edge profiles.

---

### Q3. What is a negative image?

A **negative image** reverses gray levels — dark becomes light and vice versa.

**Formula:** s = L − 1 − r → for 8-bit: s = 255 − r

**Example:** Input r = 100 → Output s = 155

**Application:** Enhances white/gray detail in dark backgrounds (mammograms, X-rays).

**Exam Tip:** Always write the formula + give one X-ray application example.

---

### Q4. Purpose of log transformations

The **log transformation** compresses the dynamic range of an image, mapping wide input ranges to narrower output ranges.

**Formula:** s = c · log(1 + r)

**Purposes:**
- Expands **dark pixels** so detail becomes visible
- Compresses **bright pixels** to fit display range
- Used for displaying **Fourier spectra** (very wide range)
- Mimics human eye's logarithmic perception

**Exam Tip:** Mention "compresses dynamic range" + Fourier spectrum example.

---

### Q5. Difference between histogram equalization and histogram matching

| Feature | Histogram Equalization | Histogram Matching |
|---|---|---|
| **Output** | Uniform (flat) histogram | User-specified histogram |
| **Function** | T(r) = (L−1)·cdf(r) | G⁻¹(T(r)) |
| **Flexibility** | Low (automatic) | High (designer-defined) |
| **Use case** | General contrast enhancement | Match to reference image |
| **Steps** | One CDF mapping | Two CDFs + inverse mapping |

**HE** automatically maximizes contrast; **HM** lets the user choose the target histogram shape.

**Exam Tip:** Use a clear comparison table with at least 4 rows.

---

### Q6. Effect of a low-pass filter on noise

A **low-pass filter** allows low-frequency components to pass while attenuating high frequencies.

**Effect on noise:**
- Most random noise (Gaussian, uniform) has high-frequency components
- LPF averages neighborhoods → **reduces noise**
- Side effect: **blurs edges and fine details**

**3×3 mean mask example:**
```
       1 1 1
1/9 × [1 1 1]
       1 1 1
```

**Trade-off:** More smoothing → cleaner image but more blur.

**Exam Tip:** Mention noise + edge blur trade-off + provide one 3×3 mask.

---

### Q7. Primary goal of image restoration

The primary goal of image restoration is to **recover the original image f(x, y)** from its degraded version g(x, y) using a mathematical model.

**Model:** g(x, y) = h(x, y) * f(x, y) + η(x, y)

The objective is to compute an **estimate f̂(x, y)** that minimizes the difference from f. Restoration is **objective** (model-based), unlike enhancement which is **subjective**.

**Exam Tip:** Quote the model formula + state difference from enhancement.

---

### Q8. Define the "Max filter"

The **Max filter** is a non-linear order-statistic filter that replaces each pixel with the maximum value in its neighborhood.

**Formula:** f̂(x, y) = max { g(s, t) : (s, t) ∈ S_xy }

**Best for:** Removing **pepper noise** (dark spots = 0), because the max picks brighter neighbors.

**Side effect:** Brightens the overall image.

**Exam Tip:** Pair "Max → pepper" and "Min → salt" together.

---

### Q9. Motion blur degradation in images

**Motion blur** is degradation caused by relative motion between camera and scene during exposure — modeled as convolution with a linear PSF.

**Spatial PSF (1D linear motion length L):**
- h(x, y) = 1/L for 0 ≤ x ≤ L, y = 0; else 0

**Frequency domain (motion a, b over time T):**
- H(u, v) = (T / π(ua + vb)) · sin(π(ua + vb)) · exp(−jπ(ua + vb))

**Parameters:** length L, angle θ, exposure T

**Causes:** camera shake, object motion, long exposure

**Restoration:** inverse / Wiener filtering with known PSF

**Exam Tip:** Mention parameters L, θ, T + restoration method.

---

### Q10. Two applications where image restoration is critical

1. **Astronomy** — recovering Hubble / James-Webb telescope images degraded by atmospheric turbulence and optical aberrations
2. **Medical imaging** — de-blurring CT/MRI scans and enhancing low-dose X-rays where details affect diagnosis

Other valid examples: forensics (CCTV enhancement), satellite remote sensing, microscopy (defocus blur).

**Exam Tip:** Choose medical + astronomy — universally accepted examples.

---

### Q11 (5-mark). Fundamental difference between image enhancement and image restoration with examples

**Image Enhancement** improves the **subjective appearance** of an image so it looks better. It is heuristic and based on visual perception.

**Image Restoration** is the **objective recovery** of an image from a degraded version using a mathematical model of the degradation.

**Comparison Table:**

| Feature | Image Enhancement | Image Restoration |
|---|---|---|
| **Goal** | Improve subjective appearance | Recover original from degradation |
| **Approach** | Heuristic / visual | Mathematical / objective |
| **Knowledge** | Visual preference | Degradation function H, noise η |
| **Techniques** | Histogram, sharpen, gamma | Inverse, Wiener, constrained LS |
| **Output** | "Looks better" image | "Closer to original" image |

**Enhancement example:** A dark night photo is brightened using gamma correction (γ = 0.5) for better viewing.

**Restoration example:** A satellite image blurred by motion is recovered using a Wiener filter with known PSF.

**Mathematical contrast:**
- Enhancement: g = T[f] (no model of f's origin)
- Restoration: g = h * f + η; estimate f̂ ≈ f

**Exam Tip:** Define both → comparison table → one example each.

---

### Q12 (5-mark). How noise and blurring together affect restoration; which is harder?

When an image is degraded by both blurring (H) and noise (η), restoration becomes substantially harder than either alone.

**Combined model:** g = h * f + η

**Challenges by case:**

**(a) Blurring alone:** Can be reversed with **inverse filter** F̂ = G/H — straightforward.

**(b) Noise alone:** Can be reduced by **spatial filters** (mean, median) — simple.

**(c) Both together:** Inverse filter **amplifies noise** at frequencies where |H(u, v)| is small. The reciprocal blows up and noise N(u, v) gets divided by small H, producing huge noise spikes.

**Which is harder?** → **Blurring is more difficult**, especially with noise, because:
- Naive inversion of H amplifies noise
- True H may be unknown (blind deconvolution)
- Need **regularization** (Wiener, constrained LS)
- Noise alone is local and statistical; blurring is global and structural

**Strategy with both:** Use **Wiener filter** F̂ = [|H|² / (|H|² + S_η/S_f)] · (G/H) — balances inversion against noise suppression.

**Conclusion:** Blur is harder when combined with noise because the inversion process itself amplifies the noise.

**Exam Tip:** Mention "noise amplification at zeros of H" + Wiener as solution.

---

### Q13 (5-mark). Complete image processing system end-to-end with block diagram

A complete digital image processing system traces an image from physical light source to final display.

**Block Diagram:**
```
[Energy Source]      →   [Scene / Object]    →   [Optical Lens]
       ↓                                                ↓
[Reflection / Transmission]                    [Image Sensor (CCD/CMOS)]
                                                        ↓
                                              [Analog Signal]
                                                        ↓
                                              [Sampling + Quantization
                                                (A/D Converter)]
                                                        ↓
                                              [Frame Buffer / Storage]
                                                        ↓
                                              [Image Processor (CPU/GPU)]
                                                        ↓
                                              [Image Memory / Mass Storage]
                                                        ↓
                                              [Display Device]
                                                        ↓
                                              [Hardcopy Device / Network]
```

**Component Descriptions:**

1. **Energy Source** — Provides illumination (sun, lamp, X-ray tube)
2. **Scene/Object** — Reflects or transmits energy
3. **Optical Lens** — Focuses light onto sensor
4. **Image Sensor (CCD/CMOS)** — Converts photons → electrical signal
5. **Analog Signal** — Continuous voltage from sensor
6. **A/D Converter** — Sampling + Quantization → digital image
7. **Frame Buffer** — Temporary storage
8. **Image Processor** — CPU/GPU performs filtering, enhancement, etc.
9. **Mass Storage** — HDD, SSD, cloud
10. **Display Device** — Monitor, projector
11. **Hardcopy Device** — Printer
12. **Network** — Transmit to remote systems

**Exam Tip:** Always draw the block diagram + describe each block in 1 line.

---

### Q14 (5-mark). Compare log and power-law transformations

| Feature | Log Transformation | Power-law (Gamma) |
|---|---|---|
| **Formula** | s = c · log(1 + r) | s = c · r^γ |
| **Parameters** | c only | c and γ |
| **Behavior** | Fixed (concave curve) | Tunable via γ |
| **γ < 1 effect** | — | Brightens image |
| **γ > 1 effect** | — | Darkens image |
| **Typical use** | Fourier spectrum display | Gamma correction (CRT/LCD) |
| **Flexibility** | Low | High |
| **Reversibility** | Inverse log | Inverse power law |

**Curve shapes:**
```
Log     :  /‾‾   (sharp rise then flatten)
γ<1     :  ⌒    (similar to log, tunable)
γ=1     :  /    (identity)
γ>1     :  ⌣    (slow rise then fast)
```

**Key insight:** Power-law is more flexible (γ tunable); log is a fixed function giving strong dark expansion.

**Applications:**
- Log → display Fourier magnitude spectrum
- Power-law → calibrate monitor display (γ ≈ 2.2)

**Exam Tip:** Compare both formulas + γ < 1 vs γ > 1.

---

### Q15 (5-mark). Evaluate performance of Arithmetic Mean, Geometric Mean, Median, Contra-harmonic Mean for salt-and-pepper noise

Salt-and-pepper noise = isolated pixels with extreme values (0 or 255). Filter performance depends on how each filter handles outliers.

**(a) Arithmetic Mean Filter — ❌ Poor**
- Average over neighborhood
- Outliers (0/255) distort the average
- Result: noise is blurred but not removed; salt becomes light spots, pepper becomes dark spots

**(b) Geometric Mean Filter — ❌ Fails Catastrophically**
- (Π pixels)^(1/mn)
- Pepper pixels (value 0) make the entire product zero → outputs zero
- Result: black holes in image

**(c) Median Filter — ✅ BEST**
- Sort and take middle value
- Outliers appear at ends of sorted list and are discarded
- Result: salt-and-pepper completely removed; edges preserved
- Optimal for impulse noise

**(d) Contra-harmonic Mean Filter — ⚠ Partial**
- Q > 0 removes pepper, Q < 0 removes salt
- Single Q removes only one type, not both
- Helpful for one variety but not simultaneously

**Performance Ranking:** Median (best) → Contra-harmonic Mean → Arithmetic Mean → Geometric Mean (worst)

**Why Median wins:**
- Non-linear — outliers don't affect middle value
- Edge-preserving
- Computationally simple

**Practical recommendation:** Use Median filter (3×3 or 5×5) for salt-and-pepper noise.

**Exam Tip:** Rank filters and explain WHY each succeeds or fails.

---

## ====== MID-TERM EXAMINATION — SET II (25/10/2025, 2 hrs, 40 marks) ======

### Q1. Define 8-neighborhood

The **8-neighborhood N₈(p)** of pixel p(x, y) consists of all 8 surrounding pixels — 4 horizontal/vertical + 4 diagonal.

```
[NW] [N] [NE]
[W]  [p] [E]
[SW] [S] [SE]
```

N₈(p) = N₄(p) ∪ N_D(p). Used in 8-connectivity and morphological operations.

**Exam Tip:** Show the 3×3 matrix labeling all 8 neighbors.

---

### Q2. Concept of a path between two pixels

A **path** from pixel p(x₀, y₀) to pixel q(xₙ, yₙ) is a sequence of distinct pixels (x₀, y₀), ..., (xₙ, yₙ) where each consecutive pair is **adjacent** (4-, 8-, or m-adjacent).

**Types:** 4-path, 8-path, m-path depending on adjacency used.

If p = q, the path is **closed**.

Used in region growing, connected component labeling, distance computation.

**Exam Tip:** Mention all 3 path types + closed path concept.

---

### Q3. Spatial domain in image processing

The **spatial domain** is the image plane itself where image processing is performed by direct manipulation of pixel intensities — no transform involved.

**General form:** g(x, y) = T[f(x, y)]

T = transformation operator (point operation or mask operation).

**Examples:** histogram equalization, convolution, gamma correction.

**Exam Tip:** State formula g(x,y) = T[f(x,y)] + give one example.

---

### Q4. Power-law (gamma) transformations

**Power-law transformation** maps input r to output s using **s = c · r^γ**.

**Behavior:**
- γ < 1 → brightens image (boost shadows)
- γ > 1 → darkens image (compress shadows)
- γ = 1 → identity

**Application:** Gamma correction for displays (CRT γ ≈ 2.2; capture pre-applies γ ≈ 1/2.2 ≈ 0.45).

**Exam Tip:** Always give γ<1 vs γ>1 effects + display correction.

---

### Q5. Define a low-pass filter in the spatial domain

A **spatial-domain low-pass filter** is a smoothing mask that passes low frequencies and attenuates high frequencies (noise + edges).

**Example 3×3 mean mask:**
```
       1 1 1
1/9 × [1 1 1]
       1 1 1
```

Each output pixel = average of neighborhood → blur + denoise.

**Exam Tip:** Mention "averages neighborhood → blur + denoise."

---

### Q6. Effect of high-pass filter on edges

A **high-pass filter** enhances edges by emphasizing high-frequency content (rapid intensity changes).

**Effect:**
- Edges become **brighter and more pronounced**
- Smooth regions become **suppressed**
- Output contains mostly edge structure

**Laplacian mask example:**
```
 0 -1  0
-1  4 -1
 0 -1  0
```

Used in edge detection (Sobel, Prewitt, Laplacian).

**Exam Tip:** Mention "enhance edges, suppress smooth" + one mask.

---

### Q7. Difference between image enhancement and image restoration

| Feature | Enhancement | Restoration |
|---|---|---|
| **Goal** | Improve appearance | Recover original |
| **Approach** | Subjective | Objective (model-based) |
| **Knowledge** | Visual heuristic | Degradation model |
| **Examples** | Histogram eq., gamma | Inverse / Wiener filter |

Enhancement makes the image look better; restoration mathematically reverses a known degradation.

**Exam Tip:** Mention "subjective vs objective" + one example each.

---

### Q8. Explain the "Min filter"

The **Min filter** is an order-statistic filter that replaces each pixel with the minimum of its neighborhood.

**Formula:** f̂(x, y) = min { g(s, t) : (s, t) ∈ S_xy }

**Best for:** Removing salt noise (bright spots = 255), as salt is the maximum and gets replaced by smaller neighbors.

**Side effect:** Darkens the overall image.

**Exam Tip:** Pair "Min → salt, Max → pepper."

---

### Q9. "Blurring" as a form of degradation

**Blurring** reduces image sharpness — caused by:
- Defocus (lens focused wrong)
- Motion (camera or object movement)
- Atmospheric turbulence
- Optical aberrations

**Model:** g(x, y) = h(x, y) * f(x, y) — convolution with PSF h.

In frequency domain, blurring attenuates high frequencies (loss of fine detail).

**Exam Tip:** Mention "convolution with PSF" + 2 causes.

---

### Q10. Define restoration in the presence of noise only

Restoration **in the presence of noise only** means the degradation function H is identity — only additive noise affects the image.

**Model:** g(x, y) = f(x, y) + η(x, y)

**Approach:** Use **spatial-domain filters** (mean, median, geometric mean) chosen based on noise PDF:
- Gaussian → Mean filter
- Salt-and-pepper → Median filter
- Salt only → Min filter
- Pepper only → Max filter

**Exam Tip:** Quote model + filter–noise mapping.

---

### Q11 (5-mark). General model of image degradation/restoration with block diagram

**Spatial domain:** g(x, y) = h(x, y) * f(x, y) + η(x, y)
**Frequency domain:** G(u, v) = H(u, v) · F(u, v) + N(u, v)

**Block Diagram:**
```
                      η(x, y)  noise
                          ↓
   f(x, y) →  [ H ] → ⊕ → g(x, y) → [Restoration Filter] → f̂(x, y)
```

**Components:**
- f(x, y) — original (unknown) image
- H — degradation function (PSF)
- η — additive noise
- g — observed degraded image
- f̂ — estimate of original

**Assumptions:**
- H is linear and position-invariant (LSI)
- Noise is independent of signal
- H and noise statistics may be known (non-blind) or unknown (blind)

**Restoration approaches:**

| Filter | Knowledge Needed | Behavior |
|---|---|---|
| **Inverse** | H | Simple division G/H; amplifies noise |
| **Pseudo-inverse** | H | Threshold limit to avoid blow-up |
| **Wiener** | H + S_η + S_f | Optimal MSE |
| **Constrained LS** | H + smoothness | Robust |

**Goal:** Minimize ‖f − f̂‖.

**Exam Tip:** Draw the block diagram + state both spatial and frequency formulas.

---

### Q12 (5-mark). Why restoring both blur and noise is harder

Three compounding issues:

**(a) Noise amplification at zeros of H** — Inverse filter F̂ = G/H = F + N/H; when |H(u,v)| is small (high frequencies where blur dominates), N/H explodes.

**(b) Trade-off between sharpness and noise** — Aggressive deblurring amplifies noise; conservative deblurring leaves blur. Need regularization.

**(c) Frequency content overlap** — Both noise (high freq) and signal high-frequency content reside in the same band; can't simply low-pass filter.

**Wiener solution:** F̂ = [H* / (|H|² + NSR)] · G
- When NSR → 0 (no noise), Wiener → inverse filter
- When NSR large (high noise), Wiener becomes attenuating

**Why harder:**
- Need TWO pieces of info: H AND noise statistics
- Regularization parameter must be tuned
- Blind cases (unknown H) require iterative methods

**Exam Tip:** Mention "noise amplification + tradeoff + Wiener solution."

---

### Q13 (5-mark). Image formation model with diagram

**Block Diagram:**
```
[Illumination Source]
       ↓ (light rays)
[3D Scene / Object Surface]
       ↓ (reflected / transmitted light)
[Optical System (Lens)]
       ↓ (focused light)
[Image Sensor (2D Plane)]
       ↓ (sampled + quantized)
[Digital Image f(x, y)]
```

**Components:**
1. **Illumination Source** — provides electromagnetic energy (i(x, y), 0 < i < ∞)
2. **3D Scene** — reflects energy based on surface property r(x, y), 0 ≤ r ≤ 1
3. **Image Formation Equation:** f(x, y) = i(x, y) · r(x, y)
4. **Range Constraint:** L_min ≤ f(x, y) ≤ L_max
5. **Optical System** — focuses 3D scene onto 2D sensor (projection)
6. **Image Sensor** — CCD/CMOS converts photons to digital values

**Examples of reflectance:**

| Surface | r |
|---|---|
| Black velvet | 0.01 |
| Stainless steel | 0.65 |
| White wall | 0.80 |
| Snow | 0.93 |

**Exam Tip:** Use f = i × r formula + range constraint + reflectance table.

---

### Q14 (5-mark). Point vs Local vs Global processing

| Type | Scope | Examples |
|---|---|---|
| **Point processing** | 1 pixel → 1 pixel | Negative, gamma, threshold |
| **Local (mask) processing** | Neighborhood → 1 pixel | Mean filter, Sobel, Laplacian |
| **Global processing** | Whole image → 1 pixel / whole | Histogram equalization, FFT, image statistics |

**Point Processing:**
- Output depends only on input pixel at same location
- Formula: s = T(r)
- Examples: Negative (s=255−r), Gamma (s=cr^γ), Threshold (s=0 or L−1)
- Fastest; per-pixel parallelizable

**Local (Mask) Processing:**
- Output depends on a neighborhood of input pixels
- Formula: g(x, y) = ΣΣ w(s, t) · f(x+s, y+t)
- Examples: Mean filter (3×3 box), Sobel, Median
- Mask defines effect

**Global Processing:**
- Output uses information from all pixels
- Examples: Histogram equalization (CDF computed globally), Fourier transform, image statistics
- Computationally heavier

**Exam Tip:** Provide clear table + 1 example per category.

---

### Q15 (5-mark). Atmospheric turbulence blur restoration

**Atmospheric Turbulence Blur** occurs in long-exposure ground-based astronomical imaging when light passes through Earth's turbulent atmosphere.

**Degradation Model:**
- Spatial: g(x, y) = h(x, y) * f(x, y) + η(x, y)
- Frequency: H(u, v) = exp[−k · (u² + v²)^(5/6)] where k = turbulence severity

**Properties of Turbulence PSF:**
- Radially symmetric (depends only on √(u²+v²))
- High frequencies attenuated more
- Worse with longer exposure

**Restoration Pipeline:**
```
Degraded g(x, y) → Estimate H(u, v) using k → Estimate noise S_η →
Apply Wiener filter → Inverse FFT → Restored f̂(x, y)
```

**Why Wiener is best:**
- Atmospheric blur is strong at high frequencies — naive inverse blows up
- Wiener automatically weights between inversion and attenuation via NSR
- Atmospheric models give H; noise variance can be estimated

**Alternatives:**
- Lucky imaging — keep sharp frames
- Adaptive optics — physical correction
- Speckle imaging — combine short exposures
- Blind deconvolution — when H unknown

**Conclusion:** H(u, v) = exp[−k(u²+v²)^(5/6)] is the model; Wiener filter is the most effective restoration.

**Exam Tip:** Quote the H(u,v) formula + recommend Wiener.

---

## ====== DEPARTMENTAL INTERNAL TEST — DIT 1 (Set II) — 17/02/2026 ======

### Q1. What is image processing?

**Image processing** is the manipulation of a digital image f(x, y) using computer algorithms for enhancement, restoration, analysis, compression, or interpretation.

Three levels:
- **Low-level** (preprocessing): smooth, sharpen
- **Mid-level** (segmentation, classification)
- **High-level** (interpretation, cognition)

Used in medical, remote sensing, robotics, security.

---

### Q2. Define image quantization

**Image quantization** is the discretization of intensity values of an image — converting continuous brightness into a finite set of discrete gray levels.

- For k-bit quantization: **L = 2^k levels** (e.g., 8-bit → 256)
- Too few levels → **false contouring**

**Exam Tip:** Always state L = 2^k.

---

### Q3. Explain digital image with example

A **digital image** is a 2D matrix f(x, y) where:
- (x, y) = discrete spatial coordinates
- f(x, y) = discrete gray-level value

**Example 3×3 image:**
```
f = [ 100  120  150 ]
    [ 110  130  160 ]
    [  90  140  170 ]
```

At position (2, 3), f = 160. Digital images are produced via sampling + quantization from continuous images.

---

### Q4. What is image sensor?

An **image sensor** is a hardware device that converts incident photons (light) into an electrical signal corresponding to scene brightness.

**Types:**
- **CCD (Charge-Coupled Device)** — high quality, more expensive
- **CMOS (Complementary Metal-Oxide Semiconductor)** — cheaper, low-power, mobile
- Specialized: X-ray, IR, UV sensors

Each photosite = 1 pixel; output digitized via A/D converter.

---

### Q5. What does f(x, y) represent in a digital image?

**f(x, y)** is the 2D image function where:
- **x, y** = spatial coordinates (row, column) — pixel position
- **f** = intensity / gray-level value at that position

For 8-bit gray image: 0 ≤ f(x, y) ≤ 255
For color image: f(x, y) = (R, G, B)

---

### Q6. What is reflectance?

**Reflectance r(x, y)** is the fraction of illumination reflected by an object's surface at point (x, y).

- Range: 0 ≤ r(x, y) ≤ 1
- r = 0 → total absorption (black)
- r = 1 → total reflection (snow, polished silver)
- Used in image formation: f(x, y) = i(x, y) · r(x, y)

---

### Q7. Effect of low sampling rate

A **low sampling rate** causes:
- **Aliasing** — high frequencies fold into low → false patterns / moiré
- **Pixelation** — blocky / staircase appearance
- **Loss of fine detail** — small structures disappear
- **Reduced spatial resolution** — blurry image

To avoid: sample at ≥ 2 × highest frequency (**Nyquist criterion**).

**Exam Tip:** Always mention Nyquist + aliasing.

---

### Q8 (5-mark). Components of a digital image processing system

A DIP system has 8 components:

1. **Image Sensors** — capture light (CCD, CMOS, X-ray)
2. **Specialized Hardware** — frame grabber, ALU, GPU
3. **Computer (Host)** — general-purpose PC
4. **Image Processing Software** — MATLAB, OpenCV, ImageJ
5. **Mass Storage** — RAM (short-term), HDD (online), tape/cloud (archival)
6. **Image Display** — Monitor, LCD/LED, projector
7. **Hardcopy Device** — printer, plotter
8. **Network** — transmit images

**Block Diagram:**
```
[Image Sensor]→[Specialized HW]→[Computer]→[DIP Software]
                                              ↓
[Mass Storage]←→[Display]←→[Hardcopy]←→[Network]
```

Knowledge base spans all components, providing domain expertise.

**Exam Tip:** Draw block diagram + describe each block in 1-2 lines.

---

### Q9 (5-mark). Compare sampling and quantization with examples

**Comparison Table:**

| Feature | Sampling | Quantization |
|---|---|---|
| **Acts on** | Spatial coords (x, y) | Intensity amplitude f |
| **Determines** | Spatial resolution | Intensity (gray-level) resolution |
| **Parameter** | M × N | L = 2^k levels |
| **Low-value problem** | Aliasing, pixelation | False contouring |
| **High-value benefit** | More detail | Smoother gradients |

**Examples:**

**Sampling example:** A photo sampled at 1024×1024 vs 64×64 — the high-res shows fine textures; the low one looks blocky.

**Quantization example:** A face image with 256 gray levels looks smooth; the same with 4 levels shows visible bands (false contouring).

**Storage impact:** 512×512 8-bit image = 256 KB; 4-bit version ≈ 128 KB.

**Conclusion:** Sampling → spatial dimension; Quantization → amplitude dimension; both required for a digital image.

**Exam Tip:** Use clear table + 1 numerical example each.

---

## ====== DEPARTMENTAL INTERNAL TEST — DIT 2 (Set I) — 21/04/2026 ======

### Q1. Define image compression

**Image compression** is the process of reducing the data size required to store or transmit an image — exploiting redundancies in the data.

Two types:
- **Lossless** — exact recovery (PNG, GIF)
- **Lossy** — approximate, higher CR (JPEG, MPEG)

---

### Q2. What does HSI stand for?

**HSI** stands for **Hue, Saturation, Intensity** — a perceptual color model:
- **Hue** — dominant wavelength (color type)
- **Saturation** — purity of color
- **Intensity** — brightness

Decouples color from brightness → useful for image processing.

---

### Q3. Explain lossy compression

**Lossy compression** reduces image data size by discarding information not perceptually significant — original cannot be exactly recovered.

**Trade-off:** Higher CR (10:1–100:1) at cost of some quality.

**Examples:** JPEG, MPEG, WebP, MP3 (audio).
**Techniques:** DCT + quantization, wavelet, vector quantization.

---

### Q4. Explain closing operation

**Closing** is a morphological operation: dilation followed by erosion.

**Formula:** A • B = (A ⊕ B) ⊖ B

**Effects:**
- Fills small holes in objects
- Connects nearby objects
- Smooths concave contours
- Preserves overall shape

Useful in OCR (fill character gaps), noise removal (pepper noise).

---

### Q5. Define boundary extraction in morphological processing

**Boundary extraction** finds the edge pixels of objects in a binary image:

**Formula:** β(A) = A − (A ⊖ B)

- Erode A by SE B → object shrinks
- Subtract from original → only boundary pixels remain
- Boundary thickness = (size of SE − 1) / 2

---

### Q6. Primary and secondary colors of light

**Primary colors of light (additive):**
- **Red, Green, Blue (RGB)** — combine to form white

**Secondary colors (mixtures of two primaries):**
- **Cyan = G + B**
- **Magenta = R + B**
- **Yellow = R + G**

Adding all three → white; adding none → black.

Used in monitors, cameras, image sensors.

---

### Q7. Need for image compression in modern digital systems

- **Storage** — Modern devices store thousands of images
- **Bandwidth** — Internet transmission is bandwidth-limited
- **Streaming** — Real-time video delivery
- **Cost** — Storage and transmission cost money
- **User experience** — Faster downloads, less buffering

Without compression, 4K raw images (~25 MB) would be impractical for web; with JPEG → ~2 MB.

---

### Q8 (5-mark). Mathematical relationship between RGB and HSI

**RGB → HSI Conversion:**
```
I = (R + G + B) / 3
S = 1 − [ 3 · min(R, G, B) / (R + G + B) ]
θ = arccos { [½((R−G) + (R−B))] / √((R−G)² + (R−B)(G−B)) }
H = θ        if B ≤ G
H = 360 − θ  if B > G
```

**HSI → RGB** (three sectors based on H):

**Sector RG (0° ≤ H < 120°):**
- B = I · (1 − S)
- R = I · [1 + (S · cos H) / cos(60 − H)]
- G = 3I − (R + B)

**Sector GB (120° ≤ H < 240°):** H' = H − 120, similar formulas
**Sector BR (240° ≤ H < 360°):** H' = H − 240, similar formulas

**Challenges near saturation axis:**
- **Hue undefined when S = 0** (pure gray)
- **Numerical instability near S = 0**
- **Out-of-gamut** after computation (clip to [0, 1])
- **Sector boundary errors** at 0°, 120°, 240°

**Solutions:** Use double precision, add ε tolerance, clamp output.

**Exam Tip:** Write all conversion formulas + 3 numerical issues.

---

### Q9 (5-mark). Explain closing operation in detail

**Closing A • B = (A ⊕ B) ⊖ B** is dilation followed by erosion.

**Step-by-step example (3×3 SE):**
```
Original A:        After Dilation (A ⊕ B):
1 0 1              1 1 1
0 0 0              1 1 1
1 0 1              1 1 1

After Erosion = A • B
1 1 1
1 1 1   (Small holes filled)
1 1 1
```

**Properties:**
- **Extensive:** A ⊆ A • B
- **Idempotent:** (A • B) • B = A • B
- **Increasing**
- **Translation-invariant**

**Effects:**
- Fills small holes (smaller than SE)
- Connects nearby objects (gaps smaller than SE)
- Smooths concave contours
- Removes pepper noise (dark spots inside objects)

**Applications:**
1. **OCR** — connect broken character strokes
2. **Medical imaging** — fill small holes in tissue segmentation
3. **Industrial inspection** — fill voids in product images
4. **Satellite imagery** — connect fragments of land features
5. **Noise removal** — remove pepper-like noise

**Opening vs Closing:**

| Feature | Opening | Closing |
|---|---|---|
| Sequence | Erode → Dilate | Dilate → Erode |
| Removes | Small bright objects | Small dark holes |
| Effect | Smooth outside | Smooth inside |

**Exam Tip:** Define formula + show step-by-step example + list 4+ applications.

---

## ====== PROBLEM SET I — UNIT I ======

### Q1. f(4, 6) = 180 — what does this mean?

**Identification:**
- Coordinates (x, y) = (4, 6) → pixel at row 4, column 6
- f(4, 6) = 180 → intensity at that pixel

**Interpretation:**
For an 8-bit grayscale image (range 0–255):
- 0 = black
- 255 = white
- **180 = light gray** (~70% of max)

Percentage = 180/255 ≈ 70.6%

The pixel has a brightness of 180 out of 255 — a fairly bright gray pixel.

**Exam Tip:** Always state range (0–255), interpret as percentage.

---

### Q2. Effect of very low sampling rate

**Problem:** Aliasing (along with pixelation and loss of detail).

**Justification (Nyquist theorem):** Sampling frequency must be ≥ 2× highest frequency in the image.

If violated:
- **Aliasing** — high frequencies fold back into low → false patterns, moiré
- **Pixelation** — blocky look
- **Loss of fine detail** — small structures unrecognizable
- **Reduced spatial resolution** — blurry image

**Visual effect with decreasing sampling rate:**
- 512×512 → clear
- 128×128 → slight blur
- 64×64 → visible pixelation
- 32×32 → severe aliasing

**Solution:** Increase sampling rate or apply anti-aliasing filter before sampling.

**Exam Tip:** Always cite Nyquist theorem + aliasing.

---

### Q3. Sampling vs Quantization for resolution

| Feature | Sampling | Quantization |
|---|---|---|
| **(a) Spatial resolution** | ✅ Affects | ✗ Does not |
| **(b) Intensity resolution** | ✗ Does not | ✅ Affects |
| **Parameter** | M × N | L = 2^k |
| **Low-value problem** | Aliasing | False contouring |

**(a) Spatial resolution** = smallest discernible spatial detail; determined by **sampling**.
**(b) Intensity resolution** = smallest discernible intensity change; determined by **quantization**.

**Examples:**
- 256×256 with 256 gray levels → moderate spatial, full intensity
- 1024×1024 with 4 levels → high spatial, poor intensity
- 64×64 with 256 levels → low spatial, good intensity

**Exam Tip:** Match sampling↔spatial, quantization↔intensity.

---

### Q4. Satellite image blurred despite high-resolution sensors

Model: g(x, y) = h(x, y) * f(x, y) + η(x, y)

**Possible Responsible Stages:**

1. **Atmospheric turbulence** — H(u,v) = exp[−k(u²+v²)^(5/6)] — most common
2. **Motion blur** — satellite movement during exposure
3. **Defocus / optical aberrations** — imperfect lens
4. **Sensor response** — finite pixel area integration
5. **Compression artifacts** — JPEG block artifacts
6. **Resampling** — geometric correction

**Most likely culprit:** Atmospheric turbulence + motion blur during long exposure.

**Solutions:**
- Pre-launch: better optics, adaptive optics
- Post-processing: Wiener filter, blind deconvolution, deep-learning deblurring

**Exam Tip:** List all stages systematically and rank likelihood.

---

### Q5. Convert continuous image to digital step-by-step

**Step 1 — Continuous Image f_c(x, y)** — captured by sensor with continuous coords/amplitude.

**Step 2 — Sampling** (discretize coordinates):
- Grid with spacing (Δx, Δy)
- f(m, n) = f_c(m·Δx, n·Δy) for m = 0..M-1, n = 0..N-1
- Determines spatial resolution

**Step 3 — Quantization** (discretize amplitude):
- Map continuous intensity to L = 2^k discrete levels
- f_q = round((f / max) × (L − 1))
- Determines intensity resolution

**Step 4 — Storage** as 2D matrix:
- Total bits = M · N · k

**Step 5 — Output Digital Image f(x, y)** — fully discrete; ready for processing.

**Pipeline:**
```
Continuous Image → Sampling (discretize x, y) →
   Quantization (discretize f) → Digital Matrix f(m, n)
```

**Example:** 8.5×11 inch image at 300 DPI = 2550×3300 pixels; 8-bit gray → ~8.4 MB.

**Exam Tip:** Always explain "sampling = spatial, quantization = amplitude."

---

### Q6. 4-connectivity vs 8-connectivity (pixel with diagonal + horizontal neighbors)

The pixel has neighbors in both horizontal/vertical AND diagonal directions:
- Horizontal/vertical → 4 neighbors (N₄)
- Diagonal → 4 neighbors (N_D)
- **Combined → 8 neighbors total**

**Verdict:** **8-connectivity (N₈)**

```
[NW] [N] [NE]
[W]  [p] [E]
[SW] [S] [SE]
```

- **4-connectivity** uses only horizontal + vertical (4 neighbors, + pattern)
- **8-connectivity** adds diagonals (8 neighbors, square pattern)
- **m-connectivity** refines 8-connectivity to eliminate path ambiguity

**Exam Tip:** Count neighbors → if 8 → 8-connectivity.

---

### Q7. Why low quantization causes false contouring; how to reduce

**Why it occurs:**
- Smooth intensity changes require many gray levels to look continuous
- With few quantization levels (e.g., 4), adjacent areas get same value
- Where different regions get different quantized values, a visible boundary (ridge) appears
- Human eye is highly sensitive to these artificial edges

**Visual Example:**

| Original | 0 | 50 | 100 | 150 | 200 | 255 |
|---|---|---|---|---|---|---|
| 8-bit (256 lv) | 0 | 50 | 100 | 150 | 200 | 255 |
| 4-bit (16 lv) | 0 | 48 | 96 | 144 | 192 | 240 |
| 2-bit (4 lv) | 0 | 0 | 85 | 170 | 170 | 255 |

**How to reduce:**
1. **Increase quantization levels** (move from 4-bit to 8-bit)
2. **Dithering** — add random noise before quantization
3. **Error diffusion (Floyd-Steinberg)** — propagate error to neighbors
4. **Halftoning** — pattern of dots
5. **Companding** — non-uniform quantization

**Exam Tip:** Show "few levels → ridges" + dithering as solution.

---

### Q8. Image formation model — illumination + reflectance forming pixel intensity

**Formula:** f(x, y) = i(x, y) × r(x, y)

**Components:**
- **i(x, y)** — illumination from source (0 < i < ∞)
- **r(x, y)** — reflectance of surface (0 ≤ r ≤ 1)

**How they combine:**
- Bright light + reflective surface → bright pixel
- Bright light + dark surface → medium pixel
- Dim light + reflective surface → medium pixel
- Dim light + dark surface → dark pixel

**Examples:**

| Scene | i (lm/m²) | r | f = i × r |
|---|---|---|---|
| Snow in sunlight | 90,000 | 0.93 | 83,700 |
| Black coal in sunlight | 90,000 | 0.01 | 900 |
| White wall in office | 1,000 | 0.80 | 800 |
| Black wall in office | 1,000 | 0.05 | 50 |

**Range:** L_min = i_min · r_min ≤ f ≤ L_max = i_max · r_max — after mapping to 0–255, this becomes the gray scale.

**Conclusion:** The model cleanly separates the physics of light (illumination) from the physics of surface (reflectance).

**Exam Tip:** State formula + give range + 1 numerical example.

---

### Q9. Image with dark histogram — analyze and suggest enhancement

**Analysis:**
- Most pixels are 0–80 → image is dark / under-exposed
- **Low contrast** — narrow intensity range
- Details in bright regions barely visible
- Image looks dim or shadowy

**Suggested Technique:** **Histogram Equalization**

**Reason:**
- Automatically redistributes pixels across full intensity range
- Stretches the narrow dark histogram into uniform distribution
- Increases contrast without manual tuning
- Formula: s_k = (L − 1) · cdf(r_k)

**Alternatives:**
- **Power-law (Gamma) with γ < 1** — specifically brightens dark regions
- **Log transformation** — s = c · log(1 + r) for very wide ranges
- **Linear contrast stretching** — map [r_min, r_max] linearly to [0, 255]

**Best choice:** Histogram equalization for general under-exposed images.

**Exam Tip:** State problem + suggest HE + provide formula.

---

### Q10. Meaning of x, y, f(x, y)

- **x** = horizontal coordinate (column index in image matrix); discrete integer 0 ≤ x ≤ M−1
- **y** = vertical coordinate (row index); discrete integer 0 ≤ y ≤ N−1
- **f(x, y)** = intensity (gray-level) at pixel (x, y); for 8-bit, 0 ≤ f ≤ 255

For color image, f(x, y) = (R, G, B).

**Example:** f(2, 3) = 150 means at row 2, column 3, pixel has gray level 150.

**Exam Tip:** Give all 3 meanings + example f(2, 3) = 150.

---

## ====== PROBLEM SET II — UNIT II ======

### Q1. "Spatial domain" in image processing

The **spatial domain** is the image plane itself where image processing is done by direct manipulation of pixel intensities.

**General form:** g(x, y) = T[f(x, y)]

T = transformation operator — point operation (single pixel) or mask operation (neighborhood).

**Categories:**
- Point processing: Negative, gamma, threshold
- Mask processing: Mean filter, median, Sobel, Laplacian
- Global ops: Histogram equalization, image stats

**Contrast with frequency domain:** Frequency-domain processing transforms image via DFT, multiplies in Fourier space, then inverts.

**Advantages of spatial domain:** Fast for small kernels, simpler to understand, direct pixel control.

---

### Q2. Histogram equalization vs histogram matching goals

| Feature | Histogram Equalization | Histogram Matching |
|---|---|---|
| **Goal** | Maximize global contrast | Produce specified histogram |
| **Output histogram** | Uniform (flat) | User-defined shape |
| **Function** | T(r) = (L−1)·cdf(r) | G⁻¹(T(r)) |
| **User control** | None (automatic) | Full (specify target) |
| **Flexibility** | Low | High |
| **Use case** | General enhancement | Match reference image |

HE always produces a uniform output; HM allows the user to choose any target distribution (useful when uniform isn't ideal, e.g., medical images often need bimodal contrast).

---

### Q3. Negative of grayscale image — math expression

**Formula:** s = L − 1 − r

Where:
- L = number of gray levels (e.g., 256 for 8-bit)
- r = input pixel intensity
- s = output pixel intensity

For 8-bit: **s = 255 − r**

**Examples:**

| r | s = 255 − r |
|---|---|
| 0 | 255 |
| 100 | 155 |
| 128 | 127 |
| 200 | 55 |
| 255 | 0 |

**Application:** Enhancing white details on dark backgrounds (X-rays).

---

### Q4. Histogram equalization step-by-step + justify contrast enhancement

**Algorithm:**

1. Compute histogram: h(r_k) = n_k
2. Normalize: p_r(r_k) = n_k / MN
3. Compute CDF: cdf(r_k) = Σ_{j=0..k} p_r(r_j)
4. Map pixels: s_k = round((L − 1) · cdf(r_k))
5. Replace each pixel.

**Numerical Example (3-bit, 64 pixels):**

| r_k | n_k | p | cdf | (L-1)·cdf | s_k |
|---|---|---|---|---|---|
| 0 | 8 | 0.125 | 0.125 | 0.875 | 1 |
| 1 | 10 | 0.156 | 0.281 | 1.97 | 2 |
| 2 | 10 | 0.156 | 0.437 | 3.06 | 3 |
| 3 | 2 | 0.031 | 0.469 | 3.28 | 3 |
| 4 | 12 | 0.187 | 0.656 | 4.59 | 5 |
| 5 | 16 | 0.250 | 0.906 | 6.34 | 6 |
| 6 | 4 | 0.063 | 0.969 | 6.78 | 7 |
| 7 | 2 | 0.031 | 1.000 | 7.00 | 7 |

**Justification — How HE Enhances Contrast:**
- Stretches narrow histograms across full range
- Maps frequent gray levels to wider output range
- Compresses rare gray levels
- Final output approx uniform → maximum global contrast

**Limitations:**
- May enhance noise
- May produce unnatural look
- Local features can be lost

---

### Q5. Smoothing vs sharpening filters

| Feature | Smoothing | Sharpening |
|---|---|---|
| **Frequency response** | Low-pass | High-pass |
| **Effect** | Blurs, reduces noise | Enhances edges, fine details |
| **Math basis** | Average / weighted sum | Derivatives (1st, 2nd order) |
| **Typical kernels** | Mean, Gaussian, median | Sobel, Prewitt, Laplacian |
| **Edge effect** | Blurred | Enhanced |
| **Noise effect** | Reduces | Amplifies |
| **Use** | Pre-processing, denoise | Edge detection, feature extraction |

**Objectives:**

**Smoothing:** Reduce noise, remove fine details, pre-process for segmentation, produce uniform regions.
**Sharpening:** Enhance edges, highlight fine structures, feature extraction, OCR pre-processing.

**Example Kernels:**
```
3×3 Mean (smooth):       Laplacian (sharpen):
       1 1 1               0 -1  0
1/9 × [1 1 1]             -1  4 -1
       1 1 1               0 -1  0
```

---

### Q6. Arithmetic operations — applications in noise reduction, motion detection, masking

**Addition (s = f + g):**
- **Noise reduction by averaging:** ḡ = (1/K) Σ g_i → variance reduces by 1/K
- Long-exposure simulation
- Double exposure (artistic)

**Subtraction (s = f − g):**
- **Motion detection** — subtract consecutive frames; moving objects appear
- **Background subtraction** — remove static background
- **Digital Subtraction Angiography (DSA)** — subtract pre/post contrast medical images

**Multiplication (s = f × g):**
- **Masking** — binary mask × image to extract ROI
- **Shading correction** — multiply by inverse illumination pattern
- **Watermarking**

**Division (s = f / g):**
- **Shading correction** — divide image by illumination pattern
- **Flat-field correction** in microscopy
- **Calibration** — normalize against reference

---

### Q7. Logical operations — truth tables + 3×3 examples + applications

**Truth Table:**

| p | q | AND | OR | XOR | NAND | NOR |
|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |

**Example 3×3 matrices:**
```
A = 1 0 1     B = 1 1 0
    0 1 0         0 1 1
    1 1 0         1 0 0
```

**AND:** ROI extraction, intersection
```
1 0 0
0 1 0
1 0 0
```

**OR:** Region union
```
1 1 1
0 1 1
1 1 0
```

**NOT(A):** Complement
```
0 1 0
1 0 1
0 0 1
```

**XOR:** Change detection
```
0 1 1
0 0 1
0 1 0
```

**Applications:**
- AND → masking, intersection
- OR → region union
- NOT → complement
- XOR → change detection
- NAND/NOR → logic completeness

---

### Q8. Hospital MRI: contrast stretch + HE + noise reduction — details lost — analyze

**Analysis:** HE automatically maximizes global contrast but can lose subtle local details — critical issue for medical imaging.

**Advantages of HE in Medical Images:**
1. Automatic — no parameters
2. Global contrast enhancement
3. Computationally cheap
4. Reproducible
5. Easy to implement

**Disadvantages of HE in Medical Images:**
1. **Over-enhancement of noise** — random noise amplified
2. **Loss of subtle details** — small intensity differences (tumors, micro-calcifications) merged
3. **Unrealistic appearance**
4. **Global approach** — doesn't adapt locally
5. **Saturation** — bright/dark may saturate
6. **Sensitive to outliers**

**Suggested Improvements:**

1. **CLAHE (Contrast-Limited Adaptive Histogram Equalization)** — applies HE on small tiles with clipping; gold standard for medical
2. **AHE (Adaptive HE)** — local HE on sliding windows
3. **Histogram Matching** to a reference good image
4. **Gamma Correction** — specific γ for ROI
5. **Wavelet-based enhancement** — preserves details at all scales
6. **Denoising before HE** — non-local means or BM3D

**Recommended:** CLAHE + denoise pre-processing.

---

### Q9. Compare 4 noise removal filters (Arithmetic, Geometric, Median, Gaussian)

| Feature | Arithmetic Mean | Geometric Mean | Median | Gaussian |
|---|---|---|---|---|
| **Formula** | (1/mn)·Σg | (Πg)^(1/mn) | median{g} | weighted avg |
| **Linearity** | Linear | Non-linear | Non-linear | Linear |
| **Best for** | Gaussian, uniform | Gaussian (less blur) | Salt-and-pepper | Gaussian |
| **Edge effect** | Strong blur | Less blur | Preserves | Mild blur |
| **Zero-pixel issue** | None | Fails | None | None |
| **Computational cost** | O(mn) | O(mn) | O(mn·log(mn)) | O(mn) |

**Quick recommendation:**

| Noise Type | Best Filter |
|---|---|
| Salt-and-pepper | Median |
| Gaussian | Gaussian or Geometric mean |
| Uniform | Arithmetic mean |
| Mixed | Alpha-trimmed mean |

---

### Q10. Image gradient + Sobel magnitude and direction

**Image gradient ∇f** is a 2D vector representing the direction of greatest intensity change at each pixel.

**Gradient vector:**
```
∇f = [ ∂f/∂x ]
     [ ∂f/∂y ]
```

**Magnitude (edge strength):**
|∇f| = √((∂f/∂x)² + (∂f/∂y)²) ≈ |G_x| + |G_y|

**Direction (gradient angle):**
θ = arctan(G_y / G_x)

Edge direction is **perpendicular** to ∇f.

**Sobel Masks:**
```
G_x = [-1  0  1]      G_y = [-1 -2 -1]
      [-2  0  2]            [ 0  0  0]
      [-1  0  1]            [ 1  2  1]
```

**Example (3×3 patch):**
```
f = 50  60  70
    55  65  75
    60  70  80

G_x = (-50 + 70) + (-110 + 150) + (-60 + 80) = 80
G_y = (-50 - 120 - 70) + 0 + (60 + 140 + 80) = 40
|∇f| = √(80² + 40²) = √8000 ≈ 89.4
θ = arctan(40/80) = arctan(0.5) ≈ 26.6°
```

**Applications:** Edge detection (Canny uses Sobel), feature extraction, segmentation.

---

## ====== PROBLEM SET III — UNIT III ======

### Q1. Image enhancement vs restoration (with examples)

(Same as Mid-Term Set I Q11 — see above)

**Comparison Table:**

| Feature | Enhancement | Restoration |
|---|---|---|
| Goal | Subjective | Objective |
| Approach | Heuristic | Mathematical |
| Knowledge | Visual | Degradation model |
| Examples | Histogram, gamma | Inverse, Wiener |

**Enhancement example:** Brightening with γ = 0.5.
**Restoration example:** Wiener filter on motion-blurred satellite image.

---

### Q2. Min filter — which noise reduced

**Min filter:** f̂(x, y) = min { g(s, t) : (s, t) ∈ S_xy }

Replaces each pixel with smallest neighborhood value.

**Noise reduced:** **Salt noise** (bright spots = 255).

**Why?** Salt pixels are maximum. Min filter picks darker neighbors → salt removed.

**Side effects:**
- Darkens image overall
- Erodes bright objects (like morphological erosion on grayscale)

---

### Q3. Motion blur — mathematical model

(Same as Mid-Term Set I Q9 — see above)

**Spatial PSF:** h(x, y) = 1/L if 0 ≤ x ≤ L, y = 0; else 0

**Frequency:** H(u, v) = (T / π(ua + vb)) · sin(π(ua + vb)) · exp(−jπ(ua + vb))

**Parameters:** L (length), θ (angle), T (exposure time).

**Causes:** Camera shake, object motion, long exposure.

---

### Q4. Max filter — salt or pepper?

**Max filter:** f̂(x, y) = max { g(s, t) }

**Effective for:** **Pepper noise** (dark spots = 0)

**Why?** Pepper pixels are 0 (minimum). Max picks brightest neighbor → pepper replaced.

**NOT effective for salt** — salt pixels are 255 (max), Max filter preserves them.

**Side effects:** Brightens image, dilates bright regions.

---

### Q5. Prior knowledge in restoration

Without H (blind restoration): must estimate H from observed image — challenging.
With H (non-blind restoration):

1. **Enables inverse filtering:** F̂ = G/H
2. **Enables Wiener filtering** (with noise stats)
3. **Enables constrained least squares**
4. **Enables choosing filter type** (motion-specific, defocus-specific)
5. **Avoids wasted iterations** of blind methods

**Sources of prior knowledge:**
- Camera calibration data
- Atmospheric models (astronomy)
- Optical system characteristics
- Motion sensors (gyroscope readings)
- Calibration targets

**Conclusion:** Prior knowledge of H transforms restoration from blind guessing to mathematical inversion.

---

### Q6. Restoration with both blur and noise — complexity comparison

| Case | Complexity | Approach | Risk |
|---|---|---|---|
| **Noise only** | Low | Spatial filter (median) | Mild edge blur |
| **Blur only** | Low–Medium | Inverse filter | None if H known |
| **Blur + Noise** | High | Wiener / CLS | Severe noise amplification |

**Difficulties with both:**
1. **Noise amplification** — inverse filter F̂ = G/H + N/H; small |H| → N/H explodes
2. **Frequency overlap** — noise (high freq) and edge content coexist
3. **Need multiple parameters** — H, S_η, S_f, regularization
4. **Trade-off required** — aggressive deblur amplifies noise
5. **Blind cases are worst** — H unknown

**Conclusion:** Blur + noise is hardest case; needs regularized restoration (Wiener / CLS).

---

### Q7. Mathematical model for motion blur

**Spatial PSF for uniform linear motion (length L):**
h(x, y) = 1/L for 0 ≤ x ≤ L, y = 0; 0 otherwise

**Frequency domain:**
H(u, v) = (T / π(ua + vb)) · sin(π(ua + vb)) · exp(−jπ(ua + vb))

**Parameters:**
1. **Length L** — distance traversed during exposure
2. **Angle θ** — direction of motion
3. **Exposure time T** — longer T = more accumulated motion
4. **Motion type** — linear uniform, non-uniform, rotational

**Restoration:** Estimate L and θ → construct H → apply inverse / Wiener filter.

---

### Q8. Comprehensive image degradation/restoration model with block diagram

**Block Diagram:**
```
                          η(x, y) noise
                              ↓
   f(x,y) → [ H ] → ⊕ → g(x,y) → [Restoration Filter] → f̂(x,y)
```

**Components:**
- f(x, y) — original (unknown)
- H — linear, position-invariant degradation
- η(x, y) — additive noise
- g(x, y) — observed degraded image
- Restoration filter — recovery operator
- f̂(x, y) — estimate

**Mathematical Derivation:**

Step 1 — Spatial: g = h * f + η

Step 2 — Frequency (FT): G = H · F + N

Step 3 — Inverse restoration: F̂ = G/H = F + N/H (noise amplified)

Step 4 — Wiener restoration: F̂ = [|H|² / (|H|² + S_η/S_f)] · G/H

**Behavior:**
- High SNR (S_η/S_f → 0): Wiener → inverse
- Low SNR: Wiener → 0 (suppress)

**Assumptions:** LSI, additive noise, signal-independent.

---

### Q9. Inverse vs Wiener — when does Wiener become pseudo-inverse?

(Same as Unit III topic — see SYLLABUS_NOTES)

**Inverse:** F̂ = G/H (amplifies noise where |H| ≈ 0)

**Wiener:** F̂ = [H*/(|H|² + S_η/S_f)] · G

**Wiener → Pseudo-Inverse condition:** When **NSR → 0** (no noise):
F̂ = [H* / (|H|² + 0)] · G = (1/H) · G

**Pseudo-inverse filter:** Modified inverse that clips when |H| is very small:
F̂ = G/H if |H| > threshold, else 0

**Conclusion:** Wiener generalizes inverse to include noise; without noise, reduces to inverse/pseudo-inverse.

---

### Q10. Different noise types with PDFs

**Gaussian:** p(z) = (1/σ√2π) · exp(−(z − μ)² / 2σ²) — sensors/electronic
**Rayleigh:** p(z) = (2/b)(z − a) · exp(−(z − a)²/b) — range imaging
**Erlang:** p(z) = (a^b · z^(b−1) / (b−1)!) · exp(−az) — laser
**Exponential:** p(z) = a · exp(−az) — laser (special case)
**Uniform:** p(z) = 1/(b − a) for a ≤ z ≤ b — simulation
**Impulse (Salt-and-pepper):** p(z) = P_a at z=a (pepper), P_b at z=b (salt)

| Noise | Source | Best Filter |
|---|---|---|
| Gaussian | Sensor / electronic | Mean / Gaussian |
| Salt-pepper | Transmission | Median |
| Rayleigh | Range imaging | Geometric mean |
| Erlang | Laser | Geometric mean |
| Uniform | Simulation | Mean |

---

## ====== PROBLEM SET IV — UNIT IV ======

### Q1. Three color representations

1. **RGB (Red, Green, Blue)** — additive model for monitors, cameras
2. **HSI (Hue, Saturation, Intensity)** — perceptual model
3. **CMY / CMYK (Cyan, Magenta, Yellow, Key/Black)** — subtractive model for printing

Other valid: YCbCr (video, JPEG), YIQ (NTSC), Lab (perceptually uniform).

---

### Q2. Intensity component in HSI

**Intensity (I)** in HSI is the brightness component — how much gray/luminance the color has.

**Formula:** I = (R + G + B) / 3

**Range:** 0 (black) ≤ I ≤ 1 (white)

**Properties:**
- Determines overall brightness
- Independent of hue and saturation
- Plot along central axis of HSI cone

**Difference from H and S:**

| Component | Meaning | Range | Controls |
|---|---|---|---|
| Hue (H) | Dominant wavelength | 0°–360° | Color type |
| Saturation (S) | Color purity | 0 – 1 | Vividness |
| Intensity (I) | Brightness | 0 – 1 | Darkness/lightness |

---

### Q3. Define color model — primary purpose

A **color model** is a mathematical system for representing colors as numerical tuples (usually 3 or 4 components).

**Examples:** RGB, HSI, CMYK, YCbCr, Lab

**Primary Purposes:**
1. Standardization — unambiguous color specification
2. Device compatibility — RGB for monitors, CMYK for printers
3. Image storage/transmission — YCbCr for compression
4. Processing convenience — HSI for manipulation
5. Color conversion between devices
6. Color analysis (segmentation, recognition)

---

### Q4. Saturation component in HSI — relation to purity

**Saturation (S)** measures purity of color — degree to which color is diluted by white light.

**Formula:** S = 1 − [3 · min(R, G, B) / (R + G + B)]

**Range:** 0 (gray) ≤ S ≤ 1 (pure)

**Relation to purity:**
- **High S (→1):** Pure, fully saturated color
- **Low S (→0):** Diluted, mixed with white
- **S = 0:** Pure gray (no hue)

**Examples:**

| Color | R | G | B | S |
|---|---|---|---|---|
| Pure red | 1.0 | 0.0 | 0.0 | 1.0 |
| Pink | 1.0 | 0.7 | 0.7 | 0.30 |
| Light red | 1.0 | 0.5 | 0.5 | 0.50 |
| Gray | 0.5 | 0.5 | 0.5 | 0.0 |

---

### Q5. Color quantization technique

**Color quantization** reduces the number of distinct colors in an image — from millions (24-bit, 16.7M) to a small palette (e.g., 256).

**Algorithms:**
- **Uniform quantization** — equal subdivision (poor for natural images)
- **Median-cut** — recursive split of color cube
- **Octree** — tree-based subdivision
- **K-means clustering** — cluster similar colors

**Situations requiring it:**
1. GIF format (256 colors max)
2. Older 8-bit displays (VGA)
3. Limited storage (IoT)
4. Image compression
5. Vector quantization step
6. Web optimization

**Trade-off:** Smaller palette → smaller file but color banding.

---

### Q6. Importance of image compression — 2 application areas

**Importance:**
- Storage efficiency (4K raw 25 MB → JPEG 2 MB)
- Bandwidth savings
- Cost reduction
- Real-time streaming
- Mobile devices

**Application Area 1 — Web Browsing / Streaming:**
- Need: Fast image/video load for billions
- Solution: JPEG, WebP, MP4 (H.264, H.265)
- CR: 10:1 to 100:1
- Impact: Without compression, websites would load 50× slower

**Application Area 2 — Medical Imaging Archives:**
- Need: Store millions of patient scans for years
- Solution: JPEG 2000 (lossy + lossless modes)
- CR: 5:1 to 20:1 for lossless
- Impact: 80% reduction in storage costs

---

### Q7. RGB color cube — primary and secondary colors

**RGB Color Cube Visualization:**
```
        White (1, 1, 1)
        /|
       / |
   Yellow ── Cyan
    /|     /|
   / |    / |
 Red ── Magenta ── Blue
   \  |   /
    \ |  /
   Black (0, 0, 0)
```

**Primary Colors (single axis = 1):**

| Color | R | G | B |
|---|---|---|---|
| Red | 1 | 0 | 0 |
| Green | 0 | 1 | 0 |
| Blue | 0 | 0 | 1 |

**Secondary Colors (two axes = 1):**

| Color | R | G | B | Combination |
|---|---|---|---|---|
| Yellow | 1 | 1 | 0 | R + G |
| Cyan | 0 | 1 | 1 | G + B |
| Magenta | 1 | 0 | 1 | R + B |

**Extremes:** Black (0,0,0), White (1,1,1).
**Gray line:** Main diagonal from black to white (R = G = B).

24-bit RGB → 256³ = 16,777,216 distinct colors.

---

### Q8. Lossless vs Lossy compression — comparison

| Feature | Lossless | Lossy |
|---|---|---|
| **Data recovery** | Bit-exact | Approximate |
| **Quality loss** | None | Some (controlled) |
| **CR** | 2:1 to 5:1 | 10:1 to 100:1 |
| **Techniques** | Huffman, RLE, LZW, Arithmetic, DPCM | DCT, Wavelet, VQ |
| **Formats** | PNG, GIF, TIFF | JPEG, MPEG, WebP, HEIC |
| **Use cases** | Medical, legal, text | Web, video, mobile |

**Use Cases:**

| Domain | Lossless | Lossy |
|---|---|---|
| Medical imaging | ✓ Diagnosis | ✗ Loss affects diagnosis |
| Legal evidence | ✓ Court admissible | ✗ Tampering risk |
| Photographs | Optional | ✓ Smaller files |
| Video streaming | ✗ Too large | ✓ Bandwidth limited |

---

### Q9. Color constancy — modern cameras

**Color constancy** = ability to perceive consistent colors of objects despite changes in illumination.

**Modern Methods:**

1. **Auto White Balance (AWB)** — most common in cameras; estimates illumination and cancels it (Daylight, Tungsten, Fluorescent presets)
2. **Gray-World Assumption** — average of scene = gray; adjust R, G, B gains
3. **White-Patch (Retinex)** — brightest pixel in each channel = reference white
4. **Bayesian Color Constancy** — probabilistic illuminant estimation
5. **Machine Learning / Deep Learning** — modern AI cameras (Google Pixel, iPhone)
6. **Multi-illuminant Detection** — local processing for mixed lighting
7. **Color Calibration** — reference card (X-Rite ColorChecker)

**Modern Camera Pipeline:**
```
Capture → Raw → AWB → Color Correction → Color Space Conversion → Display
```

---

### Q10. Vector quantization — training, codebook, matching

**Vector Quantization (VQ)** maps groups (vectors) of pixels to a codebook of representative vectors, storing only indices.

**Pipeline:**
```
Image → Blocks → Find nearest codeword → Index → Bitstream
                                              ↓
                              Index → Codebook lookup → Reconstructed
```

**1. Training Vector Selection:**
- Collect representative images
- Divide into fixed-size blocks (e.g., 4×4 = 16-dim vectors)
- Diverse training → better codebook

**2. Codebook Generation (LBG Algorithm):**

Step 1: Initialize codebook with K codewords (random or splitting)
Step 2: Assign each training vector to nearest codeword (Euclidean)
Step 3: Recompute codewords as centroids
Step 4: Repeat steps 2–3 until distortion converges
Step 5: Final codebook = K representative vectors

**3. Matching Process:**

**Encoding:** Divide input into blocks → find nearest codeword → store index
**Decoding:** Look up codeword for each index → reassemble

**Compression Ratio:** For 4×4 blocks (128 bits) → 8-bit index = 16:1.

**Variants:** Tree-structured VQ, mean-removed VQ, classified VQ.

**Applications:** Image compression, speech compression, pattern recognition.

---

## ====== PROBLEM SET V — UNIT V (MORPHOLOGICAL IMAGE PROCESSING) ======

### Q1. Two core morphological operations

The two core operations:

**1. Dilation (A ⊕ B)** — expands binary objects
**2. Erosion (A ⊖ B)** — shrinks binary objects

All other morphological operations are derived from these:
- Opening = Erosion → Dilation
- Closing = Dilation → Erosion
- Hit-or-Miss = combined erosions
- Boundary = original − erosion
- Hole filling, skeleton, thinning — iterative dilation/erosion

---

### Q2. Hit-or-miss transformation + structuring element for top-left corners

**Hit-or-Miss Transformation (HMT)** detects specific shapes using two disjoint structuring elements.

**Formula:** A ⊛ B = (A ⊖ B₁) ∩ (A^c ⊖ B₂)

Where:
- B₁ = foreground pattern (hit)
- B₂ = background pattern (miss)
- B₁ ∩ B₂ = ∅ (disjoint)

**For Top-Left Corner Detection:**

B₁ (foreground hit):
```
0 0 0
0 1 1
0 1 1
```

B₂ (background miss):
```
1 1 1
1 0 0
1 0 0
```

Center pixel = 1 only where top-left corner is detected.

**Applications:** Corner detection, isolated point detection, line endpoint detection, thinning, skeletonization.

---

### Q3. Erosion and dilation — examples + boundary effects

**Erosion (A ⊖ B):** A ⊖ B = { z | B_z ⊆ A } — shrinks objects.

```
A:                   A ⊖ B (3×3 SE):
0 0 0 0 0            0 0 0 0 0
0 1 1 1 0            0 0 0 0 0
0 1 1 1 0    →       0 0 1 0 0
0 1 1 1 0            0 0 0 0 0
0 0 0 0 0            0 0 0 0 0
```
Only center survives. Boundary moves inward.

**Dilation (A ⊕ B):** A ⊕ B = { z | (B̂)_z ∩ A ≠ ∅ } — grows objects.

```
A:                   A ⊕ B (3×3 SE):
0 0 0 0 0            0 0 0 0 0
0 0 0 0 0            0 1 1 1 0
0 0 1 0 0    →       0 1 1 1 0
0 0 0 0 0            0 1 1 1 0
0 0 0 0 0            0 0 0 0 0
```
Single pixel becomes 3×3 block. Boundary moves outward.

| Op | Effect | Boundary | Uses |
|---|---|---|---|
| Erosion | Shrink | Inward | Remove small objects/noise |
| Dilation | Grow | Outward | Fill small gaps, connect parts |

---

### Q4. Opening and closing — composed from erosion + dilation; smoothing, noise reduction, shape analysis

**Opening:** A ∘ B = (A ⊖ B) ⊕ B (Erode first, then dilate)

**Geometric meaning:** Removes small protrusions, smooths outer contours, preserves overall size.

**Effects:**
- Salt noise removal (small bright specks)
- Smoothing object outlines
- Removing thin connections
- Granulometry (size distribution analysis)

**Properties:** Anti-extensive (A ∘ B ⊆ A), idempotent.

**Closing:** A • B = (A ⊕ B) ⊖ B (Dilate first, then erode)

**Geometric meaning:** Fills small holes, connects nearby objects, smooths concave contours.

**Effects:**
- Pepper noise removal (small dark holes)
- Filling gaps
- Connecting nearby objects
- OCR (close character gaps)

**Properties:** Extensive (A ⊆ A • B), idempotent.

| Feature | Opening | Closing |
|---|---|---|
| Sequence | Erode → Dilate | Dilate → Erode |
| Removes | Small bright | Small dark holes |
| Effect | Smooth outside | Smooth inside |

---

### Q5. Erosion, dilation, opening, closing — effects on boundaries, holes, gaps

| Operation | Formula | Boundary | Holes | Gaps |
|---|---|---|---|---|
| **Erosion** (A ⊖ B) | Shrink | Moves inward | Enlarges | Widens |
| **Dilation** (A ⊕ B) | Grow | Moves outward | Shrinks/fills | Closes |
| **Opening** (A ∘ B) | (A ⊖ B) ⊕ B | Smooths outside | Slightly affected | Removes thin gaps |
| **Closing** (A • B) | (A ⊕ B) ⊖ B | Smooths inside | Fills small holes | Closes small gaps |

**Detailed Effects:**

- **Erosion:** Boundary inward; holes larger; gaps widen; small objects vanish
- **Dilation:** Boundary outward; holes shrink; gaps close
- **Opening:** Outer contour smoothed; small objects removed
- **Closing:** Inner contour smoothed; small holes filled

---

### Q6. Boundary extraction, hole filling, connected components — algorithms + examples

**(1) Boundary Extraction:** β(A) = A − (A ⊖ B)

Algorithm:
1. Erode A by B (3×3 SE)
2. Subtract eroded from original
3. Output = boundary pixels

```
A:                  β(A):
1 1 1 1 1           1 1 1 1 1
1 1 1 1 1           1 0 0 0 1
1 1 1 1 1   →       1 0 0 0 1
1 1 1 1 1           1 0 0 0 1
1 1 1 1 1           1 1 1 1 1
```

**(2) Hole Filling:** X_k = (X_{k-1} ⊕ B) ∩ A^c

Algorithm:
1. Find seed inside hole; X_0 = {p}
2. Dilate X by B
3. Intersect with complement of A
4. Repeat until X_k = X_{k-1}
5. Final filled = A ∪ X_k

**(3) Connected Component Extraction:** X_k = (X_{k-1} ⊕ B) ∩ A

Algorithm:
1. Seed pixel inside component
2. Dilate X by B
3. Intersect with A (not A^c)
4. Repeat until convergence
5. X_k = one connected component

**Applications:** Boundary extraction → contour mapping. Hole filling → OCR, shape analysis. Connected components → region labeling, blob detection.

---

### Q7. Morphological openings of increasing size → object size distributions (granulometry)

**Concept:** Apply opening with SE of increasing size; each opening removes objects smaller than the SE. Track area changes.

**Algorithm:**

1. Start with binary image A
2. For k = 1, 2, 3, ...:
   - Apply opening A_k = A ∘ B_k (B_k of radius k)
   - Compute area |A_k|
3. Compute differences d_k = |A_{k-1}| − |A_k|
4. d_k = total area of objects of size = k
5. Plot d_k vs k → granulometric curve

**Numerical Example:**
```
|A| = 100
|A ∘ B_1| = 95   → 5 pixels (size 0-1)
|A ∘ B_2| = 80   → 15 pixels (size 1-2)
|A ∘ B_3| = 50   → 30 pixels (size 2-3)
|A ∘ B_5| = 0    → all removed
```

Most objects are size 2-3.

**Applications:** Metallurgy (grain size), cell counting, soil science (particle size), industrial QC.

---

### Q8. Algorithm to extract boundaries of all objects in binary image

**Algorithm: Boundary Extraction**

**Formula:** β(A) = A − (A ⊖ B)

**Step-by-step:**
1. Take binary image A
2. Choose SE B (typically 3×3 square)
3. Erode A by B: A ⊖ B = { z | B_z ⊆ A }
4. Subtract eroded from original: β(A) = A − (A ⊖ B)
5. Output boundary image

**Why it works:** Erosion shrinks each object by one pixel-layer; subtraction reveals outermost layer → boundary. Works simultaneously for all objects.

**Example with multiple objects:**
```
A:                            β(A):
0 0 0 0 0 0 0 0 0 0           0 0 0 0 0 0 0 0 0 0
0 1 1 1 0 0 1 1 1 0           0 1 1 1 0 0 1 1 1 0
0 1 1 1 0 0 1 1 1 0     →     0 1 0 1 0 0 1 0 1 0
0 1 1 1 0 0 1 1 1 0           0 1 1 1 0 0 1 1 1 0
0 0 0 0 0 0 0 0 0 0           0 0 0 0 0 0 0 0 0 0
```

Boundaries of both objects extracted simultaneously.

**Properties:** Handles multiple objects without segmentation; linear time; extensible with different SEs.

---

### Q9. Connected components extraction via morphological operations

**Concept:** Extract a connected component of A starting from a seed pixel using iterative constrained dilation.

**Algorithm:**

1. Choose seed pixel p inside desired component; X_0 = {p}
2. Iterate: X_k = (X_{k-1} ⊕ B) ∩ A
3. Repeat until X_k = X_{k-1} (convergence)
4. X_k = all pixels of connected component

**To label all components:** Pick unlabeled foreground pixel as seed; repeat for each component; assign unique label.

**Comparison with other techniques:**

| Method | Approach | Complexity |
|---|---|---|
| Morphological (iterative dilation) | Set theory | O(passes · MN) |
| Two-pass labeling | Scan + union-find | O(MN) |
| Flood fill (BFS/DFS) | Graph traversal | O(MN) |
| Recursive labeling | DFS via recursion | O(MN), stack limits |

**Example:** Binary image with 3 disconnected regions → run algorithm 3 times with different seeds → label each as different component.

**Applications:** Object counting, image segmentation for OCR, robot vision, quality inspection.

---

### Q10. Morphological operations for noise removal (salt, pepper, mixed)

| Noise Type | Best Operation | Why |
|---|---|---|
| **Salt** (bright specks) | Opening (A ∘ B) | Removes small bright objects |
| **Pepper** (dark specks) | Closing (A • B) | Fills small holes |
| **Mixed (S+P)** | Open-Close or Close-Open | Removes both |

**Operation Effects:**

- **Opening (A ∘ B):** Salt removal — erode small bright pixels, dilate restores
- **Closing (A • B):** Pepper removal — dilate fills holes, erode restores
- **Open-Close:** First remove salt, then fill pepper (salt-dominated)
- **Close-Open:** First fill pepper, then remove salt (pepper-dominated)

**Effectiveness Table:**

| Noise | Opening | Closing | Open-Close | Close-Open |
|---|---|---|---|---|
| **Salt only** | ✅ Excellent | ❌ Poor | ✅ Good | ❌ Poor |
| **Pepper only** | ❌ Poor | ✅ Excellent | ❌ Poor | ✅ Good |
| **Mixed** | ⚠ Partial | ⚠ Partial | ✅ Good | ✅ Good |

**Order matters:** Opening and closing are non-commutative — Open-Close differs from Close-Open slightly.

**Conclusion:**
- Salt only → Opening
- Pepper only → Closing
- Mixed → Open-Close OR Close-Open

---

# END OF PROBLEM SET SOLUTIONS
