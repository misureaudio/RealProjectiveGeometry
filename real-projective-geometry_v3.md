# Real Projective Geometry: From the Cross-Ratio to the Erlangen Program and Beyond

## Abstract

Real projective geometry occupies a central position at the intersection of linear algebra, topology, algebraic geometry, and applied mathematics. This essay surveys the foundations of real projective spaces — their construction as quotient manifolds, the classical theorems of incidence geometry (Desargues, Pappus), the cross-ratio as the fundamental projective invariant, and the Fundamental Theorem of Projective Geometry identifying $\mathrm{PGL}(n+1,\mathbb{R})$ as the full collineation group. Klein's Erlangen program is then presented as the unifying framework that positions projective geometry as the ambient context for all classical geometries. We develop the differential-geometric viewpoint (constant-curvature metric, geodesics, projective connections), projective algebraic geometry (homogeneous ideals, Bézout's theorem), and the topology of $\mathbb{R}\mathrm{P}^n$ (cohomology, Stiefel–Whitney classes, embedding obstructions). The final section emphasizes applications: computer vision and multiple-view geometry, where projective structure is the intrinsic geometry of perspective imaging; convex optimization and convex algebraic geometry; robot kinematics via projective geometric algebra; and quantum control theory, where the projective Hilbert space carries the Fubini–Study metric.

---

## 1. Foundations

### 1.1. Construction and Basic Properties

Let $\mathbb{R}^{n+1} \setminus \{0\}$ carry the equivalence relation $v \sim \lambda v$ for all $\lambda \in \mathbb{R} \setminus \{0\}$. The quotient space

$$\mathbb{R}\mathrm{P}^n = \left(\mathbb{R}^{n+1} \setminus \{0\}\right) / \sim$$

is the *real projective $n$-space*. Its points — *projective points* — are one-dimensional subspaces of $\mathbb{R}^{n+1}$. Homogeneous coordinates $[x_0 : x_1 : \cdots : x_n]$ represent the equivalence class of $(x_0, \ldots, x_n)$, and the projective linear group

$$\mathrm{PGL}(n+1,\mathbb{R}) = \mathrm{GL}(n+1,\mathbb{R}) / \mathbb{R}^\times I$$

acts transitively on $\mathbb{R}\mathrm{P}^n$. Every $A \in \mathrm{GL}(n+1,\mathbb{R})$ induces a projective transformation $[A] : \mathbb{R}\mathrm{P}^n \to \mathbb{R}\mathrm{P}^n$ by $[x] \mapsto [Ax]$.

The standard smooth structure arises from the atlas $\{U_i\}_{i=0}^n$ where $U_i = \{[x] : x_i \neq 0\}$ and the chart $\phi_i : U_i \to \mathbb{R}^n$ is given by

$$\phi_i([x_0 : \cdots : x_n]) = \left(\frac{x_0}{x_i}, \ldots, \widehat{\frac{x_i}{x_i}}, \ldots, \frac{x_n}{x_i}\right).$$

The transition functions $\phi_j \circ \phi_i^{-1}$ are rational maps with non-vanishing denominators on their domains, hence smooth. Thus $\mathbb{R}\mathrm{P}^n$ is a smooth $n$-dimensional compact manifold without boundary.

The canonical double covering

$$\pi : S^n \to \mathbb{R}\mathrm{P}^n, \quad x \mapsto [x]$$

identifies antipodal points and makes $\mathbb{R}\mathrm{P}^n$ the quotient of $S^n$ by the free action of $\mathbb{Z}_2$. This covering is a Riemannian covering when $S^n$ carries the round metric, endowing $\mathbb{R}\mathrm{P}^n$ with the unique metric of constant sectional curvature $+1$.

### 1.2. Duality and Incidence

Projective duality is the most striking departure from affine and Euclidean geometry. The dual projective space $(\mathbb{R}\mathrm{P}^n)^*$ is the space of hyperplanes in $\mathbb{R}\mathrm{P}^n$, which are precisely the images of linear hyperplanes in $\mathbb{R}^{n+1}$. A hyperplane $H \subset \mathbb{R}\mathrm{P}^n$ corresponds to a nonzero linear functional $\ell \in (\mathbb{R}^{n+1})^* \setminus \{0\}$ up to scale, so $(\mathbb{R}\mathrm{P}^n)^* \cong \mathbb{R}\mathrm{P}^n$ canonically. The incidence relation $p \in H$ is symmetric: $p \in H$ in $\mathbb{R}\mathrm{P}^n$ if and only if $H \in p$ in $(\mathbb{R}\mathrm{P}^n)^*$.

In $\mathbb{R}\mathrm{P}^2$, this yields the celebrated duality between points and lines: any theorem about points and lines remains valid when "point" and "line" are interchanged and "incidence" is preserved. In general dimension, duality interchanges $k$-flats and $(n-2-k)$-flats in $\mathbb{R}\mathrm{P}^n$, which is equivalent to the linear-algebraic fact that the annihilator of a $k$-dimensional subspace of $\mathbb{R}^{n+1}$ has codimension $k$.

### 1.3. Grassmannians

The Grassmannian $\mathrm{Gr}(k, n+1)$ parametrizes $k$-dimensional subspaces of $\mathbb{R}^{n+1}$. Projective space is the case $k=1$: $\mathrm{Gr}(1, n+1) = \mathbb{R}\mathrm{P}^n$. The Plücker embedding

$$\mathrm{Gr}(k, n+1) \hookrightarrow \mathbb{R}\mathrm{P}^{\binom{n+1}{k}-1}$$

