# Numerical results of Part III (summary)

All numbers are exact. File names refer to `data/`.

## 1. The hexad (hexad_search.py, hexad_fit.py, sextic_identity.py)

For every (λ_3, λ_5) ∈ F_q × F_q^× with ker L' ⊂ F_{q^12} (q = 8, 32) the Frobenius-stable translation classes of
hexads with duad set ker L' \ 0 were enumerated. Exactly one of them has normalised sextic B/λ_5^2 with
B = λ_5^2 u^6 + λ_3^2 u^2 + λ_5 u + 1; its factorisation type over F_q is the S_6-class of the Frobenius.
The identity L' = x^4 B^2 + B + 1 and the membership L'(r+s) ∈ (B(r), B(s)) are verified symbolically over
F_2[r, s, λ_3, λ_5] (Gröbner basis).

Number of stable symplectic forms per Frobenius class and the types of the Frobenius in them (hexads_k3.json,
hexads_k5.json, stable_stats.txt), compared with 28|t|/|C|:

| class | found | predicted |
|---|---|---|
| 1^6 | 28 | 28 |
| 2 1^4 | 4 | 4 |
| 2^2 1^2, 2^3 | 8 = 6 (type 2^2 1^2) + 2 (type 2^3) | 6 + 2 |
| 3 1^3 | 1 | 1 |
| 3^2 | 10 | 10 |
| 3 2 1 | 1 | 1 |
| 4 1^2, 4 2 | 2 = 1 + 1 | 1 + 1 |
| 6 | 2 | 2 |
| 5 1 | not searched (ker L' ⊄ F_{q^12}) | 3 |

## 2. Class counts of B over F_q (sextic_types.py)

Odd k, verified for q = 8, 32, 128, 512 (sextic_types.txt), λ_3 ≠ 0 | λ_3 = 0:

| class | λ_3 ≠ 0 | λ_3 = 0 |
|---|---|---|
| 1^6 | (q−2)(q−8)/720 | 0 |
| 2 1^4 | (q−2)(q−8)/48 | 0 |
| 2^2 1^2 | q(q−2)/16 | 0 |
| 2^3 | (q−2)(q−8)/48 | (q−2)/6 |
| 3 1^3 | (q+1)(q−2)/18 | 0 |
| 3^2 | (q+1)(q−2)/18 | 0 |
| 3 2 1 | (q+1)(q−2)/6 | 0 |
| 4 1^2 | (q−2)(q−4)/8 | (q−2)/2 |
| 4 2 | q(q−2)/8 | 0 |
| 5 1 | (q^2+1)/5 | 0 |
| 6 | (q+1)(q−2)/6 | (q+1)/3 |

Even k (sextic_types_even.txt: q = 4, 16, 64, 256; sextic_types_k10.txt: q = 1024). The counts depend on k mod 4.
Common to both residues: 2 1^4, 2^3: q(q−4)/48; 3 1^3, 3^2: (q−1)(q−4)/18; 3 2 1, 6: q(q−1)/6; 4 1^2, 4 2: q^2/8.
k ≡ 2 (mod 4): 1^6: (q−4)(q−28)/720; 2^2 1^2: (q−4)^2/16; 5 1: (q−3)(q+1)/5; pure column 1^6: (q−4)/60,
2^2 1^2: (q−4)/4, 5 1: 2(q+1)/5, 3^2: (q−1)/3 — all fifteen counts confirmed at q = 1024.
k ≡ 0 (mod 4): 1^6: (q−16)^2/720; 2^2 1^2: q(q−8)/16; 5 1: (q−1)^2/5; pure column 1^6: (q−16)/60, 2^2 1^2: q/4,
5 1: 2(q−1)/5, 3^2: (q−1)/3 — fitted to q = 16, 256 only.

## 3. Witt sums (witt_lpoly.py)

For each (λ_3, λ_5, λ_1): the Gauss sums s_m over F_{q^m}, m = 1..4, the four Frobenius eigenvalues, the predicted
S'' = −Σ ω_j^12, and the comparison of Σ_{λ_1} S'' with the exact W' of Part II. Agreement for every pair at
q = 8 (56 pairs), q = 32 (4 pairs per class, witt_lpoly_k5.txt), q = 4 and q = 16 (all pairs, even k).

W'/q^7 by class (odd k | even k) and the multiset of S''(λ_1)/4q^6 over λ_1 ∈ F_q:

| class | odd k | even k | S''(λ_1)/4q^6, odd k |
|---|---|---|---|
| 1^6 | 4 | (−4, not yet observed) | +1 (q times) |
| 2 1^4 | 0 | 0 | ±1, q/2 each |
| 2^2 1^2 | 0 | 0 | ±1, q/2 each |
| 2^3 | 4 | −4 | +1 (q times) |
| 3 1^3 | 4 | −4 | +1 (q times) |
| 3^2 | 4 | −4 | +1 (q times) |
| 3 2 1 | 0 | 0 | ±1, q/2 each |
| 4 1^2 | 2 | −2 | +1 (q/2), 0 (q/2) |
| 4 2 | −2 | 2 | −1 (q/2), 0 (q/2) |
| 5 1 | −1 | 1 | −1/4 (q times), i.e. S'' = −q^6 |
| 6 | 4 | −4 | +1 (q times) |

Normalised eigenvalues ω_j/√q are 24th roots of unity when ker L' ⊂ F_{q^12} and 40th roots in the class 5 1
(η ζ_5^c with η a primitive 8th root of unity for odd k, η ∈ {±1, ±i} for even k); complete lists in
witt_lpoly_k3_b120.txt (q = 8), witt_lpoly_k5.txt (q = 32), witt_lpoly_k2.txt, witt_lpoly_k4.txt (q = 4, 16).

Decomposition of q^3 X = Σ W' into the parts (0,0) | pure cubic | pure quintic | mixed, in units of q^7:
q = 8: 1, 8, 22, 41 (total 72 = q^2 + q); q = 32: 1, 32, 94, 929 (1056); q = 4: −1, −2, −2, −7 (−12 = −q^2 + q);
q = 16: −1, −14, −14, −211 (−240).

## 4. Trace identities (hexad_traces.py, hexad_traces_k35.txt)

For q = 8, 32 and every pair: Tr_{q/2}(r_5 + r_6) = 0 in the classes of order 4; every class has a root with absolute
trace 0; Tr_{q^m/2} vanishes on ker L' for every even m with ker L' ⊂ F_{q^m}. These are the inputs of the
integrality theorem and of the reductions S'' = q^4 s_4 (N_0 | 4) and S'' = ±4q^6 (N_0 ∈ {3, 6}).
