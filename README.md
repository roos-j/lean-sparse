# Formalization of multi-scale sparse domination

This is a Lean 4 formalization of the main theorem (Theorem 1.1) from the paper
[Multi-scale sparse domination](https://doi.org/10.1090/memo/1491) by D. Beltran, J. Roos and
A. Seeger.

A bilinear form sparse domination theorem is proved that applies to many multi-scale operators
beyond Calderon-Zygmund theory. For a family of operators T_j on vector-valued functions on
Euclidean space, satisfying a support condition at scale 2^j, uniform weak type (p,p) and
restricted strong type (q,q) bounds for their partial sums, uniform single-scale L^p to L^q bounds
and an epsilon-regularity condition together with its adjoint version, the bilinear forms of all
partial sums are dominated by maximal sparse forms. The constant is the sum of the weak type and
restricted strong type constants plus the single-scale constant times the logarithm of two plus the
ratio of the regularity constant to the single-scale constant, up to a factor depending only on
the dimension, the exponents, the regularity exponent and the sparseness parameter. The necessary
conditions and the applications to Fourier multipliers, maximal functions, square functions and
variation norm operators in the paper are not formalized.

Reference: [Mem. Amer. Math. Soc. 298 (2024), no. 1491](https://doi.org/10.1090/memo/1491),
[arXiv:2009.00227v3](https://arxiv.org/abs/2009.00227v3).

## Main theorems

`Auto.mainthm`

**Theorem 1.1** (multi-scale sparse domination). Let $d \ge 1$, $1 < p \le q$,
$\varepsilon > 0$ and $0 < \gamma < 1$. Then `MainTheoremStatement d p q ε γ` holds.

Here `MainTheoremStatement d p q ε γ` asserts that there is a constant $K > 0$ such that for every
scalar field $\Bbbk$ (real or complex), all Banach spaces $B_1, B_2$ over $\Bbbk$, every family
$(T_j)_{j \in \mathbb Z}$ satisfying `BasicAssumptions` with constants
$A(p), A(q), A_\circ(p,q), B \ge 0$, all integers $N_1 \le N_2$ and all
$f_1 \in \mathcal S_{B_1}$, $f_2 \in \mathcal S_{B_2^*}$,

$$\Big| \Big\langle \sum_{j=N_1}^{N_2} T_j f_1, f_2 \Big\rangle \Big| \le
  K \, \mathcal C \, \Lambda^*_{\gamma,p,q'}(f_1, f_2),$$

where $\mathcal C = A(p) + A(q) + A_\circ(p,q) \log(2 + B / A_\circ(p,q))$. All definitions, and
the conventions in which they differ from the paper, are documented in
[`Challenge.lean`](Challenge.lean).

## Layout

- `Challenge.lean`: the advertised statement and the definitions it uses (imports only Mathlib).
- `Solution.lean`: imports the formalization; Comparator configuration in `comparator.json`.
- `LeanSparse/Auto/Sec1Introduction.lean`: definitions and the statement (Section 1 of the paper).
- `LeanSparse/Auto/Sec3SingleScale.lean`: single-scale estimates (Section 3).
- `LeanSparse/Auto/Sec4ProofOfMainResult.lean`: the proof of Theorem 1.1 (Section 4).
- `LeanSparse/Auto/HardyLittlewoodMaximal.lean`, `WhitneyDecomposition.lean`,
  `SparseCarleson.lean`: general prerequisites.
- `automation/`: instructions, status ledger and discrepancy report of the formalization.
- `formalization.yaml`: metadata.

Build with `lake exe cache get && lake build`. The formalization was generated predominantly by
Claude.