sends a $k$-plane $W = \mathrm{span}(v_1, \ldots, v_k)$ to the line in $\Lambda^k \mathbb{R}^{n+1}$ spanned by the decomposable $k$-vector $v_1 \wedge \cdots \wedge v_k$. The image is cut out by the Plücker relations — quadratic equations characterizing decomposable $k$-vectors — making $\mathrm{Gr}(k, n+1)$ a smooth projective algebraic variety.

The Grassmannians carry a transitive action of $\mathrm{GL}(n+1,\mathbb{R})$, and the isotropy at a $k$-plane $W_0$ is the parabolic subgroup preserving $W_0$. Thus $\mathrm{Gr}(k, n+1) \cong \mathrm{GL}(n+1,\mathbb{R}) / P_k$, a homogeneous space. More generally, flag manifolds $\mathrm{Fl}(k_1, \ldots, k_m; n+1)$ are also projective varieties with transitive $\mathrm{PGL}$-actions.

---

## 2. Classical Projective Geometry

### 2.1. Incidence Axioms and the Projective Plane

The synthetic foundations of projective geometry are built on incidence axioms. A *projective plane* is a set of points and a set of lines satisfying:

> **(I1)** Any two distinct points lie on exactly one line.
> **(I2)** Any two distinct lines meet in exactly one point.
> **(I3)** There exist four points, no three of which are collinear (the *non-degeneracy axiom*).

Axiom (I2) is the dramatic departure from Euclidean geometry: in $\mathbb{R}\mathrm{P}^2$, *there are no parallel lines*. Every pair of lines intersects. This is the price of compactification — the point at infinity that Euclidean geometry adds to each family of parallel lines becomes a single line, the *line at infinity*, and every line meets it in exactly one point.

From these axioms one derives the *Principle of Duality*: every theorem remains valid when "point" and "line" are interchanged. This is not an accident but a structural feature, reflecting the identification $(\mathbb{R}\mathrm{P}^2)^* \cong \mathbb{R}\mathrm{P}^2$.

### 2.2. The Cross-Ratio

The cross-ratio is the fundamental projective invariant — the single scalar that characterizes the relative position of four collinear points up to projective transformation.

Let $A, B, C, D$ be four distinct points on a projective line $\mathbb{R}\mathrm{P}^1$. Choose homogeneous coordinates so that $A = [1:0]$, $B = [0:1]$, $C = [1:1]$, and $D = [1:\lambda]$. The *cross-ratio* is defined as

$$(A, B; C, D) = \lambda.$$

Equivalently, if $a, b, c, d \in \mathbb{R} \cup \{\infty\}$ are the affine coordinates of the four points (obtained by choosing an affine chart), then

$$(A, B; C, D) = \frac{(c - a)(d - b)}{(c - b)(d - a)},$$

with the standard convention for handling $\infty$.

#### Invariance and Characterization

A key structural fact: **three distinct points of $\mathbb{R}\mathrm{P}^1$ can be sent to any other three distinct points by a unique projectivity**. This is the projective analogue of the Euclidean fact that three non-collinear points determine a unique isometry. The proof is immediate in homogeneous coordinates: given $A, B, C$ and $A', B', C'$, choose coordinates so that $A=[1:0]$, $B=[0:1]$, $C=[1:1]$ and $A'=[1:0]$, $B'=[0:1]$, $C'=[1:1]$; the identity map in these coordinates is the unique projectivity sending the first triple to the second.

The cross-ratio is the *residual invariant* after fixing three points. Once $A, B, C$ are fixed, the fourth point $D$ is determined up to the cross-ratio $(A,B;C,D) \in \mathbb{R} \setminus \{0,1\}$. In this sense, the cross-ratio measures the "position" of $D$ relative to the projective frame $\{A,B,C\}$, and its invariance under projective transformations reflects the fact that projective transformations are completely determined by their action on three points.

The cross-ratio is invariant under projective transformations: for any $T \in \mathrm{PGL}(2,\mathbb{R})$,

$$(A, B; C, D) = (T(A), T(B); T(C), T(D)).$$

Conversely, the cross-ratio *completely characterizes* projective transformations of $\mathbb{R}\mathrm{P}^1$: a bijection $f : \mathbb{R}\mathrm{P}^1 \to \mathbb{R}\mathrm{P}^1$ is a projective transformation if and only if it preserves cross-ratios. This is the *Fundamental Theorem of Projective Geometry for $\mathbb{R}\mathrm{P}^1$*.

The cross-ratio takes all real values except $0, 1, \infty$ as $D$ varies while $A, B, C$ are fixed. The six possible values obtained by permuting the four points are

$$(A,B;C,D), \quad (A,B;C,D)^{-1}, \quad 1 - (A,B;C,D), \quad \frac{1}{1-(A,B;C,D)}, \quad \frac{(A,B;C,D)-1}{(A,B;C,D)},$$
$$ \quad \frac{(A,B;C,D)}{(A,B;C,D)-1},$$

forming an orbit of size 6 under the quotient $S_4 / V_4 \cong S_3$ (the *anharmonic group*). The Klein four-group $V_4 \subset S_4$ is precisely the subgroup that *fixes* the cross-ratio — it acts trivially on the six values.

#### Harmonic Conjugates

Four points $A, B, C, D$ are in *harmonic position* (or form a *harmonic range*) if

$$(A, B; C, D) = -1.$$

