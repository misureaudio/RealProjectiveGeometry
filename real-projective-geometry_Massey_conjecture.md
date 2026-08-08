
# Massey's Immersion Conjecture — Proved by Cohen (1985)

## 1. The Problem

Given a smooth, compact, *n*-dimensional manifold *M*, what is the smallest dimension of Euclidean space **R**ᵈ in which *M* can be **immersed** (i.e., mapped smoothly with everywhere-injective differential, allowing self-intersections)?

Whitney (1936) showed that **every** such *M* immerses in **R**²ⁿ, and in fact embeds in **R**²ⁿ. The question is: can we do better?

---

## 2. Massey's 1960 Theorem — The Obstruction

William S. Massey (1960) proved the following:

> **Theorem (Massey, 1960).** Let *M*ⁿ be a closed smooth *n*-manifold. Let α(*n*) be the number of ones in the binary expansion of *n*. Then the Stiefel–Whitney classes of the stable normal bundle satisfy:
>
> w̄ᵢ(*M*ⁿ) = 0 for all *i* > *n* − α(*n*).

In other words, the Stiefel–Whitney classes of the stable normal bundle vanish above degree *n* − α(*n*). This is a consequence of Wu's formulas and the structure of the Steenrod algebra.

**Why does this matter?** If *M*ⁿ immerses in **R**ᵈ, then the normal bundle has rank *d* − *n*, so the normal bundle is a (*d* − *n*)-dimensional real vector bundle. A vector bundle of rank *k* has w̄ᵢ = 0 for all *i* > *k* (the Stiefel–Whitney classes vanish above the rank). Therefore, an immersion into **R**ᵈ implies:

w̄ᵢ(*M*ⁿ) = 0 for all *i* > *d* − *n*.

Combining with Massey's vanishing, this means that if *d* = 2*n* − α(*n*), then *d* − *n* = *n* − α(*n*), and the Stiefel–Whitney class obstruction vanishes exactly at that dimension. Hence **the only possible Stiefel–Whitney class obstruction to immersing in **R**²ⁿ⁻ᵅ⁽ⁿ⁾ disappears**.

---

## 3. The Conjecture

Massey then showed the bound is sharp:

> **Theorem (Massey).** For every *n*, there exists a closed *n*-manifold that does **not** immerse in **R**²ⁿ⁻ᵅ⁽ⁿ⁾⁻¹.

The extremal examples are products of real projective spaces of the form **R**P²ⁱ¹ × ⋯ × **R**P²ⁱʳ, where the sum of the 2-powers 2ⁱᵏ equals *n*. For these manifolds, the Stiefel–Whitney class w̄²ⁱʳ is non-zero, providing an obstruction to immersing in **R**²ⁿ⁻ᵅ⁽ⁿ⁾⁻¹.

This led to the natural conjecture:

> **Massey's Immersion Conjecture.** Every closed smooth *n*-manifold immerses in **R**²ⁿ⁻ᵅ⁽ⁿ⁾.

In other words, the Stiefel–Whitney class obstruction is the **only** obstruction.

---

## 4. What α(*n*) Means in Practice

Let me make the conjecture concrete with examples:

| *n* | Binary | α(*n*) | 2*n* − α(*n*) |
|---|---|---|---|
| 1 | 1 | 1 | 1 |
| 2 | 10 | 1 | 3 |
| 3 | 11 | 2 | 4 |
| 4 | 100 | 1 | 7 |
| 5 | 101 | 2 | 8 |
| 6 | 110 | 2 | 10 |
| 7 | 111 | 3 | 11 |
| 8 | 1000 | 1 | 15 |

So the conjecture says:
- Every closed 2-manifold immerses in **R**³ (true: the Klein bottle and **R**P² do, and surfaces in **R**³ are well known).
- Every closed 4-manifold immerses in **R**⁷.
- Every closed 8-manifold immerses in **R**¹⁵.

Compare this with Whitney's bound of **R**²ⁿ — the improvement is dramatic, especially for powers of 2, where α(2ᵏ) = 1, so 2·2ᵏ − 1 = 2ᵏ⁺¹ − 1 instead of 2·2ᵏ = 2ᵏ⁺¹.

