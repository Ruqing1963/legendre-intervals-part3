# Prime polynomials in Legendre intervals over F_{2^k}[t], III

The hexad of a quartic linearised polynomial, the symplectic group Sp_4(F_2), and the Witt sums behind the constant X.

Preprint DOI: 10.5281/zenodo.23290724.

Third part of the series on Open Problem 8.2 of
[legendre-intervals-explicit-formula](https://github.com/Ruqing1963/legendre-intervals-explicit-formula)
(Part I, DOI 10.5281/zenodo.23225896) and sequel to
[legendre-intervals-part2](https://github.com/Ruqing1963/legendre-intervals-part2)
(Part II, DOI 10.5281/zenodo.23252762). Part II reduced the constant X of the degree-6 Legendre variance to
sums W'(λ_3, λ_5) of order-4 characters governed by the kernel of
L' = λ_5^4 x^16 + λ_3^4 x^8 + x^4 + λ_3^2 x^2 + λ_5 x, observed numerically to carry an action of S_6 ≅ Sp_4(F_2)
with exact polynomial class counts. This paper explains and largely proves that picture.

## Results in one paragraph

* **Hexad theorem (proved, all k).** ker L' is the set of pairwise sums of the six roots of the sextic
  **B = λ_5^2 u^6 + λ_3^2 u^2 + λ_5 u + 1 = u·A(u) + 1**, A the Bluher quintic of Part II, via the identity
  L' = x^4 B^2 + B + 1. The roots satisfy T'(r) = 1 for the polar operator T'; the coset T'^{-1}(1) consists of the six
  roots and the ten synthematic totals; the family L + ε x^4 corresponds to uA(u) + √ε and degenerates to the quintic
  frame of Part II at ε = 0.
* **Frobenius classes (proved).** The S_6-class of the Frobenius on ker L' is the factorisation type of B over F_q; the
  symplectic form is the duad–syntheme pairing of the generalised quadrangle W(2). The number of Frobenius-stable
  symplectic forms of each type is 28|t|/|C| (C the GL_4(F_2)-class); a Frobenius of order 4 is a 4·1² for one of its
  two invariant forms and a 4·2 for the other, and only the canonical form (the one given by B) predicts W'.
* **Counting.** First moments of the family u^6 + a u^2 + b u + b^2 proved: Σ N_1 = (q−1)^2, Σ N_1(N_1−1) = (q−2)^2,
  Σ (N_2 − N_1) = q(q−2). The eleven class-count polynomials of Part II (odd k) are verified for q ≤ 512; for even k
  the counts depend on k mod 4 and are given by new polynomials (k ≡ 2 mod 4 verified for q ≤ 1024).
* **Witt sums (proved).** The order-4 sums S''(λ) are Frobenius traces of rank-4 Witt–Artin–Schreier sheaves.
  Every S''(λ) is an integer, equal to 0 or ±4q^6 (±q^6 for 5-cycles); the normalised Frobenius eigenvalues are roots
  of unity. **Class of 5-cycles:** the L-polynomial is (1 − η^5 q^{5/2} T^5)/(1 − η q^{1/2} T) with η a primitive 8th
  root of unity for odd k, hence S'' = −q^6 for every λ_1 and W' = −q^7 (unconditional; +q^7 for even k). **Classes with
  kernel in F_{q^4}:** the F_{q^12}-sum equals q^4 times the F_{q^4}-sum. **Classes with N_0 ∈ {3, 6}:** all S'' = ±4q^6.
  The sign pattern in λ_1 is an F_2-quadratic form on T'(V).
* **What remains for X = q^6 + q^5 (odd k):** the class counts (Conjecture 5.3) and the signs of the Gauss sums s_4 on
  F_{q^4} and s_6 on F_{q^6} (Conjecture 6.16), both verified exactly; the L-polynomial predictions reproduce every W'
  at q = 8 (all pairs), q = 32 (four pairs per class) and, for even k, q = 4, 16 (all pairs).

See the status table at the end of `paper/paper_part3.pdf` for exactly what is proved, verified, or conjectural.

## Layout

```
paper/     paper_part3.tex / .pdf, table_k3.tex (Appendix A), make_figures3.py, figures/ (four vector figures)
code/      verification scripts (numpy, sympy); self-contained (includes the field tables fqlib.py and the Part II
           modules legendre_d6_qf.py, legendre_var_check.py, quintic_check.py, legendre_d6_Wp_pattern.py they import)
data/      exact outputs quoted in the paper
results/   summary of the numerical results (class counts, W' by class, eigenvalue classes) in Markdown
```

## Reproducing

```bash
pip install -r requirements.txt
cd code
python sextic_identity.py                 # L' = x^4 B^2 + B + 1 and ker L' = pairwise root sums (symbolic + q = 8, 32)
python sextic_types.py 3 5 7 9            # class counts of B over F_q, odd k (Table 2); 2 4 6 8 10 for even k (Table 11)
python hexad_search.py 3                  # Frobenius-stable hexads / symplectic forms -> data/hexads_k3.json (k = 5: 5 min)
python hexad_fit.py 5                     # recovers the coefficients of B from the stable classes
python hexad_signs.py 3 5                 # roots in the coset T'^{-1}(1), traces, radical of the F_2-form of Part II
python hexad_traces.py 3 5                # trace identities on the hexad (Lemma 4.4)
python stable_stats.py 3 5                # stable symplectic structures per class (Proposition 4.5, Table 4)
python witt_lpoly.py 3                    # Witt sums over F_{q^m}, m <= 4, L-polynomials, S''(lambda_1) (Tables 5, 6; 2.5 min)
python witt_lpoly.py 5 4                  # q = 32, four pairs per class (about 2 h); witt_lpoly.py 2 / 4 for even k
python appendix_table_k3.py > ../paper/table_k3.tex
cd ../paper && python make_figures3.py && pdflatex paper_part3.tex   # run pdflatex three times for references
```

Run times (laptop): everything above runs in seconds to minutes except `hexad_search.py 7` (hours),
`witt_lpoly.py 5 4` (2 h) and `sextic_types.py 10` (28 min).

## Citation

R. Chen, *Prime polynomials in Legendre intervals over F_{2^k}[t], III: the hexad of a quartic linearised polynomial,
the symplectic group Sp_4(F_2), and the Witt sums behind the constant X*, preprint (2026), DOI 10.5281/zenodo.23290724.

## License

Paper, data, figures and results: CC BY 4.0. Code: MIT. See `LICENSE`.