In this case, $D$ is the *harmonic conjugate* of $C$ with respect to $A$ and $B$. Harmonic conjugates appear naturally in the complete quadrangle: given four points in general position in $\mathbb{R}\mathrm{P}^2$, the intersections of the diagonals with the sides are harmonic conjugates. This construction — the *harmonic construction* — shows that harmonic conjugacy is a projective concept requiring no metric structure.

### 2.3. Projective Transformations and Normal Forms

A projectivity of $\mathbb{R}\mathrm{P}^n$ is represented by a matrix in $\mathrm{PGL}(n+1,\mathbb{R})$ — an $(n+1) \times (n+1)$ invertible matrix up to scalar. The classification of projectivities reduces to the classification of matrices up to conjugation in $\mathrm{GL}(n+1,\mathbb{R})$ and scalar multiplication.

#### Classification in $\mathbb{R}\mathrm{P}^1$

In dimension 1, projectivities of $\mathbb{R}\mathrm{P}^1$ are represented by $2 \times 2$ matrices up to scalar, and they fall into three types determined by the eigenvalues of a representative matrix:

| Type | Eigenvalues | Fixed points | Geometric description |
|------|-------------|--------------|----------------------|
| **Elliptic** | Complex conjugate pair | No real fixed points | Rotation on $\mathbb{R}\mathrm{P}^1 \cong S^1$ |
| **Parabolic** | Equal real eigenvalues (Jordan block) | One fixed point (double) | Translation fixing the point at infinity |
| **Hyperbolic** | Distinct real eigenvalues | Two fixed points | Dilation expanding one direction, contracting the other |

This classification is intimately related to the Möbius transformation classification. Identifying $\mathbb{R}\mathrm{P}^1$ with the extended real line $\mathbb{R} \cup \{\infty\}$, projectivities are precisely the Möbius transformations

$$x \mapsto \frac{ax + b}{cx + d}, \quad ad - bc \neq 0,$$

and the three types correspond to the usual classification of Möbius transformations by their fixed points.

The cross-ratio provides the normal form for hyperbolic transformations: if $A$ and $B$ are the two fixed points, then for any $x$, the cross-ratio $(A, B; x, T(x))$ is a constant independent of $x$ — the *multiplier* of $T$. This constant is the ratio of the eigenvalues of the representing matrix.

#### Fixed Points and Normal Forms in Higher Dimension

In $\mathbb{R}\mathrm{P}^n$, a projectivity $[A]$ has fixed points corresponding to the eigenspaces of $A$. The Jordan normal form of $A$ determines the local behavior near fixed points. A projectivity is *unipotent* (all eigenvalues equal) if and only if it is a product of transvections — projectivities fixing a hyperplane pointwise and a point outside that hyperplane.

The cross-ratio generalizes to higher dimensions through the concept of *projective invariants of configurations*: any projectively invariant function of a finite set of points is a rational function of the cross-ratios of points on lines connecting them. This is the content of the *First Fundamental Theorem of Projective Invariants*.

### 2.4. Projectivities and the Fundamental Theorem

A *projectivity* of $\mathbb{R}\mathrm{P}^n$ is a bijection $f : \mathbb{R}\mathrm{P}^n \to \mathbb{R}\mathrm{P}^n$ induced by an element of $\mathrm{PGL}(n+1,\mathbb{R})$. A *collineation* is a bijection that maps lines to lines (preserving incidence). The profound question: are all collineations projectivities?

> **Fundamental Theorem of Projective Geometry.** Every collineation of $\mathbb{R}\mathrm{P}^n$ ($n \geq 2$) is a projectivity. Equivalently,
> $$\mathrm{Aut}(\mathbb{R}\mathrm{P}^n) \cong \mathrm{PGL}(n+1,\mathbb{R}).$$

The standard proof proceeds by coordinate reconstruction. Choose a projective basis $E_0, \ldots, E_n, E$ in $\mathbb{R}\mathrm{P}^n$ — $n+2$ points in general position (no $n+1$ of which lie on a hyperplane). Every point $P$ has unique homogeneous coordinates $[x_0 : \cdots : x_n]$ determined by intersecting lines through $P$ with the coordinate hyperplanes. A collineation $f$ maps this basis to another projective basis $f(E_0), \ldots, f(E_n), f(E)$. There is a unique linear map $A \in \mathrm{GL}(n+1,\mathbb{R})$ sending the first basis to the second, and the induced projectivity $[A]$ agrees with $f$ on the basis. Since both $f$ and $[A]$ preserve incidence, they agree on all points: any point $P$ is the intersection of lines determined by basis points, and the image under $f$ is the intersection of the corresponding image lines — which is exactly $[A](P)$. Thus $f = [A]$.

For fields other than $\mathbb{R}$, the Fundamental Theorem states that every collineation is induced by a *semilinear* transformation — a composition of a linear map and a field automorphism. Since $\mathbb{R}$ has no non-trivial field automorphisms, the real case is particularly clean.

### 2.5. Desargues' Theorem