---

## 5. The Road to the Proof

Before Cohen, significant progress had been made:

- **R. Brown (1960s)**: Proved the conjecture "up to cobordism" — every closed *n*-manifold is cobordant to one that immerses in **R**²ⁿ⁻ᵅ⁽ⁿ⁾. This used Thom's cobordism theorem and the structure of the unoriented cobordism ring.
- **Brown–Peterson (1960s–70s)**: Developed a program using the Brown–Peterson spectrum BP and its associated homology to study the obstruction theory of immersions. They reduced the conjecture to understanding the homotopy type of certain classifying spaces, specifically the spaces BO/*I*ₙ (where *I*ₙ encodes the immersion condition) and BO(*n* − α(*n*)).
- **Peterson**: Made significant contributions to understanding the algebraic topology of these spaces.

The key reduction was: the immersion problem translates to a homotopy-lifting problem for maps from *M* into the classifying space BO. Specifically, *M* immerses in **R**ᵈ iff the stable normal bundle map *M* → BO factors through BO(*d* − *n*). The question becomes: does every map *M* → BO (coming from a manifold) factor through BO(*n* − α(*n*))?

---

## 6. Cohen's 1985 Proof

**Ralph L. Cohen** proved the conjecture in his 92-page paper:

> **Cohen, Ralph L.** "The immersion conjecture for differentiable manifolds." *Annals of Mathematics* 122 (1985), no. 2, 237–328.

The proof is highly technical and uses deep tools from algebraic topology, including:

1. **Surgery theory**: Cohen uses surgery to modify a given manifold within its cobordism class so that the normal bundle becomes simpler, while preserving the property of being a closed *n*-manifold.

2. **Brown–Peterson homology (BP\*)**: The Brown–Peterson spectrum provides a refined homology theory that captures the essential p-local information (particularly at *p* = 2, where Stiefel–Whitney classes live). The structure of BP\*(BO) and its relation to the Steenrod algebra is central.

3. **The structure of the classifying spaces**: Cohen analyzes the homotopy types of the spaces BO(*n* − α(*n*)) and the relative spaces BO/BO(*n* − α(*n*)) using the Brown–Peterson spectral sequence and related tools.

4. **Obstruction theory**: The core of the proof is showing that all obstructions to lifting a map *M* → BO to BO(*n* − α(*n*)) vanish, not just the Stiefel–Whitney class obstructions but all higher homotopy-theoretic obstructions. The vanishing of the Stiefel–Whitney classes (Massey's theorem) eliminates the primary obstructions, and Cohen's work shows that there are no hidden higher obstructions.

5. **Cobordism arguments**: Following Brown's approach, Cohen works within cobordism classes and uses surgery to move between manifolds in the same class, simplifying the normal bundle step by step.

The overall strategy can be summarized as:
- Start with an arbitrary closed *n*-manifold *M*.
- Use Massey's vanishing to know the primary obstructions (Stiefel–Whitney classes) are gone.
- Use surgery within the cobordism class to simplify the normal bundle.
- Use the deep structure of BP\*(BO) and the Brown–Peterson spectral sequence to show all higher obstructions also vanish.
- Conclude that the normal bundle classifies into BO(*n* − α(*n*)), which means *M* immerses in **R**²ⁿ⁻ᵅ⁽ⁿ⁾.

---

## 7. Significance

The proof is considered one of the major achievements in differential topology of the 20th century because:

- It resolved a problem that had been open for 25 years.
- It confirmed that the Stiefel–Whitney class obstruction is the **only** obstruction to immersion — a clean and deep structural result.
- The techniques (especially the use of BP-homology and surgery in this context) had broad implications for the study of immersions and embeddings more generally.
- The bound 2*n* − α(*n*) is **sharp** for infinitely many *n* (whenever *n* is a sum of distinct powers of 2, which is every *n* by binary representation).

---

## 8. A Note on Embedding

The corresponding **embedding** question is different. The sharp embedding dimension is generally larger than the immersion dimension, and the embedding problem involves more subtle obstructions (including the van Kampen obstruction). Cohen's result is specifically about immersions.
