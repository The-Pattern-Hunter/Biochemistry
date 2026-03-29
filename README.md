# 🔬 Pattern Hunters: Enzyme Kinetics Series

### Two notebooks — from first principles to inhibition diagnosis

> *"Mathematics does not describe nature from the outside.  
> It is forced out of nature by the act of careful questioning."*

---

## What this is

Two self-guided Google Colab notebooks for BSc and MSc Biochemistry students, structured as a series. Each notebook is independent but they build on each other naturally.

**Notebook 1** teaches enzyme kinetics starting from raw observation — not equations. The Michaelis-Menten equation is the last thing students arrive at, not the first. By the time they see it, they have already understood why it must have the shape it has, why no other equation would fit, and what the parameters mean in a living enzyme working in a real soil.

**Notebook 2** teaches enzyme inhibition as a detective story — starting from anomalous data and reasoning toward a molecular diagnosis. Four inhibition types are treated not as categories to memorise but as four distinct physical situations, each with a different molecular story, a different experimental signature, and a different consequence for soil biomarker interpretation.

Both notebooks are explicitly scaffolded for two levels: BSc students engage with the observation and physical reasoning layers; MSc students additionally work through full algebraic derivations, quantitative Ki extraction, and the Dixon plot.

Most textbooks show one figure and hand down the equation. **These notebooks do the opposite.**

---

## The central argument

The standard textbook figure hides three things simultaneously:

1. **The progress curve** — what actually happens in one flask over time (the raw experiment that the MM curve is derived from)
2. **The experimental architecture** — that the MM curve requires many separate fresh flasks, not one reused flask with substrate added sequentially
3. **The diversity of real enzyme behaviour** — sigmoidal, substrate-inhibited, and bisubstrate curves exist and are biologically important

Showing only the hyperbolic v vs [S] curve without these three things produces students who can calculate Km from a Lineweaver-Burk plot but cannot design an enzyme kinetics experiment, cannot recognise when their data is corrupted, and cannot interpret Km as a biological signal.

---

## Open in Google Colab

### Notebook 1 — How the MM Equation Emerges from Nature

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/The-Pattern-Hunter/Biochemistry/blob/main/notebook/enzyme_kinetics_pattern_hunters.ipynb)

### Notebook 2 — Enzyme Inhibition: A Detective Notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/The-Pattern-Hunter/Biochemistry/blob/main/notebook/enzyme_inhibition_pattern_hunters.ipynb)

> No installation needed. Both notebooks run entirely in a browser — including on mobile.  
> Notebook 1 should be completed before Notebook 2, but each can also be used independently.

---

## Contents

### Notebook 1 — How the MM Equation Emerges from Nature

| Section | What students do | What emerges |
|---------|-----------------|--------------|
| **Setup** | Run one cell to load all functions | Ready to hunt |
| **1 — The real experiment** | Watch product form in one flask over time | The progress curve — the raw truth |
| **2 — The problem with measuring late** | Visualise all five confounds separately, then together | Why v₀ is the only trustworthy measurement |
| **3 — The architecture** | Compare right way vs wrong way; see what reusing a flask does to your Km | Many separate fresh flasks, not one |
| **4 — The data demands a shape** | Compare linear, quadratic, and hyperbolic fits against real data | The data corners the equation |
| **5 — The mechanism** | Watch active sites fill up as [S] rises | Saturation is physical, not mathematical |
| **6 — The equation is cornered** | Step-by-step derivation; verify against data; Lineweaver-Burk | The MM equation — no other form is possible |
| **7 — Parameters carry biology** | Compare four enzyme scenarios with different Km and Vmax | Km = affinity, Vmax = capacity, Vmax/Km = efficiency |
| **8 — Your own experiment** | Modify Vmax, Km, toggle confounds; predict before running | Parameters have consequences you can anticipate |
| **9 — The complete picture** | All four curve families with their progress curves | What the textbook's one figure hides |
| **10 — Western Odisha connection** | Soil enzyme kinetics along a contamination gradient | The equation as a field diagnostic tool |
| **Summary** | Table of the full journey | The hunt is complete |

### Notebook 2 — Enzyme Inhibition: A Detective Notebook