> **Desargues' Theorem.** Let two triangles $ABC$ and $A'B'C'$ in $\mathbb{R}\mathrm{P}^2$ be perspective from a point $O$ (meaning $AA'$, $BB'$, $CC'$ are concurrent at $O$). Then the intersections of corresponding sides — $AB \cap A'B'$, $BC \cap B'C'$, and $CA \cap C'A'$ — are collinear (lying on the *axis of perspectivity*).

Desargues' theorem is a theorem *about* $\mathbb{R}\mathrm{P}^2$ but it is *not* a theorem of the abstract incidence axioms (I1)–(I3). There exist projective planes satisfying (I1)–(I3) in which Desargues' theorem fails (the non-Desarguesian planes). A projective plane is Desarguesian if and only if it is isomorphic to $\mathbb{F}\mathrm{P}^2$ for some *division ring* $\mathbb{F}$. This is the deep structural content of Desargues' theorem: it characterizes exactly those projective planes that admit a coordinatization by a division ring, and hence by a field when commutativity is also assumed. For $\mathbb{F} = \mathbb{R}$ we obtain $\mathbb{R}\mathrm{P}^2$. The proof for $\mathbb{R}\mathrm{P}^2$ uses the underlying vector space: the concurrency condition at $O$ translates to a linear-algebraic relation among the homogeneous coordinate vectors, and the collinearity of the intersections follows by computing determinants.

### 2.6. Pappus' Theorem

> **Pappus' Theorem.** Let $A, B, C$ be three points on one line and $A', B', C'$ be three points on another line in $\mathbb{R}\mathrm{P}^2$. Then the three intersection points
> $$AB' \cap A'B, \quad BC' \cap B'C, \quad CA' \cap C'A$$
> are collinear.

Pappus' theorem is stronger than Desargues' theorem: a projective plane satisfying Pappus' theorem is isomorphic to $\mathbb{F}\mathrm{P}^2$ for a *commutative field* $\mathbb{F}$. Since Desargues' theorem holds in $\mathbb{F}\mathrm{P}^2$ for any division ring (commutative or not), Pappus implies Desargues but not conversely. The conceptual significance is sharp: Desargues characterizes coordinatization by division rings, while Pappus characterizes the *commutativity* of the coordinate field. This is one of the deepest results in classical projective geometry — it shows that the algebraic structure of the underlying field is encoded in the incidence geometry of the projective plane.

The proof for $\mathbb{R}\mathrm{P}^2$ is again a computation with homogeneous coordinates. The theorem is dual to itself under the point-line duality of $\mathbb{R}\mathrm{P}^2$.

### 2.7. Projective Coordinates and Synthetic Construction

The projective coordinate system emerges naturally from the incidence structure. Given $n+2$ points in general position (a *projective basis* $E_0, \ldots, E_n, E$), every point $P \in \mathbb{R}\mathrm{P}^n$ has unique homogeneous coordinates $[x_0 : \cdots : x_n]$ determined by the cross-ratios of the points obtained by intersecting lines through $P$ with the coordinate axes. This shows that the coordinate system is not an external imposition but is *synthetically determined* by the incidence geometry.

---

## 3. Klein's Erlangen Program and the Unifying Role of Projective Geometry

### 3.1. The Erlangen Program

Klein's 1872 *Vergleichende Betrachtungen über neuere geometrische Forschungen* proposed that a geometry is characterized by its symmetry group $G$ acting on a space $X$. The fundamental insight: Euclidean, affine, and projective geometries are *not* fundamentally different subjects but rather *different choices* of symmetry group within the same ambient projective framework.

Let $X = \mathbb{R}\mathrm{P}^n$. Then:

| Geometry | Space $X$ | Group $G$ | Invariants |
|----------|-----------|-----------|------------|
| Projective | $\mathbb{R}\mathrm{P}^n$ | $\mathrm{PGL}(n+1,\mathbb{R})$ | Cross-ratio, incidence, collinearity |
| Affine | $\mathbb{R}^n \subset \mathbb{R}\mathrm{P}^n$ | Affine group $A(n,\mathbb{R})$ | Parallelism, ratios of lengths on parallel lines |
| Euclidean | $\mathbb{R}^n$ | $\mathrm{Euc}(n) = \mathbb{R}^n \rtimes O(n)$ | Lengths, angles, circles |
| Conformal | $\mathbb{R}^n$ | Möbius group | Angles (conformal class) |

The inclusion chain

$$\mathrm{Euc}(n) \subset \mathrm{CO}(n) \subset A(n,\mathbb{R}) \subset \mathrm{PGL}(n+1,\mathbb{R})$$

expresses that projective geometry is the *most general* classical geometry. Euclidean geometry is what remains when one fixes a hyperplane at infinity (passing from projective to affine) and a conic at infinity (passing from affine to Euclidean). The conic at infinity is the *absolute* — its stabilizer in $\mathrm{PGL}(n+1,\mathbb{R})$ is the Euclidean group.

### 3.2. The Absolute Conic and Cayley–Klein Distance

In $\mathbb{R}\mathrm{P}^2$, fix a non-degenerate conic $\Omega$ (the *absolute*). The distance between two points $P, Q$ is defined projectively as

$$d(P,Q) = \frac{1}{2\sqrt{\kappa}} \log (A, B; P, Q),$$

where $A, B$ are the intersection points of the line $PQ$ with $\Omega$, $(\cdot,\cdot;\cdot,\cdot)$ is the cross-ratio, and $\kappa$ is a constant depending on the signature of $\Omega$. This is the *Cayley–Klein distance*. Depending on whether $\Omega$ is real, imaginary, or degenerate, one recovers hyperbolic, Euclidean, or elliptic geometry. In the Euclidean case, $\Omega$ is the imaginary conic $x^2 + y^2 = 0$ at infinity, and the distance formula reduces to the familiar expression via the logarithm of the cross-ratio.

This construction is profound: it shows that metric properties — distances and angles — are *projective invariants* of a configuration involving a distinguished conic. There is no need to introduce metric structure as an independent axiom; it emerges from projective structure plus a choice of absolute.

### 3.3. Modern Formulation: Homogeneous Spaces

In modern language, Klein's program says: a geometry is a pair $(G, H)$ where $G$ is a Lie group and $H$ is a closed subgroup, and the space is the homogeneous space $G/H$. Projective geometry corresponds to $(\mathrm{PGL}(n+1,\mathbb{R}), P)$ where $P$ is a maximal parabolic subgroup. The Erlangen perspective has been generalized in Thurston's geometrization program, Cartan's theory of connections, and Cartan geometry.

---

## 4. Projective Algebraic Geometry

### 4.1. Homogeneous Ideals and Projective Varieties

A polynomial $F \in \mathbb{R}[x_0, \ldots, x_n]$ is *homogeneous* of degree $d$ if $F(\lambda x) = \lambda^d F(x)$ for all $\lambda \in \mathbb{R}$. A homogeneous polynomial defines a well-defined subset of $\mathbb{R}\mathrm{P}^n$ — its *zero set*:

$$Z(F) = \{[x] \in \mathbb{R}\mathrm{P}^n : F(x) = 0\}.$$

A *projective algebraic variety* is the zero set of a homogeneous ideal $I \subset \mathbb{R}[x_0, \ldots, x_n]$. The passage between affine and projective varieties is governed by *homogenization* and *dehomogenization*: an affine polynomial $f(x_1, \ldots, x_n)$ of degree $d$ homogenizes to $F(x_0, \ldots, x_n) = x_0^d f(x_1/x_0, \ldots, x_n/x_0)$, and dehomogenization sets $x_0 = 1$.

Projective space *compactifies* affine algebraic geometry: every affine variety has a projective closure, obtained by homogenizing its defining equations. For example, the affine parabola $y = x^2$ compactifies to the projective curve $Y X_0 = X^2$ in $\mathbb{R}\mathrm{P}^2$, adding the point $[0:1:0]$ at infinity.

### 4.2. Bézout's Theorem

One of the most fundamental results in projective algebraic geometry:

> **Bézout's Theorem.** Let $F$ and $G$ be homogeneous polynomials of degrees $d$ and $e$ in $\mathbb{C}[x_0, \ldots, x_n]$ with no common component. Then the number of intersection points of $Z(F)$ and $Z(G)$ in $\mathbb{C}\mathrm{P}^n$, counted with multiplicity, is exactly $d \cdot e$.

The passage to $\mathbb{C}\mathrm{P}^n$ is essential: over $\mathbb{R}$, real intersection points may be fewer than $d \cdot e$ (some are complex). The theorem fails in affine space — the lines $y = 0$ and $y = 1$ do not intersect — but holds in projective space where they meet at $[1:0:0]$ on the line at infinity. This is the quintessential example of why projective compactification is not merely a technical device but a conceptual necessity.

### 4.3. Connections to Applications

The study of projective varieties is the language of *algebraic vision* (Kileel and Kohn, 2022): the epipolar variety, trifocal tensors, and minimal problems in 3D reconstruction are all described by homogeneous equations on projective varieties, with Gröbner bases and numerical algebraic geometry providing the computational tools.

---

## 5. Differential Geometry of $\mathbb{R}\mathrm{P}^n$

### 5.1. The Constant-Curvature Metric

The double covering $\pi : S^n \to \mathbb{R}\mathrm{P}^n$ is a Riemannian covering for the round metric on $S^n$, inducing on $\mathbb{R}\mathrm{P}^n$ the unique metric of constant sectional curvature $+1$. The diameter of $\mathbb{R}\mathrm{P}^n$ in this metric is $\pi/2$ (half that of $S^n$), since antipodal points on $S^n$ project to the same point.

Geodesics in $\mathbb{R}\mathrm{P}^n$ are the projections of great circles on $S^n$. Each geodesic is a closed curve of length $\pi$. In $\mathbb{R}\mathrm{P}^2$, two distinct geodesics intersect in exactly one point — the projective analogue of the Euclidean axiom that two distinct lines intersect in exactly one point. In higher dimensions this fails: two generic geodesics in $\mathbb{R}\mathrm{P}^n$ ($n \geq 3$) do not intersect, reflecting the need for Grassmannians and flats of controlled dimension to guarantee intersections.

### 5.2. Projective Connections and Geodesic Equivalence

Projective geometry can be viewed not only as incidence geometry but also as the geometry of *unparameterized geodesics*. A *projective connection* on a manifold is a connection whose geodesics are preserved — not the connection itself but its unparameterized geodesics. Two metrics are *projectively equivalent* if they share the same unparameterized geodesics.

Cartan developed the theory of projective connections systematically: the space of all projective connections on $\mathbb{R}\mathrm{P}^n$ can be identified with sections of a certain bundle associated to the parabolic subgroup $P \subset \mathrm{PGL}(n+1,\mathbb{R})$. The standard projective connection on $\mathbb{R}\mathrm{P}^n$ corresponds to the flat connection induced by the inclusion $P \subset \mathrm{PGL}(n+1,\mathbb{R})$.

This is the differential-geometric counterpart of Klein's program: projective connections are the natural connections associated to the geometry of $\mathrm{PGL}(n+1,\mathbb{R})$-homogeneous spaces, and the flat projective connection on $\mathbb{R}\mathrm{P}^n$ is the model for all others.

---

## 6. Topology of Real Projective Spaces

### 6.1. Fundamental Group and Universal Cover

From the double covering $\pi : S^n \to \mathbb{R}\mathrm{P}^n$ with $n \geq 2$, standard covering space theory yields

$$\pi_1(\mathbb{R}\mathrm{P}^n) \cong \mathbb{Z}_2, \quad \pi_k(\mathbb{R}\mathrm{P}^n) \cong \pi_k(S^n) \text{ for } k \geq 2.$$

For $n=1$, $\mathbb{R}\mathrm{P}^1 \cong S^1$, so $\pi_1(\mathbb{R}\mathrm{P}^1) \cong \mathbb{Z}$. The distinction at $n=1$ is the only exception in the homotopy type.

### 6.2. Cohomology and Stiefel–Whitney Classes

The cohomology ring with $\mathbb{Z}_2$-coefficients is one of the most elementary and important computations in algebraic topology. Let $a \in H^1(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2)$ be the generator. Then

$$H^*(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2) \cong \mathbb{Z}_2[a] / (a^{n+1}),$$

with $a$ of degree 1. With integer coefficients,

$$H^k(\mathbb{R}\mathrm{P}^n; \mathbb{Z}) = \begin{cases} \mathbb{Z} & k = 0, \\ \mathbb{Z}_2 & k \text{ odd}, 0 < k < n, \\ \mathbb{Z} & k = n \text{ and } n \text{ odd}, \\ 0 & \text{otherwise}. \end{cases}$$

The tangent bundle $T\mathbb{R}\mathrm{P}^n$ is not the quotient of the trivial bundle by the tautological line bundle — rather, it is the bundle of homomorphisms from the tautological line bundle to its quotient. Let $\gamma^1$ be the tautological line bundle and $Q$ the quotient bundle, fitting into the short exact sequence

$$0 \to \gamma^1 \to \underline{\mathbb{R}}^{n+1} \to Q \to 0.$$

Then

$$T\mathbb{R}\mathrm{P}^n \cong \operatorname{Hom}(\gamma^1, Q) \cong (\gamma^1)^* \otimes Q.$$

Equivalently, one has the Euler sequence

$$0 \to \mathcal{O} \to \mathcal{O}(1)^{\oplus(n+1)} \to T\mathbb{R}\mathrm{P}^n \to 0,$$

or in bundle-theoretic notation,

$$T\mathbb{R}\mathrm{P}^n \oplus \mathbf{1} \cong (n+1)\gamma^1{}^*.$$

Since $(\gamma^1)^*$ has $w_1 = a$, the total Stiefel–Whitney class is

$$w(\mathbb{R}\mathrm{P}^n) = (1+a)^{n+1} \in H^*(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2).$$

This implies $\mathbb{R}\mathrm{P}^n$ is orientable if and only if $n$ is odd (since $w_1 = (n+1)a \neq 0$ when $n$ is even). The non-orientability of $\mathbb{R}\mathrm{P}^2$ is the origin of the Möbius strip and Klein bottle constructions.

### 6.3. Embedding and Immersion Results

A central question — when does $\mathbb{R}\mathrm{P}^n$ embed in $\mathbb{R}^N$? — connects projective geometry to topology and algebra. The Wu formulas and Stiefel–Whitney class obstructions show that $\mathbb{R}\mathrm{P}^n$ embeds in $\mathbb{R}^{2n}$ for all $n$. For immersions, Massey's conjecture — proved by Ralph Cohen (1985) — states that $\mathbb{R}\mathrm{P}^n$ immerses in $\mathbb{R}^{2n - \alpha(n)}$, where $\alpha(n)$ is the number of 1's in the binary expansion of $n$. The corresponding embedding conjecture would give $\mathbb{R}^{2n - \alpha(n) + 1}$, but this remains open in general. Notably:

- $\mathbb{R}\mathrm{P}^1 \cong S^1 \hookrightarrow \mathbb{R}^2$ (embedding),
- $\mathbb{R}\mathrm{P}^2 \hookrightarrow \mathbb{R}^4$ (embedding), and immerses in $\mathbb{R}^3$ (Boy's surface),
- $\mathbb{R}\mathrm{P}^3 \hookrightarrow \mathbb{R}^5$ (embedding), and immerses in $\mathbb{R}^4$,
- $\mathbb{R}\mathrm{P}^n$ immerses in $\mathbb{R}^{2n - \alpha(n)}$ (Cohen, 1985).

The immersion and embedding dimension problems are intimately related to the vector field problem on spheres and to Hopf invariant one elements — a connection that ties projective topology to algebraic $K$-theory and stable homotopy.

---

## 7. Applications

### 7.1. Computer Vision and Multiple-View Geometry

The most extensive application of real projective geometry to engineering is computer vision, where the geometry of perspective imaging is *inherently* projective. Hartley and Zisserman's *Multiple View Geometry in Computer Vision* (2004) is the definitive reference.

#### 7.1.1. Camera Model

A pinhole camera is modeled as a linear projection

$$\mathbf{x} = P \mathbf{X},$$

where $\mathbf{X} \in \mathbb{R}^4$ is a point in $\mathbb{R}\mathrm{P}^3$ (homogeneous coordinates), $\mathbf{x} \in \mathbb{R}^3$ is a point in the image plane $\mathbb{R}\mathrm{P}^2$, and $P$ is a $3 \times 4$ matrix of rank 3 — the *camera matrix*. The kernel of $P$ is the camera center $C \in \mathbb{R}\mathrm{P}^3$. This model is projective: it makes no reference to metric structure. The matrix $P$ is determined only up to a non-zero scalar, reflecting the homogeneous nature of projective coordinates.

Decomposing $P$ as

$$P = K [R \mid t],$$

where $K$ is the $3 \times 3$ intrinsic calibration matrix (encoding focal length, principal point, and skew), $R \in SO(3)$ is a rotation, and $t \in \mathbb{R}^3$ is a translation, requires additional constraints that fix the Euclidean structure — the choice of an absolute conic. Without calibration, one works entirely in the projective category.

#### 7.1.2. Epipolar Geometry and the Fundamental Matrix

Given two views with camera matrices $P$ and $P'$, the *fundamental matrix* $F \in \mathbb{R}^{3 \times 3}$ satisfies

$$\mathbf{x}'^T F \mathbf{x} = 0$$

for corresponding points $\mathbf{x} \in \mathbb{R}\mathrm{P}^2$ and $\mathbf{x}' \in \mathbb{R}\mathrm{P}^2$. The matrix $F$ has rank 2 and is determined up to scale by 7 point correspondences (the *7-point algorithm*). Epipolar lines $\mathbf{l} = F\mathbf{x}$ and $\mathbf{l}' = F^T\mathbf{x}'$ arise from the duality discussed in §1.2: $F$ maps a point to a line, and by duality, a line to a point.

The epipoles $e$ and $e'$ are the null vectors of $F$ and $F^T$ respectively — they are the projections of the other camera center. The epipolar constraint is a *projective invariant*: it depends only on the incidence structure of points, lines, and the two camera centers.

#### 7.1.3. Projective Reconstruction

A landmark result: from two or more uncalibrated views, one can reconstruct the 3D scene *up to a projective transformation of $\mathbb{R}\mathrm{P}^3$*. This is *projective reconstruction*. To upgrade to affine or Euclidean reconstruction, one must impose constraints — vanishing points (for affine structure) or the dual of the absolute conic (for metric structure). The upgrade process is exactly the Erlangen program in action: progressively fixing subgroups of $\mathrm{PGL}(4,\mathbb{R})$.

#### 7.1.4. Algebraic Vision

Recent work has deepened the connection between projective geometry and algebraic geometry in computer vision. The survey by Kileel and Kohn (2022) introduces the term *algebraic vision* for this intersection. The *epipolar variety* — the set of all possible correspondences between points in multiple views — is a projective algebraic variety whose study uses tools from commutative algebra and algebraic geometry. Minimal problems in 3D reconstruction reduce to solving systems of polynomial equations on projective varieties, with solutions studied via Gröbner bases, resultant theory, and numerical algebraic geometry.

### 7.2. Convex Optimization and Convex Algebraic Geometry

Projective geometry interacts with convex optimization through several channels.

#### 7.2.1. Projective Representations of Convex Sets

A *projective representation* of a convex set $C \subset \mathbb{R}^n$ is a description of $C$ as the linear section of the projection of a spectrahedron (a set defined by a linear matrix inequality). This concept, developed by Gouveia, Parrilo, Thomas, and others, generalizes Lasserre's lift-and-project hierarchies. The *projective rank* of a convex set — the smallest dimension of a spectrahedron needed for a projective representation — is a fundamental complexity measure.

The connection to projective geometry is structural: the projection and intersection operations in the definition are precisely the projective operations of projecting from a center and taking hyperplane sections. The study of which convex sets admit low-dimensional projective representations connects to questions about the structure of convex algebraic varieties in projective space.

#### 7.2.2. Semidefinite Programming and Projective Cutting Planes

Porumbel (2023) formulates the projection subproblem in semidefinite programming as a projective operation, yielding efficient cutting-plane methods. The book by Gouveia, Parrilo, and Thomas (2022), *Semidefinite Optimization and Convex Algebraic Geometry*, systematically develops this viewpoint.

### 7.3. Projective Geometric Algebra and Robot Kinematics

Projective geometric algebra (PGA), developed by Hestenes and extended by Dorst, Fontijne, and Mann (2007), provides a unified algebraic framework for projective, Euclidean, and conformal geometry. PGA is the Clifford algebra $\mathrm{Cl}(3,0,1)$ — the geometric algebra on a 4-dimensional space with signature $(3,0,1)$, where the distinguished direction encodes the plane at infinity.

#### 7.3.1. Unified Representation

In PGA, points, lines, planes, and their duals are represented as multivectors. The meet ($\wedge$) and join ($\vee$) operations correspond to intersection and span. Rigid transformations — rotations and translations — are represented as versors (products of reflections), and their composition is simply versor multiplication. This eliminates the need for separate matrix representations (rotation matrices, translation vectors, homogeneous transformation matrices) and unifies the algebraic treatment.

#### 7.3.2. Robot Kinematics and Dynamics

Recent work by Sun and Ding (2023) on *high-order inverse dynamics of serial robots based on projective geometric algebra* demonstrates the practical power of this approach. The PGA formulation yields:

- **Coordinate invariance**: the formulas do not depend on a choice of coordinate frame, unlike the Denavit–Hartenberg parameterization which requires careful frame placement.
- **Computational efficiency**: the recursive algorithms are expressed as geometric products, avoiding explicit matrix inversions.
- **Geometric intuition**: the dynamics equations have a clear geometric interpretation in terms of forces, wrenches, and twists as multivectors.

### 7.4. Quantum Control and Projective Hilbert Space

In quantum mechanics, physical states are rays in a Hilbert space $\mathcal{H}$, so the state space is the projective Hilbert space $\mathbb{P}(\mathcal{H})$. For finite-dimensional systems, $\mathbb{P}(\mathbb{C}^n) = \mathbb{C}\mathrm{P}^{n-1}$ carries the Fubini–Study metric. Pastorello (2017) applies the accessibility-algebra framework of control theory to show that quantum controllability is characterized by Killing vector fields on $\mathbb{P}(\mathcal{H})$ — the projective structure is essential because the unitary group acts effectively only on the projective space, not on $\mathcal{H}$ itself. The Aharonov–Anandan geometric phase is the holonomy of the natural $U(1)$-bundle $\mathcal{H} \setminus \{0\} \to \mathbb{P}(\mathcal{H})$, again a fundamentally projective invariant.

### 7.5. Additional Applications

- **Convex algebraic geometry and polynomial optimization**: The Lasserre hierarchy defines spectrahedra via moment matrix conditions whose projections yield increasingly tight outer approximations. The Positivstellensatz theorems of Schmüdgen and Putinar characterize non-negative polynomials on real algebraic sets, which are naturally projective when homogenized.

- **Symplectic and Hamiltonian geometry**: The cotangent bundle $T^*\mathbb{R}\mathrm{P}^n$ carries a natural symplectic structure, and the geodesic flow on $\mathbb{R}\mathrm{P}^n$ with its constant-curvature metric is completely integrable (Arnold, 1988).

- **Information geometry**: The Fisher information metric on statistical manifolds carries a projective structure invariant under reparameterization of the statistical model (Amari and Nagaoka, 2000).

---

## 8. Concluding Remarks

Real projective geometry is not an isolated branch of mathematics but a *unifying framework*. The Fundamental Theorem of Projective Geometry — that every collineation of $\mathbb{R}\mathrm{P}^n$ is induced by a projective linear transformation — justifies $\mathrm{PGL}(n+1,\mathbb{R})$ as the maximal symmetry group of classical geometry. Klein's Erlangen program then positions this group at the top of an inclusion chain, with affine and Euclidean geometries arising by fixing additional structure (a hyperplane at infinity, then a conic at infinity).

The cross-ratio, as the fundamental projective invariant, encodes the entire geometry of $\mathbb{R}\mathrm{P}^1$ and appears in every application: the Cayley–Klein distance, the epipolar constraint in computer vision, the harmonic construction of projective bases, and the projective connections of Cartan geometry. Classical theorems — Desargues', Pappus' — are not mere curiosities but structural characterizations: they distinguish $\mathbb{R}\mathrm{P}^2$ from non-Desarguesian planes and characterize commutativity of the underlying field.

This unifying power explains the breadth of projective geometry's applications. In computer vision, the projective structure is intrinsic to perspective imaging, and the Erlangen program's philosophy — progressively fixing structure to recover affine and metric properties — is the foundation of camera calibration. In convex optimization, projective representations and projective cutting planes exploit the same projection-section duality that underlies projective duality. In robotics, projective geometric algebra unifies the algebraic treatment of points, lines, planes, and transformations. In quantum mechanics, the projective Hilbert space is the natural domain for the unitary group's effective action.

The interplay between the algebraic (homogeneous coordinates, Grassmannians, Plücker embeddings, Bézout's theorem), the synthetic (cross-ratio, Desargues, Pappus, harmonic conjugates), the differential (constant-curvature metric, projective connections), the topological (cohomology, Stiefel–Whitney classes, embedding obstructions), and the applied (vision, optimization, kinematics, control) aspects of real projective geometry exemplifies the deep unity of mathematics: a single structural insight — that lines through the origin in a vector space form a geometry with maximal symmetry — generates an entire interconnected edifice of theory and application.

---

## References

1. H. Amari and H. Nagaoka, *Methods of Information Geometry*, American Mathematical Society, Providence, 2000.

2. V. I. Arnold, *Mathematical Methods of Classical Mechanics*, 2nd ed., Springer, New York, 1988.

3. E. Artin, *Geometric Algebra*, Interscience Publishers, New York, 1957.

4. D. Pastorello, "A geometric approach to quantum control in projective Hilbert spaces," *Reports on Mathematical Physics*, vol. 79, no. 1, 2017, pp. 57–79.

5. F. L. Dorst, V. Fontijne, and S. Mann, *Geometric Algebra for Computer Science: An Object-Oriented Approach to Geometry*, Springer, London, 2007.

6. G. Sun and Y. Ding, "High-order inverse dynamics of serial robots based on projective geometric algebra," *Multibody System Dynamics*, vol. 59, 2023, pp. 1–31.

7. J. Kileel and K. Kohn, "Snapshot of algebraic vision," *arXiv:2210.11443* [math.AG], 2022.

8. J. Gouveia, P. A. Parrilo, and R. Thomas, *Semidefinite Optimization and Convex Algebraic Geometry*, SIAM, Philadelphia, 2022.

9. D. Hestenes, *New Foundations for Classical Mechanics*, 2nd ed., Kluwer Academic, Dordrecht, 1999.

10. R. I. Hartley and A. Zisserman, *Multiple View Geometry in Computer Vision*, 2nd ed., Cambridge University Press, Cambridge, 2004.

11. F. Klein, *Vergleichende Betrachtungen über neuere geometrische Forschungen*, Mathematische Annalen, vol. 43, 1893, pp. 63–100. (Original Erlangen program, 1872.)

12. J. W. Milnor and J. D. Stasheff, *Characteristic Classes*, Princeton University Press, Princeton, 1974.

13. D. Porumbel, "Semidefinite programming by projective cutting planes," *arXiv:2311.09365* [math.OC], 2023.

14. W. Pardon, "Conic programming: infeasibility certificates and projective duality," *Journal of Mathematical Analysis and Applications*, vol. 494, no. 2, 2021, 124567.

---
