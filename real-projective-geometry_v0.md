# Real Projective Geometry: From Klein's Unifying Vision to Modern Applications

## Abstract

Real projective geometry occupies a central position at the intersection of linear algebra, topology, and applied mathematics. This essay surveys the foundations of real projective spaces — their construction as quotient manifolds, their role as universal examples in algebraic topology, and Klein's Erlangen program as the unifying framework that positions projective geometry as the ambient context for all classical geometries. We then emphasize applications: computer vision and multiple-view geometry, where projective structure is not merely a mathematical convenience but the intrinsic geometry of perspective imaging; convex optimization and convex algebraic geometry, where projective representations and semidefinite programming interact; robot kinematics and dynamics via projective geometric algebra; and quantum control theory, where the projective Hilbert space carries a natural Fubini–Study metric. Throughout, we maintain the Erlangen perspective: projective geometry is the study of properties invariant under the action of the projective linear group $\mathrm{PGL}(n+1,\mathbb{R})$.

---

## 1. Foundations

### 1.1. Construction and Basic Properties

Let $\mathbb{R}^{n+1} \setminus \{0\}$ carry the equivalence relation $v \sim \lambda v$ for all $\lambda \in \mathbb{R} \setminus \{0\}$. The quotient space

$$\mathbb{R}\mathrm{P}^n = \left(\mathbb{R}^{n+1} \setminus \{0\}\right) / \sim$$

is the *real projective $n$-space*. Its points — projective points — are one-dimensional subspaces of $\mathbb{R}^{n+1}$. Homogeneous coordinates $[x_0 : x_1 : \cdots : x_n]$ represent the equivalence class of $(x_0, \ldots, x_n)$, and the projective linear group

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

In $\mathbb{R}\mathrm{P}^2$, this yields the celebrated duality between points and lines: any theorem about points and lines remains valid when "point" and "line" are interchanged and "incidence" is preserved. Desargues' theorem and its dual are the prototypical example. In general dimension, duality interchanges $k$-flats and $(n-2-k)$-flats in $\mathbb{R}\mathrm{P}^n$, which is equivalent to the linear-algebraic fact that the annihilator of a $k$-dimensional subspace of $\mathbb{R}^{n+1}$ has codimension $k$.

### 1.3. Grassmannians

The Grassmannian $\mathrm{Gr}(k, n+1)$ parametrizes $k$-dimensional subspaces of $\mathbb{R}^{n+1}$. Projective space is the case $k=1$: $\mathrm{Gr}(1, n+1) = \mathbb{R}\mathrm{P}^n$. More generally, the Plücker embedding

$$\mathrm{Gr}(k, n+1) \hookrightarrow \mathbb{R}\mathrm{P}^{\binom{n+1}{k}-1}$$

sends a $k$-plane $W = \mathrm{span}(v_1, \ldots, v_k)$ to the line in $\Lambda^k \mathbb{R}^{n+1}$ spanned by the decomposable $k$-vector $v_1 \wedge \cdots \wedge v_k$. The image is cut out by the Plücker relations — quadratic equations characterizing decomposable $k$-vectors — making $\mathrm{Gr}(k, n+1)$ a smooth projective algebraic variety.

The Grassmannians carry a transitive action of $\mathrm{GL}(n+1,\mathbb{R})$, and the isotropy at a $k$-plane $W_0$ is the parabolic subgroup preserving $W_0$. Thus $\mathrm{Gr}(k, n+1) \cong \mathrm{GL}(n+1,\mathbb{R}) / P_k$, a homogeneous space. This is the general pattern: flag manifolds $\mathrm{Fl}(k_1, \ldots, k_m; n+1)$ are also projective varieties with transitive $\mathrm{PGL}$-actions.

---

## 2. Topology of Real Projective Spaces

### 2.1. Fundamental Group and Universal Cover

From the double covering $\pi : S^n \to \mathbb{R}\mathrm{P}^n$ with $n \geq 2$, standard covering space theory yields

$$\pi_1(\mathbb{R}\mathrm{P}^n) \cong \mathbb{Z}_2, \quad \pi_k(\mathbb{R}\mathrm{P}^n) \cong \pi_k(S^n) \text{ for } k \geq 2.$$