| Section | What students do | What emerges |
|---------|-----------------|--------------|
| **Setup** | Load kinetic functions for all four inhibition types | Ready to diagnose |
| **1 — Something is wrong** | Observe anomalously low rate; generate hypotheses | The concept of an inhibitor as a separate molecular actor |
| **2 — Where does it bind?** | Draw three binding locations; predict consequences | Four physical situations, not four named categories |
| **3 — Competitive** *(BSc + MSc)* | 6-panel cell: LB lines, Ki extraction, Cheng-Prusoff | Km rises, Vmax unchanged — substrate can win |
| **4 — Non-competitive** *(BSc + MSc)* | 6-panel cell: Dixon plot, y-intercept vs [I], IC₅₀ shift | Vmax falls, Km unchanged — substrate cannot help |
| **5 — Uncompetitive** | The paradox: more substrate makes it worse | Both Km and Vmax fall — parallel LB lines |
| **6 — Mixed inhibition** | The general case containing all others | LB intersection in 2nd quadrant; diagnostic table |
| **7 — LB as detective tool** *(BSc + MSc)* | Identify unknown type; extract Ki from noisy real data | From pattern recognition to quantitative diagnosis |
| **8 — Reversible vs irreversible** | Preincubation time test; EDTA rescue protocol | Heavy metals — temporary stress vs permanent damage |
| **9 — IC₅₀ and dose-response** | Cheng-Prusoff equation; potency ranking of heavy metals | Inhibitor potency as an ecotoxicological index |
| **10 — Western Odisha** | Full kinetic fingerprint across contamination gradient | Inhibition type as a contamination fingerprint |
| **11 — Your own experiment** | Choose type, set Ki, predict LB pattern before running | Full diagnostic workflow from anomaly to identification |
| **Summary** | Master decision tree: observe → test → diagnose | The complete inhibition detective toolkit |

---

## The five confounds (Section 2)

When you measure enzyme rate at any time point other than t ≈ 0, five things have already changed — simultaneously, inseparably:

| Confound | What happens | What it violates |
|----------|-------------|-----------------|
| Substrate depletion | [S] falls as reaction proceeds | MM assumes [S] is fixed |
| Product inhibition | Product competes with substrate for active site | MM assumes [P] = 0 |
| Reverse reaction | As [P] builds, P → S accelerates | MM describes only forward rate |
| Enzyme denaturation | Activity declines over time | MM assumes [E] is constant |
| Steady-state violated | [ES] ≈ constant only when [S] >> Km | Mathematical foundation of derivation |

The only way to be free of all five simultaneously is to measure before any of them has had time to develop. That is what v₀ does.

---

## The flask architecture (Section 3)

This is the most commonly omitted concept in undergraduate enzyme kinetics teaching.

**Wrong way** — one flask, substrate added sequentially:
```
Flask:  add [S]=5 mM → measure rate (product has built up) → add [S]=10 mM → measure again...
```
By the second addition: product inhibition is active, enzyme has been running for minutes, [S] is not what you think. Every rate you measure after the first is corrupted. The Km you calculate will be wrong.

**Right way** — one fresh flask per [S] value:
```
Flask 1:  [S]0 =   5 mM  →  measure v0 at t≈0  →  discard rest
Flask 2:  [S]0 =  10 mM  →  measure v0 at t≈0  →  discard rest
Flask 3:  [S]0 =  20 mM  →  measure v0 at t≈0  →  discard rest
...
Flask 8:  [S]0 = 220 mM  →  measure v0 at t≈0  →  discard rest
                                                      ↓
                                            8 points → MM curve
```

The notebook quantifies exactly how wrong the wrong-way Km is, and asks students: *if this were your soil enzyme data, what would the corrupted Km tell you wrongly about contamination?*

---

## The four curve shapes (Section 9)

The notebook places all four side by side — each with the progress curve that generates it — making visible what the standard textbook figure hides:

| Curve type | Shape | Example enzymes | Textbook status |
|-----------|-------|----------------|----------------|
| Michaelis-Menten | Hyperbolic | Urease, amylase, lysozyme | Shown |
| Cooperative | Sigmoidal | Phosphofructokinase, ATCase | Usually missing |
| Substrate inhibition | Bell-shaped | Acetylcholinesterase, invertase | Rarely shown |
| Bisubstrate / two-phase | Two Km values | Soil phosphatase, hexokinase | Almost never shown |

---

## Western Odisha connection (Section 10)

The notebook is grounded in the ecology of Western Odisha. Section 10 uses soil urease kinetics along a contamination gradient from an industrial zone as the primary example for reading biological meaning from Km and Vmax.

**The research link:**  
This notebook was developed alongside the OSHEC-funded project *"Genomic Responses of Earthworms to Industrial Pollution in Western Odisha: Towards the Development of Soil Health Biomarkers"* (Ref. No. 25EM/ZO/147). The soil enzyme data placeholders in Section 10 can be replaced directly with field measurements from project sampling sites to convert the notebook into a live analysis tool.

