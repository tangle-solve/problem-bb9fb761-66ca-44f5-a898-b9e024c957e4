<!-- solve-problem:bb9fb761-66ca-44f5-a898-b9e024c957e4 -->
# VP versus VNP

A [Tangle Solve problem](https://solve.tangle.tools/problems/bb9fb761-66ca-44f5-a898-b9e024c957e4).

## What is the problem?

**VP vs. VNP** is the central open problem of algebraic complexity theory. Work over a field F (char 0 for the canonical version, F = ℚ or ℂ).

An **arithmetic circuit** is a DAG whose inputs are variables x₁,…,xₙ and constants, whose gates compute +, −, ×. Size = number of gates.

- **VP** = families (fₙ) of multivariate polynomials with poly(n) variables, poly(n) degree, computable by poly(n)-size arithmetic circuits.
- **VNP** = families (fₙ) where fₙ(x) = Σ_{e ∈ {0,1}^{poly(n)}} gₙ(x, e), with g ∈ VP. Informally: "exponentially large polynomially-computable sums" — the permanent Perₙ(x) = Σ_σ ∏ᵢ x_{i,σ(i)} is the canonical VNP-complete polynomial (for char ≠ 2, also the Hamiltonian-cycle polynomial).

**Problem:** Prove VP ≠ VNP, i.e., exhibit an explicit polynomial family in VNP (the permanent is the standard candidate) requiring super-polynomial-size arithmetic circuits. (Consistency VP = VNP is also logically possible, though widely disbelieved.)

Key distinction from Boolean P vs. NP: over arithmetic circuits, one can prove unconditional lower bounds — depth-3 lower bounds exist — so the problem is *not* automatically blocked by natural-proofs-style barriers, though geometric complexity theory has revealed its own barriers (Mulmuley–Sohoni).

## Why does it matters?

Resolving it would settle the algebraic counterpart of efficient verification vs. computation, and — via Valiant's completeness results and Koiran's transfer results under GRH — would imply consequences for the Boolean counting hierarchy (P^#P ⊄ NC/poly-type separations). Lower bounds for the permanent would also derandomize polynomial identity testing (PIT) in a strong sense: the Kabanets–Impagliazzo program shows hard explicit polynomials yield derandomization of PIT. The problem anchors geometric complexity theory, the "chasm at depth 4" program, and the algebraic natural proofs barrier.

## What's already known?

- **Valiant (1979):** defined VP/VNP; permanent is VNP-complete, determinant is (nearly) VP-complete under projections.
- **Depth restrictions solved:** exponential lower bounds for the permanent against depth-3 (ΣΠΣ, Nisan–Wigderson), and — the best current general result — against depth-4 circuits of the form ΣΠΣΠ with bottom fan-in t, via the "chasm at depth 4" (Agrawal–Vinay, Koiran, Tavenas): any poly-size circuit for the permanent can be converted to a depth-4 circuit of poly size and bottom fan-in O(√(n log n)). Lower bounds currently reach bottom fan-in ~O(√n) — off by a logarithmic factor (Kayal–Saha–Saptharishi; Gupta–Kamath–Kayal–Saptharishi gave the sharp Ω(√n) result).
- **Approaches:** (1) Shifted partial derivative / skewed partials dimension counting; (2) Geometric Complexity Theory (Mulmuley–Sohoni): orbit-closure separation of det/per immanants via representation theory — stalled on positivity/algebraic-geometry questions; (3) Algebraic natural proofs (Forbes–Shpilka–de Wolf, Blum–Ivanov–Schnider–Thierauf) — a barrier: many circuit-lower-bound techniques would also give explicit hard polynomials contradicting known PIT reducibility; (4) Lower bounds for restricted models (monotone: exponential permanent lower bound, Jerrum–Snir; multi-k-ic; read-once; noncommutative).
- Best unconditional lower bound for **general** arithmetic circuits computing an explicit poly-degree-n polynomial: slightly superlinear (Ω(n log n)-ish via Baur–Strassen on individual degrees), essentially stuck for decades.

## What would count as solving it?

1. **Separation:** a proof that Perₙ (or any explicit VNP family) requires n^{ω(1)}-size general arithmetic circuits over char 0.
2. **Collapse:** a poly-size circuit family for the permanent — a shocking positive resolution.
3. **Partial credit milestones:** (a) exponential depth-4 lower bound with bottom fan-in ω(√(n log n)) (closes the depth-4 gap but does NOT solve VP vs. VNP by itself — the chasm reduction is one-way); (b) super-polynomial lower bound against depth 5; (c) algebraically natural-proof barrier circumvention.

## How to start

1. Read Shpilka–Yehudayoff's survey, especially the chapters on lower bounds (depth-3/4) and PIT — it's the best single orientation.
2. Learn the chasm-at-depth-4 reduction (Agrawal–Vinay; Koiran's homogenization; Tavenas's improved depth reduction) and the shifted-partial-derivative technique (Kayal–Saha–Saptharishi; Gupta et al.) to understand exactly where current bounds lose the log factor.
3. Understand the barriers before attacking: Blum–Ivanov–Schnider–Thierauf's algebraic natural proofs, and Chou–Forbes–Garg–Hrubeš on barriers for multi-round techniques.
4. Consider restricted settings where progress may transfer: homogeneous depth-5, low-depth arithmetic circuits (recent progress by Limaye–Srinivasan–Tavenas on log-depth lower bounds — verify current status), or GCT for small representation-theoretic cases.

Main obstacle: no known technique handles general circuits with product gates of unbounded interplay; depth reduction means you must beat all depths simultaneously.

## Key references

- L. G. Valiant, "Completeness Classes in Algebra," STOC 1979 (and SIAM J. Comput. 1979). Defines VP/VNP, proves permanent is VNP-complete. https://doi.org/10.1137/0208022
- A. Shpilka, A. Yehudayoff, "Arithmetic Circuits: A Survey of Recent Results and Open Questions," Foundations and Trends in Theoretical Computer Science, 2010. The standard survey of circuit lower bounds, depth reduction, and PIT. https://doi.org/10.1561/0400000039
- M. Agrawal, V. Vinay, "Arithmetic Circuits: A Chasm at Depth Four," FOCS 2008. Shows depth-3/4 lower bounds suffice for general lower bounds. https://arxiv.org/abs/0804.4259
- P. Koiran, "Arithmetic Circuits: The Chasm at Depth Four Gets Wider," 2012. Homogenization improvement to the depth reduction. https://arxiv.org/abs/1006.4700
- S. Tavenas, "Improved Bounds for Reduction to Depth 4 and Depth 3," MFCS 2013. Optimal depth-reduction parameters. https://arxiv.org/abs/1304.0910
- N. Kayal, C. Saha, R. Saptharishi, "A Super-polynomial Lower Bound for Regular Arithmetic Formulas," and Gupta–Kamath–Kayal–Saptharishi, "Arithmetic Circuits: A Chasm at Depth Three," FOCS 2013 / ECCC 2013. Depth-4 lower bounds for the permanent near the chasm threshold. https://eccc.weizmann.ac.il/report/2013/026/
- K. Mulmuley, M. Sohoni, "Geometric Complexity Theory I/II," SIAM J. Comput. 2001, 2008. Representation-theoretic program to separate det from per orbit closures.
- I. Newton et al. — *(omit)*; instead: J. Forbes, A. Shpilka, R. de Wolf, "Algebraic Natural Proofs," and M. Blum, G. Ivanov, R. Schnider, M. Thierauf, ECCC 2020. The algebraic natural-proof barrier. https://eccc.weizmann.ac.il/report/2020/032/ (verify link)
- V. Kabanets, R. Impagliazzo, "Derandomizing Polynomial Identity Tests Means Proving Circuit Lower Bounds," STOC 2003. Connects hard explicit polynomials to PIT derandomization. https://doi.org/10.1145/780542.780720

## Warnings

- **Depth-4 ≠ the whole problem:** closing the depth-4 gap does not immediately separate VP from VNP; Tavenas's reduction loses parameters so that "depth-4 lower bounds suffice" requires bounds for *all* bottom fan-ins up to O(√(n log n)), and the reduction also changes the polynomial (homogenization/composition).
- **Characteristic matters:** the permanent is VNP-complete only for char ≠ 2; in char 2, per = det. State your field.
- **Algebraic natural proofs:** if your lower-bound technique applies to all "explicit" polynomials via an efficiently computable property, it may be doomed — check your idea against this barrier.
- **"Explicit" must mean poly-time constructible coefficients** (or VNP membership); a nonconstructive counting argument doesn't count.
- Small-circuit results for the permanent don't transfer: constants/field extensions matter in reductions.

---
*`ALGO-000040` · unverified*

## Acceptance guidance

1. **Separation:** a proof that Perₙ (or any explicit VNP family) requires n^{ω(1)}-size general arithmetic circuits over char 0.
2. **Collapse:** a poly-size circuit family for the permanent — a shocking positive resolution.
3. **Partial credit milestones:** (a) exponential depth-4 lower bound with bottom fan-in ω(√(n log n)) (closes the depth-4 gap but does NOT solve VP vs. VNP by itself — the chasm reduction is one-way); (b) super-polynomial lower bound against depth 5; (c) algebraically natural-proof barrier circumvention.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/bb9fb761-66ca-44f5-a898-b9e024c957e4?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000040.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000040)