For $n=1$, $\mathbb{R}\mathrm{P}^1 \cong S^1$, so $\pi_1(\mathbb{R}\mathrm{P}^1) \cong \mathbb{Z}$. The distinction at $n=1$ is the only exception in the homotopy type.

### 2.2. Cohomology and Stiefel–Whitney Classes

The cohomology ring with $\mathbb{Z}_2$-coefficients is one of the most elementary and important computations in algebraic topology. Let $a \in H^1(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2)$ be the generator. Then

$$H^*(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2) \cong \mathbb{Z}_2[a] / (a^{n+1}),$$

with $a$ of degree 1. With integer coefficients,

$$H^k(\mathbb{R}\mathrm{P}^n; \mathbb{Z}) = \begin{cases} \mathbb{Z} & k = 0, \\ \mathbb{Z}_2 & k \text{ odd}, 0 < k < n, \\ \mathbb{Z} & k = n \text{ and } n \text{ odd}, \\ 0 & \text{otherwise}. \end{cases}$$

The tangent bundle $T\mathbb{R}\mathrm{P}^n$ fits into the tautological short exact sequence

$$0 \to \gamma^1 \to \underline{\mathbb{R}}^{n+1} \to T\mathbb{R}\mathrm{P}^n \to 0,$$

where $\gamma^1$ is the tautological line bundle and $\underline{\mathbb{R}}^{n+1}$ is the trivial bundle. The total Stiefel–Whitney class is

$$w(\mathbb{R}\mathrm{P}^n) = (1+a)^{n+1} \in H^*(\mathbb{R}\mathrm{P}^n; \mathbb{Z}_2).$$

This implies $\mathbb{R}\mathrm{P}^n$ is orientable if and only if $n$ is odd (since $w_1 = (n+1)a \neq 0$ when $n$ is even). The non-orientability of $\mathbb{R}\mathrm{P}^2$ is the origin of the Möbius strip and Klein bottle constructions.

### 2.3. Embedding and Immersion Results

A central question — when does $\mathbb{R}\mathrm{P}^n$ embed in $\mathbb{R}^N$? — connects projective geometry to topology and algebra. The Wu formulas and Stiefel–Whitney class obstructions show that $\mathbb{R}\mathrm{P}^n$ embeds in $\mathbb{R}^{2n}$ for all $n$, and the sharpest known results use the Adams–Kervaire–Milnor theory of immersions. Notably:

- $\mathbb{R}\mathrm{P}^1 \cong S^1 \hookrightarrow \mathbb{R}^2$ (embedding),
- $\mathbb{R}\mathrm{P}^2 \hookrightarrow \mathbb{R}^4$ (embedding, but no immersion in $\mathbb{R}^3$ without self-intersection — Boy's surface is an immersion),
- $\mathbb{R}\mathrm{P}^n$ embeds in $\mathbb{R}^{2n - \alpha(n)}$, where $\alpha(n)$ is the number of 1's in the binary expansion of $n$.

The embedding dimension problem is intimately related to the vector field problem on spheres and to Hopf invariant one elements — a connection that ties projective topology to algebraic $K$-theory and stable homotopy.

---

## 3. Klein's Erlangen Program and the Unifying Role of Projective Geometry

### 3.1. The Erlangen Program

Klein's 1872 *Vergleichende Betrachtungen über neuere geometrische Forschungen* proposed that a geometry is characterized by its symmetry group $G$ acting on a space $X$. The fundamental insight: Euclidean, affine, and projective geometries are *not* fundamentally different subjects but rather *different choices* of symmetry group within the same ambient projective framework.

Specifically, let $X = \mathbb{R}\mathrm{P}^n$. Then:

| Geometry | Space $X$ | Group $G$ | Invariants |
|----------|-----------|-----------|------------|
| Projective | $\mathbb{R}\mathrm{P}^n$ | $\mathrm{PGL}(n+1,\mathbb{R})$ | Cross-ratio, incidence, collinearity |
| Affine | $\mathbb{R}^n \subset \mathbb{R}\mathrm{P}^n$ | Affine group $A(n,\mathbb{R})$ | Parallelism, ratios of lengths on parallel lines |
| Euclidean | $\mathbb{R}^n$ | $\mathrm{Euc}(n) = \mathbb{R}^n \rtimes O(n)$ | Lengths, angles, circles |
| Conformal | $\mathbb{R}^n$ | Möbius group | Angles (conformal class) |

The inclusion chain

$$\mathrm{Euc}(n) \subset \mathrm{CO}(n) \subset A(n,\mathbb{R}) \subset \mathrm{PGL}(n+1,\mathbb{R})$$

expresses that projective geometry is the *most general* classical geometry. Euclidean geometry is what remains when one fixes a hyperplane at infinity (passing from projective to affine) and a conic at infinity (passing from affine to Euclidean). The conic at infinity is the absolute — its stabilizer in $\mathrm{PGL}(n+1,\mathbb{R})$ is the Euclidean group.

### 3.2. The Absolute Conic and Cayley–Klein Distance

In $\mathbb{R}\mathrm{P}^2$, fix a non-degenerate conic $\Omega$ (the *absolute*). The distance between two points $P, Q$ is defined projectively as

$$d(P,Q) = \frac{1}{\sqrt{\kappa}} \log \left| \frac{(A,B;P,Q)}{(A,B;Q,P)} \right|^{1/2},$$

where $A, B$ are the intersection points of the line $PQ$ with $\Omega$, and $(\cdot,\cdot;\cdot,\cdot)$ is the cross-ratio. This is the *Cayley–Klein distance*. Depending on whether $\Omega$ is real, imaginary, or degenerate, one recovers Euclidean, hyperbolic, or elliptic geometry. In the Euclidean case, $\Omega$ is the imaginary conic $x^2 + y^2 = 0$ at infinity, and the distance formula reduces to the familiar expression via the logarithm of the cross-ratio.

This construction is profound: it shows that metric properties — distances and angles — are *projective invariants* of a configuration involving a distinguished conic. There is no need to introduce metric structure as an independent axiom; it emerges from projective structure plus a choice of absolute.

### 3.3. Modern Formulation: Homogeneous Spaces

In modern language, Klein's program says: a geometry is a pair $(G, H)$ where $G$ is a Lie group and $H$ is a closed subgroup, and the space is the homogeneous space $G/H$. Projective geometry corresponds to $(\mathrm{PGL}(n+1,\mathbb{R}), P)$ where $P$ is a maximal parabolic subgroup. The Erlangen perspective has been generalized in Thurston's geometrization program, Cartan's theory of connections, and Cartan geometry (Shilov).

---

## 4. Applications

### 4.1. Computer Vision and Multiple-View Geometry

The most extensive application of real projective geometry to engineering is computer vision, where the geometry of perspective imaging is *inherently* projective. Hartley and Zisserman's *Multiple View Geometry in Computer Vision* (2004) is the definitive reference.

#### 4.1.1. Camera Model

A pinhole camera is modeled as a linear projection

$$\mathbf{x} = P \mathbf{X},$$

where $\mathbf{X} \in \mathbb{R}^4$ is a point in $\mathbb{R}\mathrm{P}^3$ (homogeneous coordinates), $\mathbf{x} \in \mathbb{R}^3$ is a point in the image plane $\mathbb{R}\mathrm{P}^2$, and $P$ is a $3 \times 4$ matrix of rank 3 — the *camera matrix*. The kernel of $P$ is the camera center $C \in \mathbb{R}\mathrm{P}^3$. This model is projective: it makes no reference to metric structure. The matrix $P$ is determined only up to a non-zero scalar, reflecting the homogeneous nature of projective coordinates.

Decomposing $P$ as

$$P = K [R | t],$$

where $K$ is the $3 \times 3$ intrinsic calibration matrix (encoding focal length, principal point, and skew), $R \in SO(3)$ is a rotation, and $t \in \mathbb{R}^3$ is a translation, requires additional constraints that fix the Euclidean structure — the choice of an absolute conic. Without calibration, one works entirely in the projective category.

#### 4.1.2. Epipolar Geometry and the Fundamental Matrix

Given two views with camera matrices $P$ and $P'$, the *fundamental matrix* $F \in \mathbb{R}^{3 \times 3}$ satisfies

$$\mathbf{x}'^T F \mathbf{x} = 0$$

for corresponding points $\mathbf{x} \in \mathbb{R}\mathrm{P}^2$ and $\mathbf{x}' \in \mathbb{R}\mathrm{P}^2$. The matrix $F$ has rank 2 and is determined up to scale by 7 point correspondences (the *7-point algorithm*). Epipolar lines $\mathbf{l} = F\mathbf{x}$ and $\mathbf{l}' = F^T\mathbf{x}'$ arise from the duality discussed in §1.2: $F$ maps a point to a line, and by duality, a line to a point.

The epipoles $e$ and $e'$ are the null vectors of $F$ and $F^T$ respectively — they are the projections of the other camera center. The epipolar constraint is a *projective invariant*: it depends only on the incidence structure of points, lines, and the two camera centers.

#### 4.1.3. Projective Reconstruction

A landmark result: from two or more uncalibrated views, one can reconstruct the 3D scene *up to a projective transformation of $\mathbb{R}\mathrm{P}^3$*. This is *projective reconstruction*. To upgrade to affine or Euclidean reconstruction, one must impose constraints — vanishing points (for affine structure) or the dual of the absolute conic (for metric structure). The upgrade process is exactly the Erlangen program in action: progressively fixing subgroups of $\mathrm{PGL}(4,\mathbb{R})$.

#### 4.1.4. Algebraic Vision

Recent work has deepened the connection between projective geometry and algebraic geometry in computer vision. The survey by Kileel and Kohn (2022) introduces the term *algebraic vision* for this intersection. The *epipolar variety* — the set of all possible correspondences between points in multiple views — is a projective algebraic variety whose study uses tools from commutative algebra and algebraic geometry. Minimal problems in 3D reconstruction reduce to solving systems of polynomial equations on projective varieties, with solutions studied via Gröbner bases, resultant theory, and numerical algebraic geometry.

### 4.2. Convex Optimization and Convex Algebraic Geometry

Projective geometry interacts with convex optimization through several channels.

#### 4.2.1. Projective Representations of Convex Sets

A *projective representation* of a convex set $C \subset \mathbb{R}^n$ is a description of $C$ as the linear section of the projection of a spectrahedron (a set defined by a linear matrix inequality). This concept, developed by Gouveia, Parrilo, Thomas, and others, generalizes Lasserre's lift-and-project hierarchies. The *projective rank* of a convex set — the smallest dimension of a spectrahedron needed for a projective representation — is a fundamental complexity measure.

The connection to projective geometry is structural: the projection and intersection operations in the definition are precisely the projective operations of projecting from a center and taking hyperplane sections. The study of which convex sets admit low-dimensional projective representations connects to questions about the structure of convex algebraic varieties in projective space.

#### 4.2.2. Semidefinite Programming and Projective Cutting Planes

The recent work of Porumbel (2023) on *semidefinite programming by projective cutting planes* exploits the projective structure of the feasible set. The projection subproblem — finding the closest point in a spectrahedron — is formulated as a projective operation, and the projective structure yields efficient solutions. The book by Gouveia, Parrilo, and Thomas (2022), *Semidefinite Optimization and Convex Algebraic Geometry*, systematically develops the projective viewpoint for SDP.

### 4.3. Projective Geometric Algebra and Robot Kinematics

Projective geometric algebra (PGA), developed by Hestenes and extended by Dorst, Fontijne, and Mann (2007), provides a unified algebraic framework for projective, Euclidean, and conformal geometry. PGA is the Clifford algebra $\mathrm{Cl}(3,0,1)$ — the geometric algebra on a 4-dimensional space with signature $(3,0,1)$, where the distinguished direction encodes the plane at infinity.

#### 4.3.1. Unified Representation

In PGA, points, lines, planes, and their duals are represented as multivectors. The meet ($\wedge$) and join ($\vee$) operations correspond to intersection and span. Rigid transformations — rotations and translations — are represented as versors (products of reflections), and their composition is simply versor multiplication. This eliminates the need for separate matrix representations (rotation matrices, translation vectors, homogeneous transformation matrices) and unifies the algebraic treatment.

#### 4.3.2. Robot Kinematics and Dynamics

Recent work by Sun and Ding (2023) on *high-order inverse dynamics of serial robots based on projective geometric algebra* demonstrates the practical power of this approach. The PGA formulation yields:

- **Coordinate invariance**: the formulas do not depend on a choice of coordinate frame, unlike the Denavit–Hartenberg parameterization which requires careful frame placement.
- **Computational efficiency**: the recursive algorithms are expressed as geometric products, avoiding explicit matrix inversions.
- **Geometric intuition**: the dynamics equations have a clear geometric interpretation in terms of forces, wrenches, and twists as multivectors.

The "tetrahedral-point (TP) model" proposed by Li et al. (2025) for base inertial parameter identification reformulates rigid body dynamics using PGA, yielding a new identification model that exploits the projective structure of the inertial parameter space.

### 4.4. Quantum Control and Projective Hilbert Space

In quantum mechanics, physical states are represented not by vectors in a Hilbert space $\mathcal{H}$ but by *rays* — one-dimensional subspaces. The space of physical states is therefore the projective Hilbert space $\mathbb{P}(\mathcal{H})$. For finite-dimensional systems, $\mathbb{P}(\mathbb{C}^n) = \mathbb{C}\mathrm{P}^{n-1}$ carries the Fubini–Study metric, which measures the geometric distance between quantum states.

#### 4.4.1. Accessibility and Controllability

The paper by Pastorello (2017) on *a geometric approach to quantum control in projective Hilbert spaces* applies classical control theory's notion of an *accessibility algebra* to quantum systems. The key result: quantum controllability can be characterized in terms of Killing vector fields with respect to the Fubini–Study metric on $\mathbb{P}(\mathcal{H})$. The projective structure is not incidental — it is the natural domain on which the unitary group acts effectively (since global phases are physically irrelevant).

#### 4.4.2. Geometric Phases

The Aharonov–Anandan geometric phase is defined intrinsically on $\mathbb{P}(\mathcal{H})$ as the holonomy of the natural connection on the principal $U(1)$-bundle $\mathcal{H} \setminus \{0\} \to \mathbb{P}(\mathcal{H})$. The projective viewpoint is essential: the phase is a projective invariant, and its computation requires the projective connection, not a flat connection on $\mathcal{H}$.

### 4.5. Additional Applications

#### 4.5.1. Convex Algebraic Geometry and Polynomial Optimization

The Lasserre hierarchy for polynomial optimization uses projective varieties: the moment matrix conditions define spectrahedra whose projections yield increasingly tight outer approximations of the convex hull of the feasible set. The connection to real algebraic geometry is deep — the Positivstellensatz theorems of Schmüdgen and Putinar characterize non-negative polynomials on real algebraic sets, and these sets are naturally projective when homogenized.

#### 4.5.2. Symplectic and Hamiltonian Geometry

The cotangent bundle $T^*\mathbb{R}\mathrm{P}^n$ carries a natural symplectic structure. The geodesic flow on $\mathbb{R}\mathrm{P}^n$ with its constant-curvature metric is completely integrable, and its study connects to integrable systems and the theory of integrable Hamiltonian systems (Arnold, 1988).

#### 4.5.3. Information Geometry

The Fisher information metric on statistical manifolds has a projective structure: geodesics are curves of constant Fisher information, and the projective structure is invariant under reparameterization of the statistical model. The projective viewpoint clarifies the relationship between different statistical divergences and their geometric properties (Amari and Nagaoka, 2000).

---

## 5. Concluding Remarks

Real projective geometry is not an isolated branch of mathematics but a *unifying framework*. Klein's Erlangen program — that geometry is the study of invariants under a group of transformations — positions $\mathrm{PGL}(n+1,\mathbb{R})$ as the maximal symmetry group of classical geometry, with all other geometries arising by fixing additional structure (a hyperplane at infinity for affine geometry; a conic at infinity for Euclidean geometry).

This unifying power explains the breadth of projective geometry's applications. In computer vision, the projective structure is intrinsic to perspective imaging, and the Erlangen program's philosophy — progressively fixing structure to recover affine and metric properties — is the foundation of camera calibration. In convex optimization, projective representations and projective cutting planes exploit the same projection-section duality that underlies projective duality. In robotics, projective geometric algebra unifies the algebraic treatment of points, lines, planes, and transformations. In quantum mechanics, the projective Hilbert space is the natural domain for the unitary group's effective action.

The interplay between the algebraic (homogeneous coordinates, Grassmannians, Plücker embeddings), the topological (cohomology, Stiefel–Whitney classes, embedding obstructions), and the applied (vision, optimization, kinematics, control) aspects of real projective geometry exemplifies the deep unity of mathematics: a single structural insight — that lines through the origin in a vector space form a geometry with maximal symmetry — generates an entire interconnected edifice of theory and application.

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