**Soil enzyme kinetics as biomarkers:**
- Elevated Km in contaminated soil = heavy metal disrupting active site affinity
- Reduced Vmax = fewer active enzyme molecules (denaturation or inhibition)
- Vmax/Km = single integrated index of catalytic efficiency, directly comparable across sites

---

## Who this is for

- **BSc students** — both notebooks are explicitly scaffolded for undergraduate level. Each code section is labelled *BSc: observe panels A, B, C*. No prior programming experience needed.
- **MSc students** — the same cells contain deeper layers labelled *MSc extension*: full algebraic derivations, Ki extraction from LB slope and y-intercept plots, Dixon plots, and Cheng-Prusoff verification.
- **PhD scholars** working on enzyme-based biomonitoring — the Western Odisha sections in both notebooks use placeholder data that can be replaced directly with field measurements from OSHEC project sites.
- **Teachers** at regional colleges with limited laboratory access — every concept in both notebooks can be taught with only the notebook and a discussion. No spectrophotometer, no reagents, no laboratory required.

---

## Pedagogical philosophy: Pattern Hunters

The Pattern Hunters approach was developed for teaching science at regional colleges in India where laboratory access is limited but intellectual rigour should not be. The core principle:

> **Replace the missing experiment with the missing question.**  
> The question creates the same cognitive demand as the experiment.

A student who has argued through *why the curve must have a ceiling* will derive the MM equation in ten minutes. A student who was given the equation first will struggle with it for years.

Each section of this notebook begins with a question or an observation — never with an answer. The equation appears only after students have already understood why it must have the shape it has. That moment of recognition — *of course, there is no other equation it could be* — is the goal.

---

## Requirements

None for students. Open the Colab link and run.

For local use:

```bash
pip install numpy matplotlib scipy
jupyter notebook enzyme_kinetics_pattern_hunters.ipynb
jupyter notebook enzyme_inhibition_pattern_hunters.ipynb
```

---

## Repository structure

```
The-Pattern-Hunter/Biochemistry/
│
├── notebook/
│   ├── enzyme_kinetics_pattern_hunters.ipynb      # Notebook 1 — MM equation
│   └── enzyme_inhibition_pattern_hunters.ipynb    # Notebook 2 — Inhibition
│
├── README.md                                      # This file
│
└── figures/                                       # Auto-generated by notebooks
    │
    ├── notebook1/
    │   ├── section1_progress_curve.png
    │   ├── section2_five_confounds.png
    │   ├── section3_flask_architecture.png
    │   ├── section4_data_demands_shape.png
    │   ├── section5_mechanism.png
    │   ├── section6_derivation.png
    │   ├── section7_biological_meaning.png
    │   ├── section9_complete_picture.png
    │   └── section10_biomarker.png
    │
    └── notebook2/
        ├── inh_s1_anomaly.png
        ├── inh_s2_binding_sites.png
        ├── inh_s3_competitive_deep.png
        ├── inh_s4_noncompetitive_deep.png
        ├── inh_s5_uncompetitive.png
        ├── inh_s6_mixed.png
        ├── inh_s7_bsc_task.png
        ├── inh_s7b_msc_reveal.png
        ├── inh_s8_reversible.png
        ├── inh_s9_ic50.png
        └── inh_s10_western_odisha.png
```

---

## Licence

MIT — free to use, adapt, and redistribute with attribution.  
If you adapt this notebook for your own teaching, a note in your materials pointing back here is appreciated but not required.

---

## Citation

If you use these notebooks in teaching or research:

```
Patel, A. (2026). Pattern Hunters: Enzyme Kinetics Series.
Notebook 1: How the Michaelis-Menten Equation Emerges from Nature.
Notebook 2: Enzyme Inhibition — A Detective Notebook.
Kuchinda Degree College, Department of Zoology, Sambalpur University.
GitHub: https://github.com/The-Pattern-Hunter/Biochemistry
```

---

## Contact

**Dr Alok Patel**  
Lecturer in Zoology, Department of Zoology  
Kuchinda Degree College (Sambalpur University)  
Kuchinda, Odisha, India

*OSHEC Research Project: Genomic Responses of Earthworms to Industrial Pollution in Western Odisha*

---

*A regional college is not a lesser version of an elite institution.  
It is a different setting that demands a more honest pedagogy —  
one that teaches science as a way of questioning rather than a body of settled answers.*
