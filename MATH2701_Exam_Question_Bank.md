# MATH2701 — Exam Preparation Question Bank
**Module: Probability & Statistics | 110 Questions across 11 Chapters**

---

## Chapter 1: Probability Distributions

---

**Q1.1** Let X ~ Gamma(3, 2). Write down the PDF of X, and state its mean and variance.

**Answer:**

The PDF of X ~ Gamma(α, λ) is:

$$f_X(x) = \frac{\lambda^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\lambda x}, \quad x \geq 0$$

With α = 3, λ = 2:

$$f_X(x) = \frac{2^3}{\Gamma(3)} x^2 e^{-2x} = \frac{8}{2} x^2 e^{-2x} = 4x^2 e^{-2x}, \quad x \geq 0$$

(since Γ(3) = 2! = 2)

**Mean:** E[X] = α/λ = 3/2

**Variance:** Var[X] = α/λ² = 3/4

*Key fact: Γ(n) = (n−1)! for positive integers, so Γ(3) = 2! = 2.*

---

**Q1.2** If Z₁, Z₂, Z₃ are independent standard normal random variables, what is the distribution of X = Z₁² + Z₂² + Z₃²?

**Answer:**

By the definition of the chi-squared distribution:

$$X = \sum_{i=1}^{k} Z_i^2 \sim \chi^2_k \quad \text{where each } Z_i \sim N(0,1)$$

Here k = 3, so **X ~ χ²₃**.

*Key fact: The chi-squared distribution is a special case of the Gamma distribution with shape α = k/2 and rate λ = 1/2. So χ²₃ ≡ Gamma(3/2, 1/2).*

---

**Q1.3** If X₁ ~ χ²₄ and X₂ ~ χ²₆ are independent, what is the distribution of:

$$F = \frac{X_1/4}{X_2/6}$$

**Answer:**

By the definition of the F-distribution, the ratio of two independent scaled chi-squared variables is:

$$F = \frac{X_1/d_1}{X_2/d_2} \sim F(d_1, d_2)$$

Here d₁ = 4, d₂ = 6, so **F ~ F(4, 6)**.

For d₂ > 2: E[F] = d₂/(d₂ − 2) = 6/4 = 3/2.

*Key fact: The F-distribution is widely used in ANOVA and regression model comparison.*

---

**Q1.4** Suppose X and Y have joint PDF f(x, y) = 6(1 − y) for 0 ≤ x ≤ y ≤ 1. Find the marginal PDF of Y.

**Answer:**

Integrate out x. Since 0 ≤ x ≤ y, x ranges from 0 to y:

$$f_Y(y) = \int_0^y 6(1-y)\,dx = 6(1-y) \cdot y = 6y(1-y), \quad 0 \leq y \leq 1$$

**Verification:** ∫₀¹ 6y(1−y) dy = 6[y²/2 − y³/3]₀¹ = 6(1/2 − 1/3) = 6 · 1/6 = 1. ✓

---

**Q1.5** For the joint PDF in Q1.4, determine whether X and Y are independent.

**Answer:**

First find the marginal PDF of X. Since x ≤ y ≤ 1:

$$f_X(x) = \int_x^1 6(1-y)\,dy = 6\left[y - \frac{y^2}{2}\right]_x^1 = 6\left(\frac{1}{2} - x + \frac{x^2}{2}\right) = 3(1-x)^2$$

Now check whether f(x, y) = f_X(x) · f_Y(y):

f_X(x) · f_Y(y) = 3(1−x)² · 6y(1−y) ≠ 6(1−y) = f(x, y) in general.

**X and Y are not independent.** (Alternatively: the support of (X, Y) is not a rectangle — X cannot exceed Y — which immediately implies dependence.)

---

**Q1.6** State under what conditions the Binomial(n, p) distribution can be approximated by a Normal distribution, and write the approximating distribution.

**Answer:**

The approximation is valid when both **np > 5** and **n(1−p) > 5**. Then:

$$X \sim \text{Binomial}(n,p) \approx N(\mu = np,\; \sigma^2 = np(1-p))$$

For greater accuracy with discrete data, apply the **continuity correction**: approximate P(X ≤ k) by P(Y ≤ k + 0.5) where Y ~ N(np, np(1−p)).

---

**Q1.7** Let X ~ Poisson(λ). Under what condition is X well approximated by a Normal distribution, and what are the approximate parameters?

**Answer:**

When **λ > 20** (and even better for larger λ):

$$X \sim \text{Poisson}(\lambda) \approx N(\mu = \lambda,\; \sigma^2 = \lambda)$$

This works because both the mean and variance of the Poisson distribution equal λ, and the CLT kicks in for large λ (think of Poisson(λ) as the sum of λ independent Poisson(1) variables).

---

**Q1.8** If X ~ Poisson(λ) and Y ~ Poisson(μ) are independent, what is the distribution of Z = X + Y? Use convolution.

**Answer:**

Using the convolution formula for independent discrete random variables:

$$P(Z = z) = \sum_{k=0}^{z} P(X=k)P(Y=z-k) = \sum_{k=0}^{z} \frac{\lambda^k e^{-\lambda}}{k!} \cdot \frac{\mu^{z-k} e^{-\mu}}{(z-k)!}$$

$$= \frac{e^{-(\lambda+\mu)}}{z!} \sum_{k=0}^{z} \binom{z}{k} \lambda^k \mu^{z-k} = \frac{(\lambda+\mu)^z e^{-(\lambda+\mu)}}{z!}$$

So **Z ~ Poisson(λ + μ)**.

*This is the reproductive property of the Poisson distribution.*

---

**Q1.9** Suppose X ~ Gamma(α₁, λ) and Y ~ Gamma(α₂, λ) are independent. State (without full proof) the distribution of Z = X + Y.

**Answer:**

Using the convolution of Gamma densities (or equivalently, using MGFs):

**Z ~ Gamma(α₁ + α₂, λ)**

*Intuition: The Gamma(α, λ) distribution is the sum of α independent Exponential(λ) variables. Adding two such sums gives Gamma(α₁ + α₂, λ).*

*Important: Both must have the same rate λ for this to work.*

---

**Q1.10** For X ~ Gamma(α, λ), the special case α = 1 reduces to which distribution? State its PDF, mean, and variance.

**Answer:**

When α = 1, Gamma(1, λ) = **Exponential(λ)**.

**PDF:** f(x) = λe^{−λx}, x > 0

**Mean:** E[X] = 1/λ

**Variance:** Var[X] = 1/λ²

*Memory check: The exponential is the only continuous memoryless distribution: P(X > s+t | X > s) = P(X > t).*

---

## Chapter 2: Moments

---

**Q2.1** A continuous random variable X has PDF f_X(x) = 6x(1−x) for 0 < x < 1. Find E[X] and Var[X].

**Answer:**

First verify the constant: ∫₀¹ 6x(1−x) dx = 6[x²/2 − x³/3]₀¹ = 6(1/2 − 1/3) = 1 ✓

**Mean:**

$$E[X] = \int_0^1 x \cdot 6x(1-x)\,dx = 6\int_0^1 (x^2 - x^3)\,dx = 6\left[\frac{1}{3} - \frac{1}{4}\right] = 6 \cdot \frac{1}{12} = \frac{1}{2}$$

**Second moment:**

$$E[X^2] = \int_0^1 x^2 \cdot 6x(1-x)\,dx = 6\int_0^1 (x^3 - x^4)\,dx = 6\left[\frac{1}{4} - \frac{1}{5}\right] = 6 \cdot \frac{1}{20} = \frac{3}{10}$$

**Variance:**

$$\text{Var}[X] = E[X^2] - (E[X])^2 = \frac{3}{10} - \frac{1}{4} = \frac{6-5}{20} = \frac{1}{20}$$

---

**Q2.2** Random variables X, Y and Z have means 1, 2, 3, variances 2, 4, 6, and Cov[X,Y] = Cov[Y,Z] = 1, Cov[X,Z] = 0. Find E[U] and Var[U] where U = X − 2Y + Z.

**Answer:**

**Mean:**

$$E[U] = E[X] - 2E[Y] + E[Z] = 1 - 2(2) + 3 = 0$$

**Variance:** Using the formula Var[aX + bY + cZ] = a²Var[X] + b²Var[Y] + c²Var[Z] + 2ab·Cov[X,Y] + 2ac·Cov[X,Z] + 2bc·Cov[Y,Z], with a=1, b=−2, c=1:

$$\text{Var}[U] = 1^2(2) + (-2)^2(4) + 1^2(6) + 2(1)(-2)(1) + 2(1)(1)(0) + 2(-2)(1)(1)$$

$$= 2 + 16 + 6 - 4 + 0 - 4 = 16$$

---

**Q2.3** Define skewness and kurtosis (population versions). What does positive skewness mean geometrically?

**Answer:**

**Skewness:** 

$$\gamma_1 = \frac{E[(X-\mu)^3]}{\sigma^3} = \frac{\mu_3}{\sigma^3}$$

**Kurtosis:** 

$$\beta_2 = \frac{E[(X-\mu)^4]}{\sigma^4} = \frac{\mu_4}{\sigma^4}$$

**Excess kurtosis:** γ₂ = β₂ − 3 (so the normal distribution has excess kurtosis 0).

**Positive skewness** means the distribution has a longer right tail — the mass is concentrated on the left, with a tail stretching right. The mean is typically greater than the median.

---

**Q2.4** Show that Cov[X+Y, Z] = Cov[X,Z] + Cov[Y,Z].

**Answer:**

By the definition of covariance:

$$\text{Cov}[X+Y, Z] = E[(X+Y)Z] - E[X+Y]E[Z]$$

$$= E[XZ] + E[YZ] - (E[X] + E[Y])E[Z]$$

$$= (E[XZ] - E[X]E[Z]) + (E[YZ] - E[Y]E[Z])$$

$$= \text{Cov}[X,Z] + \text{Cov}[Y,Z] \quad \square$$

---

**Q2.5** If X and Y are independent random variables, show that Cov[X,Y] = 0.

**Answer:**

$$\text{Cov}[X,Y] = E[XY] - E[X]E[Y]$$

When X and Y are independent, their joint PDF factorises: f_{X,Y}(x,y) = f_X(x) · f_Y(y). Therefore:

$$E[XY] = \int\int xy\, f_X(x)f_Y(y)\,dx\,dy = \int x f_X(x)\,dx \cdot \int y f_Y(y)\,dy = E[X]E[Y]$$

So Cov[X,Y] = E[X]E[Y] − E[X]E[Y] = 0. □

*Warning: The converse is false — Cov[X,Y] = 0 does not imply independence in general.*

---

**Q2.6** The rth sample moment about the origin is m'_r = (1/n)∑Xᵢʳ. Is the sample variance S² = (1/(n−1))∑(Xᵢ−X̄)² an unbiased estimator of σ²?

**Answer:**

**Yes.** E[S²] = σ². Here is a sketch of the proof:

$$\sum_{i=1}^n (X_i - \bar{X})^2 = \sum_{i=1}^n X_i^2 - n\bar{X}^2$$

Taking expectations: E[∑Xᵢ²] = n(σ² + μ²) and E[nX̄²] = n · (σ²/n + μ²) = σ² + nμ².

So E[∑(Xᵢ−X̄)²] = n(σ² + μ²) − (σ² + nμ²) = (n−1)σ².

Therefore E[S²] = (n−1)σ² / (n−1) = σ². ✓

*Note: The "naive" estimator m₂ = (1/n)∑(Xᵢ−X̄)² is biased: E[m₂] = ((n−1)/n)σ².*

---

**Q2.7** Let X ~ Gamma(α, λ). Use the raw moment formula to find E[X²] and then Var[X].

**Answer:**

For Gamma(α, λ), the PDF integrates as: ∫₀^∞ x^{k-1} e^{-λx} dx = Γ(k)/λ^k.

$$E[X^2] = \int_0^\infty x^2 \cdot \frac{\lambda^\alpha}{\Gamma(\alpha)} x^{\alpha-1}e^{-\lambda x}\,dx = \frac{\lambda^\alpha}{\Gamma(\alpha)} \cdot \frac{\Gamma(\alpha+2)}{\lambda^{\alpha+2}}$$

Since Γ(α+2) = (α+1)α Γ(α):

$$E[X^2] = \frac{\alpha(\alpha+1)}{\lambda^2}$$

$$\text{Var}[X] = E[X^2] - (E[X])^2 = \frac{\alpha(\alpha+1)}{\lambda^2} - \frac{\alpha^2}{\lambda^2} = \frac{\alpha}{\lambda^2}$$

---

**Q2.8** What is the correlation ρ(X,Y)? What are its minimum and maximum possible values?

**Answer:**

$$\rho(X,Y) = \frac{\text{Cov}[X,Y]}{\sqrt{\text{Var}[X]}\sqrt{\text{Var}[Y]}} = \frac{\sigma_{XY}}{\sigma_X \sigma_Y}$$

By the Cauchy-Schwarz inequality: **−1 ≤ ρ(X,Y) ≤ 1**.

- ρ = 1: perfect positive linear relationship (Y = aX + b with a > 0)
- ρ = −1: perfect negative linear relationship (Y = aX + b with a < 0)
- ρ = 0: uncorrelated (but not necessarily independent)

---

**Q2.9** For a random sample X₁,...,Xₙ, define the rth central sample moment mᵣ and the rth raw sample moment m'ᵣ. State the relationship m₃ = m'₃ − 3m'₂m'₁ + 2(m'₁)³.

**Answer:**

**Definitions:**

$$m'_r = \frac{1}{n}\sum_{i=1}^n X_i^r \quad \text{(raw moment)}, \qquad m_r = \frac{1}{n}\sum_{i=1}^n (X_i - \bar{X})^r \quad \text{(central moment)}$$

**Relationship** (expand (Xᵢ − X̄)³ = Xᵢ³ − 3X̄Xᵢ² + 3X̄²Xᵢ − X̄³ and average):

$$m_3 = m'_3 - 3m'_2 m'_1 + 2(m'_1)^3$$

This mirrors the population identity μ₃ = μ'₃ − 3μ'₂μ'₁ + 2(μ'₁)³.

---

**Q2.10** A random variable X has E[X] = 3, E[X²] = 13. Find Var[X] and Var[2X − 5].

**Answer:**

$$\text{Var}[X] = E[X^2] - (E[X])^2 = 13 - 9 = 4$$

$$\text{Var}[2X - 5] = 2^2 \cdot \text{Var}[X] = 4 \cdot 4 = 16$$

(Constants shift the mean but don't affect variance; scaling by a multiplies variance by a².)

---

## Chapter 3: Functions of a Random Variable

---

**Q3.1** Let X ~ Exponential(1/θ), so f_X(x) = (1/θ)e^{−x/θ}, x > 0. Find the PDF of Y = eˣ using the one-to-one transformation formula.

**Answer:**

The transformation y = eˣ is one-to-one with inverse x = g⁻¹(y) = ln(y), so y ∈ [1, ∞).

$$\frac{dx}{dy} = \frac{d}{dy}\ln(y) = \frac{1}{y}$$

Apply the formula fY(y) = f_X(g⁻¹(y)) · |dx/dy|:

$$f_Y(y) = \frac{1}{\theta} e^{-\ln(y)/\theta} \cdot \frac{1}{y} = \frac{1}{\theta} y^{-1/\theta} \cdot \frac{1}{y} = \frac{1}{\theta} y^{-(1/\theta + 1)}, \quad y \geq 1$$

This is a **Pareto distribution**.

---

**Q3.2** If X ~ Uniform(−1, 1), find the PDF of U = X² using the CDF method.

**Answer:**

For u ∈ [0, 1]:

$$F_U(u) = P(U \leq u) = P(X^2 \leq u) = P(-\sqrt{u} \leq X \leq \sqrt{u}) = \frac{\sqrt{u} - (-\sqrt{u})}{2} = \sqrt{u}$$

Differentiate:

$$f_U(u) = \frac{d}{du}\sqrt{u} = \frac{1}{2\sqrt{u}}, \quad 0 < u \leq 1$$

*This is a Beta(1/2, 1) distribution.*

---

**Q3.3** If X ~ Uniform(0, a), find the PDF of Y = X² using the one-to-one transformation.

**Answer:**

The function y = x² is one-to-one on (0, a) since x > 0. The inverse is x = √y, so y ∈ (0, a²).

$$\frac{dx}{dy} = \frac{1}{2\sqrt{y}}$$

$$f_Y(y) = f_X(\sqrt{y}) \cdot \frac{1}{2\sqrt{y}} = \frac{1}{a} \cdot \frac{1}{2\sqrt{y}} = \frac{1}{2a\sqrt{y}}, \quad 0 < y < a^2$$

This matches option **A** and **C** from the mock exam (they are equivalent, since y^{−1/2} = 1/√y).

---

**Q3.4** If X ~ Uniform(−1, 2), find the PDF of Y = X² on each domain separately.

**Answer:**

The function y = x² is two-to-one on [−1, 0] and one-to-one on [0, 2]. We split:

**Domain y ∈ (0, 1]:** Both x = −√y (from [−1,0]) and x = √y (from (0,1]) map here.

$$f_Y(y) = f_X(-\sqrt{y})\cdot\frac{1}{2\sqrt{y}} + f_X(\sqrt{y})\cdot\frac{1}{2\sqrt{y}} = \frac{1}{3}\cdot\frac{1}{2\sqrt{y}} + \frac{1}{3}\cdot\frac{1}{2\sqrt{y}} = \frac{1}{3\sqrt{y}}$$

**Domain y ∈ (1, 4]:** Only x = √y (from (1, 2]) maps here.

$$f_Y(y) = f_X(\sqrt{y})\cdot\frac{1}{2\sqrt{y}} = \frac{1}{3}\cdot\frac{1}{2\sqrt{y}} = \frac{1}{6\sqrt{y}}$$

---

**Q3.5** Let X have PDF f_X(x) = 2x for 0 < x < 1. Using the CDF method, find the PDF of Y = −ln(X).

**Answer:**

Note y = −ln(x) means x = e^{−y}, and since 0 < x < 1, we have y > 0.

$$F_Y(y) = P(Y \leq y) = P(-\ln X \leq y) = P(X \geq e^{-y}) = 1 - F_X(e^{-y})$$

Since F_X(x) = x² for 0 < x < 1:

$$F_Y(y) = 1 - e^{-2y}$$

Differentiate:

$$f_Y(y) = 2e^{-2y}, \quad y > 0$$

**Y ~ Exponential(2).**

---

**Q3.6** State the one-to-one transformation formula for a continuous random variable. When does the two-branch formula apply?

**Answer:**

**One-to-one:** If Y = g(X) is strictly monotone and differentiable:

$$f_Y(y) = f_X(g^{-1}(y)) \cdot \left|\frac{d}{dy}g^{-1}(y)\right|$$

**Two-to-one:** If for each y, the equation g(x) = y has exactly two solutions x₁(y) and x₂(y):

$$f_Y(y) = f_X(x_1(y))\left|\frac{dx_1}{dy}\right| + f_X(x_2(y))\left|\frac{dx_2}{dy}\right|$$

The two-branch formula applies when g is not globally monotone — e.g., g(x) = x² on a symmetric interval.

---

**Q3.7** Let (X, Y) have joint PDF f(x,y) and let U = g(X, Y), V = h(X, Y) be a one-to-one bivariate transformation. State the formula for f_{U,V}(u,v).

**Answer:**

If the inverse is x = g⁻¹(u,v), y = h⁻¹(u,v), and the Jacobian is:

$$J = \frac{\partial(x,y)}{\partial(u,v)} = \begin{vmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{vmatrix}$$

then:

$$f_{U,V}(u,v) = f_{X,Y}(g^{-1}(u,v),\, h^{-1}(u,v)) \cdot |J|$$

---

**Q3.8** Let X and Y be independent with X ~ Exponential(1) and Y ~ Exponential(1). Let U = X + Y and V = X/(X+Y). Show that U and V are independent and find their distributions.

**Answer:**

Set U = X + Y, V = X/(X+Y). Inverting: X = UV, Y = U(1−V).

**Jacobian:**

$$J = \begin{vmatrix} v & u \\ 1-v & -u \end{vmatrix} = -uv - u(1-v) = -u \quad \Rightarrow \quad |J| = u$$

**Joint PDF:** Since X and Y are independent Exp(1):

$$f_{X,Y}(x,y) = e^{-x}e^{-y} = e^{-(x+y)}$$

$$f_{U,V}(u,v) = e^{-u} \cdot u = ue^{-u}, \quad u > 0, \; 0 < v < 1$$

This factors as (ue^{−u}) × 1, so U ~ Gamma(2,1) and V ~ Uniform(0,1), and **they are independent**.

---

**Q3.9** Let X ~ N(0,1). Find the PDF of Y = X².

**Answer:**

For y > 0, both x = √y and x = −√y map to y:

$$f_Y(y) = f_X(\sqrt{y})\cdot\frac{1}{2\sqrt{y}} + f_X(-\sqrt{y})\cdot\frac{1}{2\sqrt{y}}$$

Since f_X is symmetric about 0, f_X(√y) = f_X(−√y) = (1/√(2π))e^{−y/2}:

$$f_Y(y) = 2 \cdot \frac{1}{\sqrt{2\pi}} e^{-y/2} \cdot \frac{1}{2\sqrt{y}} = \frac{1}{\sqrt{2\pi}} y^{-1/2} e^{-y/2} = \frac{1}{2^{1/2}\Gamma(1/2)} y^{1/2-1} e^{-y/2}$$

This is **Gamma(1/2, 1/2) = χ²₁**, confirming that the square of a standard normal is chi-squared with 1 degree of freedom.

---

**Q3.10** Let Z ~ N(0,1) and define Y = |Z|. Find f_Y(y).

**Answer:**

For y > 0: the equation |z| = y has solutions z = y and z = −y.

$$f_Y(y) = f_Z(y)\cdot 1 + f_Z(-y)\cdot 1 = \frac{2}{\sqrt{2\pi}} e^{-y^2/2}, \quad y > 0$$

(Multiplied by |d/dy (y)| = 1 and |d/dy (−y)| = 1.)

This is the **half-normal distribution**. E[Y] = √(2/π) and Var[Y] = 1 − 2/π.

---

## Chapter 4: Random Vectors

---

**Q4.1** Let Y be a random vector with mean vector μ and covariance matrix Σ. Let C be a constant matrix and b a constant vector. State E[CY + b] and Cov[CY + b].

**Answer:**

$$E[CY + b] = C\mu + b$$

$$\text{Cov}[CY + b] = C\Sigma C^\top$$

*Proof sketch: Linearity of expectation gives the first. For the covariance, CY + b − E[CY + b] = C(Y − μ), so Cov = E[C(Y−μ)(Y−μ)ᵀCᵀ] = CΣCᵀ.*

---

**Q4.2** Let X₁, X₂ be i.i.d. N(0, σ² = 4). Write down the joint PDF and the covariance matrix Σ.

**Answer:**

Since they are independent:

$$f_{X_1,X_2}(x_1,x_2) = \frac{1}{2\pi\sigma^2}\exp\left(-\frac{x_1^2+x_2^2}{2\sigma^2}\right) = \frac{1}{8\pi}\exp\left(-\frac{x_1^2+x_2^2}{8}\right)$$

Covariance matrix (diagonal since independent):

$$\Sigma = \begin{pmatrix} 4 & 0 \\ 0 & 4 \end{pmatrix} = 4I_2$$

---

**Q4.3** For the general bivariate normal X ~ N(0, Σ) with Σ = [[σ², ρσ²], [ρσ², σ²]], write the joint PDF.

**Answer:**

$$f_X(x_1, x_2) = \frac{1}{2\pi\sigma^2\sqrt{1-\rho^2}} \exp\left(-\frac{x_1^2 + x_2^2 - 2\rho x_1 x_2}{2\sigma^2(1-\rho^2)}\right)$$

with |Σ| = σ⁴(1−ρ²), so |Σ|^{1/2} = σ²√(1−ρ²).

*Key: For multivariate normal, ρ = 0 ⟺ independence (unlike general random variables).*

---

**Q4.4** If X ~ N(μ, Σ) is a multivariate normal vector and A is a constant matrix, b is a constant vector, what is the distribution of AX + b?

**Answer:**

$$AX + b \sim N(A\mu + b,\; A\Sigma A^\top)$$

This is the **affine stability property** of the multivariate normal. Any affine transformation of a multivariate normal is again multivariate normal.

---

**Q4.5** Let Y = (Y₁, Y₂)ᵀ with E[Y₁] = 1, E[Y₂] = 2, Var[Y₁] = 4, Var[Y₂] = 9, Cov[Y₁,Y₂] = 3. Define X = Y₁ + 2Y₂. Find E[X] and Var[X].

**Answer:**

Writing X = (1, 2)Y = CY with C = (1, 2):

$$E[X] = E[Y_1] + 2E[Y_2] = 1 + 4 = 5$$

$$\Sigma = \begin{pmatrix} 4 & 3 \\ 3 & 9 \end{pmatrix}$$

$$\text{Var}[X] = C\Sigma C^\top = (1, 2)\begin{pmatrix}4 & 3\\ 3 & 9\end{pmatrix}\begin{pmatrix}1\\2\end{pmatrix} = (1,2)\begin{pmatrix}10\\21\end{pmatrix} = 10 + 42 = 52$$

*Or directly: Var[Y₁ + 2Y₂] = Var[Y₁] + 4Var[Y₂] + 2·2·Cov[Y₁,Y₂] = 4 + 36 + 12 = 52.*

---

**Q4.6** Explain why the covariance matrix Σ of any random vector is always symmetric and positive semi-definite.

**Answer:**

**Symmetric:** σᵢⱼ = Cov[Yᵢ, Yⱼ] = Cov[Yⱼ, Yᵢ] = σⱼᵢ by symmetry of covariance. So Σ = Σᵀ.

**Positive semi-definite:** For any constant vector c:

$$c^\top \Sigma c = c^\top \text{Cov}[Y]c = \text{Cov}[c^\top Y, c^\top Y] = \text{Var}[c^\top Y] \geq 0$$

since variance is always non-negative. If Σ is the covariance of a non-degenerate random vector, it will be **positive definite** (strict inequality).

---

**Q4.7** For the bivariate normal X ~ N(μ, Σ), what is the marginal distribution of X₁?

**Answer:**

Any marginal of a multivariate normal is normal. Writing X₁ = (1, 0)X:

$$X_1 \sim N(\mu_1, \sigma_{11})$$

More generally, if X ~ N(μ, Σ) is partitioned as X = (X₁, X₂)ᵀ, then:

$$X_1 \sim N(\mu_1, \Sigma_{11})$$

where μ₁ and Σ₁₁ are the corresponding sub-vector and sub-matrix of μ and Σ.

---

**Q4.8** Define the covariance matrix of a random vector Y = (Y₁,...,Yₙ)ᵀ and show it can be written as Σ = E[YYᵀ] − μμᵀ.

**Answer:**

**Definition:** Σ = Cov[Y] = E[(Y − μ)(Y − μ)ᵀ] where μ = E[Y].

**Expanding:**

$$\Sigma = E[YY^\top - Y\mu^\top - \mu Y^\top + \mu\mu^\top]$$

$$= E[YY^\top] - E[Y]\mu^\top - \mu E[Y^\top] + \mu\mu^\top$$

$$= E[YY^\top] - \mu\mu^\top - \mu\mu^\top + \mu\mu^\top = E[YY^\top] - \mu\mu^\top$$

---

**Q4.9** Suppose X = (X₁, X₂)ᵀ ~ N(0, Σ) with Σ = [[1, ρ], [ρ, 1]]. For what value of ρ are X₁ and X₂ independent?

**Answer:**

For the bivariate normal distribution only, **ρ = 0** implies independence.

When ρ = 0: Σ = I₂, and the joint PDF factors as:

$$f(x_1,x_2) = \frac{1}{2\pi}e^{-(x_1^2+x_2^2)/2} = \frac{1}{\sqrt{2\pi}}e^{-x_1^2/2} \cdot \frac{1}{\sqrt{2\pi}}e^{-x_2^2/2} = f_{X_1}(x_1)f_{X_2}(x_2)$$

*This is a special property of the normal family: zero correlation implies independence, which does not hold for random variables in general.*

---

**Q4.10** Let Y = (Y₁,...,Yₙ)ᵀ where Yᵢ = a + bXᵢ for constants a and b. If X ~ N(μ𝐗 · 1, σ²Iₙ), find E[Y] and Cov[Y].

**Answer:**

Writing Y = b·X + a·1ₙ (a linear transformation with C = bIₙ, constant vector a·1ₙ):

$$E[Y] = b\mu_X \mathbf{1}_n + a\mathbf{1}_n = (a + b\mu_X)\mathbf{1}_n$$

$$\text{Cov}[Y] = (bI_n)(σ^2 I_n)(bI_n)^\top = b^2 \sigma^2 I_n$$

So each Yᵢ has mean a + bμ_X and variance b²σ², and they are uncorrelated (independent since normal).

---

## Chapter 5: Moment Generating Functions

---

**Q5.1** Define the moment generating function (MGF) of a random variable X. State the key property relating the MGF to moments.

**Answer:**

$$M_X(t) = E[e^{tX}], \quad \text{defined for } t \text{ in an open interval around 0}$$

**Key property:** 

$$M_X^{(n)}(0) = \frac{\partial^n M_X}{\partial t^n}\bigg|_{t=0} = E[X^n]$$

So the nth derivative of the MGF evaluated at t = 0 gives the nth raw moment. This gives a systematic way to compute moments by differentiating once (for mean), twice (for second moment), etc.

---

**Q5.2** Find the MGF of X ~ N(μ, σ²).

**Answer:**

$$M_X(t) = E[e^{tX}] = \int_{-\infty}^\infty e^{tx} \frac{1}{\sqrt{2\pi}\sigma} e^{-(x-\mu)^2/(2\sigma^2)}\,dx$$

Complete the square in the exponent: tx − (x−μ)²/(2σ²) = −(x−μ−tσ²)²/(2σ²) + μt + σ²t²/2.

The remaining integral is that of a normal PDF (integrates to 1):

$$\boxed{M_X(t) = e^{\mu t + \frac{\sigma^2 t^2}{2}}}$$

---

**Q5.3** Let X have MGF M_X(t) = e^{3t + 2t²}. Identify the distribution of X and find E[X³].

**Answer:**

Comparing with the normal MGF e^{μt + σ²t²/2}:

μt + σ²t²/2 = 3t + 2t² ⟹ **μ = 3, σ² = 4**

So **X ~ N(3, 4)**.

For E[X³], use the formula for normal moments. Alternatively, differentiate M_X three times. Let μ = 3, σ = 2:

$$E[X^3] = \mu^3 + 3\mu\sigma^2 = 27 + 3(3)(4) = 27 + 36 = 63$$

*This matches answer C from the mock exam.*

---

**Q5.4** Find the MGF of X ~ Exponential(λ) (with mean 1/λ).

**Answer:**

$$M_X(t) = E[e^{tX}] = \int_0^\infty e^{tx} \lambda e^{-\lambda x}\,dx = \lambda \int_0^\infty e^{-(λ-t)x}\,dx$$

This converges for t < λ:

$$M_X(t) = \lambda \cdot \frac{1}{\lambda - t} = \frac{\lambda}{\lambda - t}, \quad t < \lambda$$

Differentiating: M'(0) = E[X] = 1/λ and M''(0) = E[X²] = 2/λ², giving Var[X] = 1/λ².

---

**Q5.5** Find the MGF of X ~ Poisson(λ) and use it to find E[X] and E[X²].

**Answer:**

$$M_X(t) = E[e^{tX}] = \sum_{k=0}^\infty e^{tk} \frac{\lambda^k e^{-\lambda}}{k!} = e^{-\lambda} \sum_{k=0}^\infty \frac{(\lambda e^t)^k}{k!} = e^{-\lambda} e^{\lambda e^t} = e^{\lambda(e^t - 1)}$$

Differentiating:

$$M'(t) = \lambda e^t e^{\lambda(e^t-1)} \Rightarrow E[X] = M'(0) = \lambda$$

$$M''(t) = \lambda e^t e^{\lambda(e^t-1)} + \lambda^2 e^{2t} e^{\lambda(e^t-1)} \Rightarrow E[X^2] = M''(0) = \lambda + \lambda^2$$

$$\text{Var}[X] = \lambda + \lambda^2 - \lambda^2 = \lambda \quad \checkmark$$

---

**Q5.6** State the uniqueness property of MGFs and explain how it can be used to identify a distribution.

**Answer:**

**Uniqueness theorem:** If two random variables X and Y have the same MGF M(t) (defined on an open interval around 0), then they have the same distribution.

**Practical use:** If you derive a MGF and recognise it as the MGF of a known distribution, you can conclude the variable follows that distribution without computing the CDF. For example, if you derive M_Z(t) = e^{λ(eᵗ−1)}, you immediately conclude Z ~ Poisson(λ).

---

**Q5.7** Let X and Y be independent random variables. Show that M_{X+Y}(t) = M_X(t) · M_Y(t).

**Answer:**

$$M_{X+Y}(t) = E[e^{t(X+Y)}] = E[e^{tX} \cdot e^{tY}]$$

Since X and Y are independent, e^{tX} and e^{tY} are also independent, so:

$$E[e^{tX} \cdot e^{tY}] = E[e^{tX}] \cdot E[e^{tY}] = M_X(t) \cdot M_Y(t) \quad \square$$

*Application: If X ~ N(μ₁,σ₁²) and Y ~ N(μ₂,σ₂²) independently, then M_{X+Y}(t) = e^{(μ₁+μ₂)t + (σ₁²+σ₂²)t²/2}, identifying X + Y ~ N(μ₁+μ₂, σ₁²+σ₂²).*

---

**Q5.8** Find the MGF of X ~ Gamma(α, λ) and state for which t it is valid.

**Answer:**

$$M_X(t) = \int_0^\infty e^{tx} \frac{\lambda^\alpha}{\Gamma(\alpha)} x^{\alpha-1}e^{-\lambda x}\,dx = \frac{\lambda^\alpha}{\Gamma(\alpha)} \int_0^\infty x^{\alpha-1} e^{-(\lambda-t)x}\,dx$$

Substituting u = (λ−t)x and using ∫₀^∞ u^{α−1}e^{−u} du = Γ(α):

$$M_X(t) = \frac{\lambda^\alpha}{\Gamma(\alpha)} \cdot \frac{\Gamma(\alpha)}{(\lambda-t)^\alpha} = \left(\frac{\lambda}{\lambda-t}\right)^\alpha, \quad t < \lambda$$

---

**Q5.9** For the MGF of Z ~ N(0,1), i.e. M_Z(t) = e^{t²/2}, use differentiation to find E[Z²] and E[Z⁴].

**Answer:**

$$M_Z(t) = e^{t^2/2}$$

$$M'_Z(t) = te^{t^2/2} \Rightarrow E[Z] = M'(0) = 0 \checkmark$$

$$M''_Z(t) = e^{t^2/2} + t^2 e^{t^2/2} = (1+t^2)e^{t^2/2} \Rightarrow \mathbf{E[Z^2] = 1}$$

$$M'''_Z(t) = (3t + t^3)e^{t^2/2} \Rightarrow E[Z^3] = 0$$

$$M^{(4)}_Z(t) = (3 + 6t^2 + t^4)e^{t^2/2} \Rightarrow \mathbf{E[Z^4] = 3}$$

---

**Q5.10** If X has MGF M_X(t) and Y = aX + b for constants a, b, show that M_Y(t) = e^{bt} M_X(at).

**Answer:**

$$M_Y(t) = E[e^{tY}] = E[e^{t(aX+b)}] = E[e^{abt} \cdot e^{atX}] = e^{bt} E[e^{(at)X}] = e^{bt} M_X(at)$$

*Application: If X ~ N(μ, σ²) with M_X(t) = e^{μt + σ²t²/2}, then Z = (X−μ)/σ has M_Z(t) = e^{−(μ/σ)t} · e^{μ(t/σ) + σ²(t/σ)²/2} = e^{t²/2}, confirming Z ~ N(0,1).*

---

## Chapter 6: Limit Theorems

---

**Q6.1** State Markov's inequality. A non-negative random variable X has E[X] = 5. Find the best upper bound for P(X ≥ 15).

**Answer:**

**Markov's Inequality:** For any non-negative r.v. X and a > 0:

$$P(X \geq a) \leq \frac{E[X]}{a}$$

Applying with E[X] = 5, a = 15:

$$P(X \geq 15) \leq \frac{5}{15} = \frac{1}{3}$$

*This matches answer C from the mock exam. The bound requires only E[X] and works for any non-negative distribution.*

---

**Q6.2** State Chebyshev's inequality. If X has mean μ = 10 and standard deviation σ = 2, find an upper bound for P(|X − 10| ≥ 6).

**Answer:**

**Chebyshev's Inequality:** For any r.v. X with mean μ, variance σ², and any k > 0:

$$P(|X - \mu| \geq k) \leq \frac{\sigma^2}{k^2}$$

Applying with σ² = 4, k = 6:

$$P(|X - 10| \geq 6) \leq \frac{4}{36} = \frac{1}{9} \approx 0.111$$

*If X were normal, the exact answer would be 2·P(Z ≥ 3) ≈ 0.0027, much smaller — Chebyshev gives a conservative (but distribution-free) bound.*

---

**Q6.3** State the Weak Law of Large Numbers (WLLN) precisely.

**Answer:**

Let X₁, X₂, ... be i.i.d. random variables with E[Xᵢ] = μ and Var[Xᵢ] = σ² < ∞. Let X̄ₙ = (1/n)∑ᵢ₌₁ⁿ Xᵢ. Then for every ε > 0:

$$P(|\bar{X}_n - \mu| \geq \varepsilon) \to 0 \quad \text{as } n \to \infty$$

In words: the sample mean **converges in probability** to the population mean.

*Proof sketch: By Chebyshev, P(|X̄ₙ − μ| ≥ ε) ≤ σ²/(nε²) → 0.*

---

**Q6.4** State the Central Limit Theorem (CLT). Give the approximate distribution of X̄ₙ for large n.

**Answer:**

Let X₁, X₂, ... be i.i.d. with mean μ and finite variance σ². Define X̄ₙ = (1/n)∑Xᵢ. Then:

$$\frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} N(0,1) \quad \text{as } n \to \infty$$

Equivalently, **X̄ₙ ≈ N(μ, σ²/n) for large n**.

*The CLT holds regardless of the distribution of Xᵢ (provided σ² < ∞). It explains why the normal distribution is so prevalent in statistics.*

---

**Q6.5** In a CLT application: Xᵢ are i.i.d. with mean 4 and variance 9. Approximate P(X̄₃₆ > 4.5).

**Answer:**

By CLT, X̄₃₆ ≈ N(4, 9/36) = N(4, 0.25), so SE = √0.25 = 0.5.

Standardise:

$$P(\bar{X}_{36} > 4.5) = P\left(Z > \frac{4.5 - 4}{0.5}\right) = P(Z > 1) = 1 - \Phi(1) \approx 1 - 0.8413 = 0.1587$$

---

**Q6.6** Distinguish between convergence in probability and convergence in distribution.

**Answer:**

**Convergence in probability** (Xₙ →_p X): For every ε > 0:

$$P(|X_n - X| \geq \varepsilon) \to 0$$

This is stronger — it says the random variables themselves cluster around X.

**Convergence in distribution** (Xₙ →_d X): For every continuity point x of F_X:

$$F_{X_n}(x) \to F_X(x)$$

This only requires the CDFs to converge, not the variables themselves. The CLT uses convergence in distribution (the standardised sum approaches N(0,1) in distribution).

*Convergence in probability implies convergence in distribution, but not vice versa.*

---

**Q6.7** Suppose Xᵢ ~ Bernoulli(p) i.i.d. Use the CLT to approximate P(∑ᵢ₌₁¹⁰⁰ Xᵢ ≥ 60) when p = 0.5.

**Answer:**

Let S₁₀₀ = ∑Xᵢ. E[S₁₀₀] = 100p = 50, Var[S₁₀₀] = 100p(1−p) = 25, SD = 5.

By CLT, S₁₀₀ ≈ N(50, 25). Using continuity correction (S₁₀₀ ≥ 60 → Y ≥ 59.5):

$$P(S_{100} \geq 60) \approx P\left(Z \geq \frac{59.5 - 50}{5}\right) = P(Z \geq 1.9) = 1 - \Phi(1.9) \approx 0.0287$$

---

**Q6.8** Apply Chebyshev's inequality to construct a bound: what sample size n is needed so that P(|X̄ₙ − μ| ≥ 0.1) ≤ 0.05, if σ² = 1?

**Answer:**

By Chebyshev: P(|X̄ₙ − μ| ≥ ε) ≤ σ²/(nε²). We want:

$$\frac{1}{n(0.1)^2} \leq 0.05$$

$$\frac{1}{0.01n} \leq 0.05 \implies n \geq \frac{1}{0.01 \times 0.05} = \frac{1}{0.0005} = 2000$$

So we need **n ≥ 2000**. (If we used the CLT instead, we'd only need n ≈ 384 — Chebyshev is conservative.)

---

**Q6.9** Let Xₙ → μ in probability. Show that X̄ₙ² →_p μ².

**Answer:**

By the Continuous Mapping Theorem: if g is a continuous function and Xₙ →_p c (a constant), then g(Xₙ) →_p g(c).

Since g(x) = x² is continuous and X̄ₙ →_p μ (by WLLN), we have:

$$\bar{X}_n^2 \xrightarrow{p} \mu^2$$

*Alternatively: |X̄ₙ² − μ²| = |X̄ₙ − μ||X̄ₙ + μ|. For large n, |X̄ₙ − μ| is small with high probability and |X̄ₙ + μ| is bounded, so the product → 0.*

---

**Q6.10** A fair die is rolled 300 times. Let X̄ be the sample mean. Find (approximately) P(3.4 < X̄ < 3.6).

**Answer:**

For a fair die: E[X] = 7/2 = 3.5, and E[X²] = (1²+2²+...+6²)/6 = 91/6, so Var[X] = 91/6 − (7/2)² = 91/6 − 49/4 = 182/12 − 147/12 = 35/12.

By CLT: X̄₃₀₀ ≈ N(3.5, (35/12)/300) = N(3.5, 7/720).

Standard error = √(7/720) ≈ 0.0986.

$$P(3.4 < \bar{X} < 3.6) = P\left(\frac{3.4-3.5}{0.0986} < Z < \frac{3.6-3.5}{0.0986}\right) = P(-1.015 < Z < 1.015)$$

$$\approx 2\Phi(1.015) - 1 \approx 2(0.845) - 1 = 0.69$$

---

## Chapter 7: Estimation Methods

---

**Q7.1** Suppose Y₁,...,Yₙ ~ Exponential(λ). Derive the MLE for λ.

**Answer:**

**Likelihood:** L(λ) = ∏ᵢ λe^{−λyᵢ} = λⁿe^{−λΣyᵢ}

**Log-likelihood:** ℓ(λ) = n log λ − λΣyᵢ

**Score equation:** dℓ/dλ = n/λ − Σyᵢ = 0

**MLE:**

$$\hat{\lambda}_{MLE} = \frac{n}{\sum y_i} = \frac{1}{\bar{y}}$$

*Check second derivative: d²ℓ/dλ² = −n/λ² < 0 ✓ (confirms maximum).*

---

**Q7.2** For the exponential model above, derive the method of moments estimator for λ.

**Answer:**

The first theoretical moment of Exponential(λ) is E[Y] = 1/λ.

Equate to sample moment: X̄ = 1/λ̂

$$\hat{\lambda}_{MM} = \frac{1}{\bar{Y}} = \frac{n}{\sum Y_i}$$

In this case, **the MLE and the MOM estimator coincide.**

---

**Q7.3** Suppose Xᵢ ~ N(0, σ²) i.i.d. and we estimate σ² with T = (1/n)∑Xᵢ². Is T unbiased?

**Answer:**

$$E[T] = \frac{1}{n} \sum_{i=1}^n E[X_i^2] = \frac{1}{n} \cdot n \cdot \text{Var}[X_i] = \sigma^2$$

(Since E[Xᵢ] = 0, we have E[Xᵢ²] = Var[Xᵢ] = σ².)

**T is unbiased** for σ². This matches answer **A** from the mock exam.

*Note: T is not the same as the sample variance S² = ∑(Xᵢ−X̄)²/(n−1) since the mean is known to be 0 here.*

---

**Q7.4** For X₁,...,Xₙ ~ Uniform(a, 1), use the method of moments to estimate a given observations 0.7, 0.8, 0.9.

**Answer:**

For Uniform(a, 1): E[X] = (a+1)/2.

Setting X̄ = (a+1)/2: â = 2X̄ − 1.

Sample mean: X̄ = (0.7 + 0.8 + 0.9)/3 = 2.4/3 = 0.8.

$$\hat{a} = 2(0.8) - 1 = 0.6$$

*This matches answer B from the mock exam.*

---

**Q7.5** Define (i) bias, (ii) MSE, and (iii) consistency of an estimator θ̂ₙ for parameter θ.

**Answer:**

**(i) Bias:** Bias(θ̂ₙ) = E[θ̂ₙ] − θ. An estimator is **unbiased** if Bias = 0.

**(ii) MSE (Mean Squared Error):**

$$\text{MSE}(\hat{\theta}_n) = E[(\hat{\theta}_n - \theta)^2] = \text{Var}(\hat{\theta}_n) + [\text{Bias}(\hat{\theta}_n)]^2$$

**(iii) Consistency:** θ̂ₙ is consistent if θ̂ₙ →_p θ as n → ∞, i.e., for every ε > 0: P(|θ̂ₙ − θ| ≥ ε) → 0. A sufficient condition is MSE → 0.

---

**Q7.6** Define Fisher information I(θ) and state the Cramér-Rao lower bound.

**Answer:**

**Fisher Information:**

$$I(\theta) = -E\left[\frac{\partial^2 \ell(\theta)}{\partial \theta^2}\right] = E\left[\left(\frac{\partial \ell(\theta)}{\partial \theta}\right)^2\right]$$

**Cramér-Rao Lower Bound:** For any unbiased estimator θ̂:

$$\text{Var}(\hat{\theta}) \geq \frac{1}{I(\theta)}$$

An unbiased estimator achieving this bound is called **efficient**. The MLE is asymptotically efficient.

---

**Q7.7** For the density f(y|θ) = θy^{−θ−1}, y ≥ 1, compute the Fisher information I(θ).

**Answer:**

Log-likelihood for one observation: ℓ(θ) = log θ − (θ+1) log y

$$\frac{\partial \ell}{\partial \theta} = \frac{1}{\theta} - \log y, \qquad \frac{\partial^2 \ell}{\partial \theta^2} = -\frac{1}{\theta^2}$$

$$I(\theta) = -E\left[-\frac{1}{\theta^2}\right] = \frac{1}{\theta^2}$$

For n observations: I_n(θ) = n/θ², so Var(θ̂_MLE) ≈ θ²/n.

---

**Q7.8** Suppose λ ~ Gamma(2α, β) is used as a prior, and data Y₁,...,Yₙ ~ Exponential(λ). Derive the posterior distribution.

**Answer:**

**Prior:** π(λ) ∝ λ^{2α−1} e^{−βλ} (Gamma shape-rate)

**Likelihood:** L(λ|y) = λⁿe^{−λΣyᵢ}

**Posterior:**

$$\pi(\lambda|\mathbf{y}) \propto \lambda^n e^{-\lambda \sum y_i} \cdot \lambda^{2\alpha-1} e^{-\beta\lambda} = \lambda^{(2\alpha+n)-1} e^{-(\beta+\sum y_i)\lambda}$$

This is the kernel of a **Gamma(2α + n, β + Σyᵢ)** distribution.

**Posterior mean (Bayes estimator):**

$$\hat{\lambda}_{Bayes} = \frac{2\alpha + n}{\beta + \sum y_i}$$

For n=10, Σyᵢ=3, α=β=2: λ̂_Bayes = 14/5 = 2.8.

---

**Q7.9** Explain the invariance property of the MLE. If λ̂_MLE is the MLE of λ in an exponential model, what is the MLE of the mean 1/λ?

**Answer:**

**Invariance Property:** If θ̂ is the MLE of θ and g is a function, then g(θ̂) is the MLE of g(θ).

Since λ̂_MLE = 1/Ȳ (from Q7.1), the MLE of the mean μ = 1/λ is:

$$\hat{\mu}_{MLE} = g(\hat{\lambda}_{MLE}) = \frac{1}{\hat{\lambda}_{MLE}} = \bar{Y}$$

*Note: The invariance property applies to MLEs but not generally to unbiased estimators — the MLE of 1/λ is Ȳ, which is unbiased for 1/λ, but this is a coincidence.*

---

**Q7.10** Compute the MLE for the Pareto model f(y|θ) = θy^{−θ−1}, y ≥ 1, given a sample y₁,...,yₙ.

**Answer:**

**Log-likelihood:**

$$\ell(\theta) = n\log\theta - (\theta+1)\sum_{i=1}^n \log y_i$$

**Score equation:**

$$\frac{d\ell}{d\theta} = \frac{n}{\theta} - \sum_{i=1}^n \log y_i = 0$$

**MLE:**

$$\hat{\theta}_{MLE} = \frac{n}{\sum_{i=1}^n \log y_i}$$

*Check: d²ℓ/dθ² = −n/θ² < 0 ✓. This is the reciprocal of the geometric mean of log yᵢ.*

---

## Chapter 8: Data and Statistical Modelling

---

**Q8.1** Define the breakdown point of an estimator. Compare the breakdown points of the sample mean and the sample median.

**Answer:**

The **breakdown point** is the fraction of observations that can be replaced by arbitrarily extreme values before the estimator becomes completely unreliable.

**Sample mean:** Breakdown point = 1/n → 0. A single extreme outlier can make X̄ arbitrarily large.

**Sample median:** Breakdown point = 0.5. Up to 50% of observations can be corrupted before the median breaks down, making it a highly robust estimator.

*The median is preferred when the data may contain outliers; the mean is preferred when the data is clean because it is more efficient under normality.*

---

**Q8.2** Define the pth quantile (or percentile) of a sample. What is the interquartile range (IQR)?

**Answer:**

The **pth quantile** q_p is a value such that approximately a fraction p of the observations fall below it.

Special cases: q_{0.25} = lower quartile (Q1), q_{0.5} = median, q_{0.75} = upper quartile (Q3).

**IQR = Q3 − Q1 = q_{0.75} − q_{0.25}**

The IQR is a robust measure of spread (breakdown point 25%). It is used in box plots and in the definition of outliers (values beyond Q1 − 1.5·IQR or Q3 + 1.5·IQR).

---

**Q8.3** Explain why the sample skewness and kurtosis are sensitive to outliers.

**Answer:**

The sample skewness involves (Xᵢ − X̄)³ and kurtosis involves (Xᵢ − X̄)⁴. Raising deviations to high powers amplifies the contribution of extreme values:

- An outlier far from the mean contributes a very large term to ∑(Xᵢ−X̄)³ or ∑(Xᵢ−X̄)⁴.
- These moments are also not "order-based" — they depend on exact values, not just ranks.

As a result, a single outlier can drastically change the estimated skewness or kurtosis, making these statistics non-robust.

---

**Q8.4** A dataset appears right-skewed. Suggest a transformation that might make it more symmetric (closer to normal), and explain why.

**Answer:**

Common choices for right-skewed data:

- **Log transformation:** Y = log(X). Compresses large values, spreads small values.
- **Square root:** Y = √X. Milder compression.
- **Box-Cox transformation:** Y = (X^λ − 1)/λ, which unifies these (λ = 0 gives log, λ = 1/2 gives square root).

**Why it works:** Right skew occurs when the distribution has a long right tail. The log function grows slowly, so it compresses large values more than small ones, pulling the tail in. After transformation, the data often passes normality tests more easily.

---

**Q8.5** Explain the difference between a statistical model and the data-generating process (DGP).

**Answer:**

The **data-generating process (DGP)** is the true (unknown) mechanism that produced the observed data. It may be extremely complex.

A **statistical model** is a simplified, parametric family of distributions assumed to approximate the DGP. For example, we might model heights as Y ~ N(μ, σ²) even though the true DGP involves genetics, nutrition, and many other factors.

Key distinction: The model is always an approximation. "All models are wrong, but some are useful" (Box). The goal is to choose a model simple enough to be estimable yet rich enough to capture the key features of the DGP.

---

**Q8.6** What are the four main types of uncertainty in a statistical model? Give a one-sentence explanation of each.

**Answer:**

1. **Aleatoric uncertainty (irreducible randomness):** The inherent randomness in the data-generating process that cannot be reduced no matter how much data is collected (captured by σ² in regression).

2. **Parameter uncertainty:** Uncertainty about the true parameter values (e.g., μ, σ²), which decreases as sample size grows.

3. **Model uncertainty:** Uncertainty about whether the assumed model family is correct (e.g., is normality justified?).

4. **Measurement/data uncertainty:** Errors and noise in how the data were recorded or collected.

---

**Q8.7** Describe what a Q-Q plot is and what patterns indicate departures from normality.

**Answer:**

A **Q-Q (quantile-quantile) plot** compares the empirical quantiles of the data against the theoretical quantiles of the assumed distribution (usually normal). If the data follows the assumed distribution, the points fall approximately on a 45° straight line.

**Departures:**

- **Heavy tails (leptokurtosis):** S-shape — points curve above the line at both ends.
- **Light tails (platykurtosis):** Reverse S-shape.
- **Right skew:** Points curve above the line at the right end.
- **Left skew:** Points curve below the line at the left end.
- **Outliers:** Single points far off the line at either extreme.

---

**Q8.8** What does it mean for an estimator to be asymptotically unbiased? Give an example.

**Answer:**

An estimator θ̂ₙ is **asymptotically unbiased** if Bias(θ̂ₙ) = E[θ̂ₙ] − θ → 0 as n → ∞, even if it is biased for finite n.

**Example:** The biased sample variance m₂ = (1/n)∑(Xᵢ−X̄)²:

$$E[m_2] = \frac{n-1}{n}\sigma^2 = \sigma^2 - \frac{\sigma^2}{n}$$

The bias is −σ²/n → 0 as n → ∞, so m₂ is asymptotically unbiased for σ².

---

**Q8.9** What is the purpose of diagnostic plots in statistical modelling? Name three types used in regression.

**Answer:**

Diagnostic plots check whether the model assumptions are met for the fitted model. If assumptions are violated, inference (confidence intervals, hypothesis tests) may be unreliable.

Three common regression diagnostic plots:

1. **Residuals vs Fitted values:** Checks linearity and homoscedasticity. Should show no pattern.
2. **Q-Q plot of residuals:** Checks normality assumption. Points should lie on the line.
3. **Scale-Location plot (√|residuals| vs fitted):** Checks homoscedasticity. Should show a horizontal band.

---

**Q8.10** Explain what a "trimmed mean" is and why it is more robust than the ordinary mean.

**Answer:**

The **α-trimmed mean** is computed by removing the α proportion of the smallest and α proportion of the largest observations, then taking the mean of the remaining values.

For example, the 10% trimmed mean removes the lowest 10% and highest 10% of the sample and averages the middle 80%.

**Why more robust:** By discarding extreme observations before computing the mean, the trimmed mean is unaffected by a moderate fraction of outliers. Its breakdown point is α (compared to 1/n for the plain mean). It retains higher efficiency than the median under near-normal data while being more robust than the mean.

---

## Chapter 9: Hypothesis Testing

---

**Q9.1** Define Type I error, Type II error, the significance level α, and the power of a test.

**Answer:**

- **Type I error:** Rejecting H₀ when H₀ is true. Probability = α (significance level).
- **Type II error:** Failing to reject H₀ when H₀ is false. Probability = β.
- **Significance level α:** P(Reject H₀ | H₀ true) = α. Typically set at 0.05 or 0.01.
- **Power:** P(Reject H₀ | H₀ false) = 1 − β. Higher power is better; it measures the test's ability to detect a false null hypothesis.

These four quantities are related: reducing α (fewer false positives) increases β (more false negatives) for fixed n; increasing n reduces both.

---

**Q9.2** State the Neyman-Pearson Lemma and explain when it applies.

**Answer:**

**Setting:** Testing H₀ : θ = θ₀ vs H₁ : θ = θ₁ (both simple hypotheses).

**Lemma:** Among all tests of size α, the most powerful test has critical region:

$$C_1 = \left\{\mathbf{x} : \frac{L(\theta_0; \mathbf{x})}{L(\theta_1; \mathbf{x})} \leq c\right\}$$

where c is chosen so that P(X ∈ C₁ | θ₀) = α.

**When it applies:** Only when *both* H₀ and H₁ are **simple** (specify the distribution completely). For composite alternatives, we use the Likelihood Ratio Test (LRT), which extends this idea.

---

**Q9.3** Define the likelihood ratio statistic Λ and state its asymptotic distribution under H₀.

**Answer:**

Let Θ₀ ⊂ Θ be the null parameter space. The likelihood ratio statistic is:

$$\lambda(\mathbf{x}) = \frac{\sup_{\theta \in \Theta_0} L(\theta; \mathbf{x})}{\sup_{\theta \in \Theta} L(\theta; \mathbf{x})} \in [0,1]$$

The test statistic is Λ = −2 log λ(x).

**Wilks' Theorem:** Under H₀ and regularity conditions:

$$\Lambda \xrightarrow{d} \chi^2_q \quad \text{where } q = \dim(\Theta) - \dim(\Theta_0)$$

*From the mock exam: the key property is that Λ lies in [0,1] (numerator ≤ denominator since Θ₀ ⊂ Θ), so log Λ ≤ 0, and −2 log Λ ≥ 0 (compatible with chi-squared).*

---

**Q9.4** For testing H₀ : λ₁ = λ₂ vs H₁ : λ₁ ≠ λ₂ with Xᵢ ~ Poisson(λ₁) and Yⱼ ~ Poisson(λ₂), state the approximate distribution of the LRT statistic Λ = −2 log λ.

**Answer:**

The full parameter space Θ = {(λ₁, λ₂) : λ₁, λ₂ > 0} has **dimension 2**.

The null space Θ₀ = {(λ₁, λ₂) : λ₁ = λ₂} has **dimension 1** (only one free parameter λ₀).

By Wilks' theorem:

$$\Lambda = -2\log\lambda \xrightarrow{d} \chi^2_{2-1} = \chi^2_1$$

We reject H₀ at level α when Λ > χ²_{1,α} (e.g., > 3.84 for α = 0.05).

---

**Q9.5** For testing H₀ : μ = μ₀ with known variance σ² and a normal population, state the test statistic and describe the rejection region for a two-sided test.

**Answer:**

**Test statistic:**

$$Z = \frac{\bar{X} - \mu_0}{\sigma/\sqrt{n}} \sim N(0,1) \text{ under } H_0$$

**Two-sided rejection region** at significance level α:

$$|Z| > z_{\alpha/2}$$

(e.g., |Z| > 1.96 for α = 0.05)

If σ² is **unknown**, replace with the t-test: T = (X̄ − μ₀)/(S/√n) ~ t_{n−1} under H₀.

---

**Q9.6** Explain the p-value. At what threshold do we reject H₀?

**Answer:**

The **p-value** is the probability of observing a test statistic at least as extreme as the one computed, assuming H₀ is true:

p-value = P(Test statistic as extreme as observed | H₀)

**Decision rule:** Reject H₀ if **p-value < α** (where α is the pre-chosen significance level).

Interpretation: A small p-value means the observed data would be very unlikely if H₀ were true, providing evidence against H₀. A p-value is NOT the probability that H₀ is true.

---

**Q9.7** A chi-squared goodness-of-fit test is used to test if data follows a specified distribution. State the test statistic and its degrees of freedom.

**Answer:**

With k categories and observed counts O₁,...,Oₖ versus expected counts E₁,...,Eₖ (where Eᵢ = npᵢ):

$$\chi^2 = \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i}$$

**Under H₀** (approximately, for large n): χ² ~ χ²_{k−1} if all parameters are known, or χ²_{k−1−m} if m parameters were estimated from the data.

**Rule of thumb:** Each expected count should be at least 5 for the approximation to be valid.

---

**Q9.8** For testing H₀ : σ₁² = σ₂² using two independent normal samples, state the test statistic and its distribution under H₀.

**Answer:**

Let S₁² and S₂² be the sample variances from samples of size n₁ and n₂.

**Test statistic:**

$$F = \frac{S_1^2}{S_2^2} \sim F(n_1-1,\; n_2-1) \quad \text{under } H_0$$

**Rejection region** (two-sided, level α): F < F_{n₁-1, n₂-1, 1-α/2} or F > F_{n₁-1, n₂-1, α/2}.

*This follows because (nᵢ−1)Sᵢ²/σᵢ² ~ χ²_{nᵢ−1}, and the ratio of two independent scaled chi-squared variables is F-distributed.*

---

**Q9.9** Define what it means for a test to be "uniformly most powerful" (UMP). When does the Neyman-Pearson construction give a UMP test?

**Answer:**

A test of size α is **uniformly most powerful (UMP)** if it has the highest power among all size-α tests for every value of θ in the alternative parameter space Θ₁.

The Neyman-Pearson Lemma guarantees a UMP test when:
- H₀ and H₁ are both **simple** (point hypotheses).

For composite H₁, a UMP test exists only in special cases — typically when the likelihood ratio is monotone in the sufficient statistic (one-sided tests in exponential family models). As stated in the mock exam, "if H₀ is simple and H₁ is composite, the LRT is **not always** UMP."

---

**Q9.10** Consider testing H₀ : p = 0.5 vs H₁ : p ≠ 0.5 for a coin with n = 100 tosses. You observe X = 60 heads. Compute the approximate p-value and give a conclusion at α = 0.05.

**Answer:**

Under H₀: X ~ Binomial(100, 0.5), with mean 50 and SD = √(100·0.5·0.5) = 5.

By CLT, Z = (X − 50)/5 ~ N(0,1) approximately.

Observed: Z_obs = (60 − 50)/5 = 2.0.

**p-value** (two-sided): p = P(|Z| > 2.0) = 2(1 − Φ(2.0)) ≈ 2(0.0228) = **0.0456**.

**Conclusion:** Since 0.0456 < 0.05, we **reject H₀** at the 5% level. There is significant evidence that the coin is biased.

---

## Chapter 10: Linear Regression

---

**Q10.1** State the multiple linear regression model in matrix form, defining all components.

**Answer:**

$$\mathbf{Y} = X\boldsymbol{\beta} + \boldsymbol{\varepsilon}$$

where:

- Y = (Y₁,...,Yₙ)ᵀ: response vector (n × 1)
- X: design matrix (n × (p+1)), with first column all 1s
- β = (β₀, β₁,...,βₚ)ᵀ: coefficient vector ((p+1) × 1)
- ε: error vector (n × 1)

**Assumptions:** E[ε] = 0, Cov[ε] = σ²Iₙ (errors are uncorrelated, homoscedastic). For inference we add ε ~ N(0, σ²Iₙ).

---

**Q10.2** Derive the OLS estimator β̂ = (XᵀX)⁻¹XᵀY.

**Answer:**

Minimise r(β) = (Y − Xβ)ᵀ(Y − Xβ) = YᵀY − 2βᵀXᵀY + βᵀXᵀXβ.

Taking the gradient with respect to β and setting to zero:

$$\frac{\partial r}{\partial \boldsymbol{\beta}} = -2X^\top \mathbf{Y} + 2X^\top X\boldsymbol{\beta} = \mathbf{0}$$

The **normal equations** are: XᵀXβ̂ = XᵀY.

Assuming rank(X) = p+1 (XᵀX is invertible):

$$\hat{\boldsymbol{\beta}} = (X^\top X)^{-1}X^\top \mathbf{Y}$$

---

**Q10.3** Show that the OLS estimator β̂ is unbiased.

**Answer:**

$$E[\hat{\boldsymbol{\beta}}] = E[(X^\top X)^{-1}X^\top \mathbf{Y}] = (X^\top X)^{-1}X^\top E[\mathbf{Y}]$$

Since E[Y] = Xβ:

$$E[\hat{\boldsymbol{\beta}}] = (X^\top X)^{-1}X^\top X\boldsymbol{\beta} = I_{p+1}\boldsymbol{\beta} = \boldsymbol{\beta} \quad \square$$

---

**Q10.4** Show that σ̂² = ε̂ᵀε̂/(n−p−1) is an unbiased estimator of σ².

**Answer:**

The key result is that ε̂ᵀε̂/σ² ~ χ²_{n-p-1}, so E[ε̂ᵀε̂] = (n−p−1)σ².

This uses the fact that ε̂ = (I − H)Y where H = X(XᵀX)⁻¹Xᵀ is the hat matrix, and (I−H) is idempotent with rank n−p−1.

Therefore:

$$E\left[\hat{\sigma}^2\right] = E\left[\frac{\hat{\boldsymbol{\varepsilon}}^\top \hat{\boldsymbol{\varepsilon}}}{n-p-1}\right] = \frac{(n-p-1)\sigma^2}{n-p-1} = \sigma^2 \quad \checkmark$$

---

**Q10.5** In simple linear regression (p=1), state the formulas for β̂₁ and β̂₀.

**Answer:**

$$\hat{\beta}_1 = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2} = \frac{S_{xy}}{S_{xx}}$$

$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$$

**Unbiasedness of β̂₁:** Substitute yᵢ = β₀ + β₁xᵢ + εᵢ:

$$\hat{\beta}_1 = \beta_1 + \frac{\sum(x_i-\bar{x})\varepsilon_i}{\sum(x_i-\bar{x})^2}$$

Taking expectation and using E[εᵢ] = 0 gives E[β̂₁] = β₁.

---

**Q10.6** State the Gauss-Markov theorem and explain its significance.

**Answer:**

**Theorem:** Under the model assumptions (E[ε]=0, Cov[ε]=σ²Iₙ, X is full rank), the OLS estimator β̂ is the **Best Linear Unbiased Estimator (BLUE)** of β. That is, among all linear unbiased estimators, β̂ has the smallest variance.

**Significance:** This result does NOT require normality of errors — only zero mean, constant variance, and uncorrelated errors. It guarantees that OLS is optimal in a broad class, justifying its widespread use. With the additional normality assumption, OLS is also the maximum likelihood estimator.

---

**Q10.7** Define the hat matrix H and list two of its key properties.

**Answer:**

$$H = X(X^\top X)^{-1}X^\top$$

This "puts the hat on Y": Ŷ = HY.

**Properties:**

1. **Symmetric:** H = Hᵀ
2. **Idempotent:** H² = H (applying the projection twice is the same as once)

Additional: rank(H) = p+1, the diagonal elements hᵢᵢ ∈ [1/n, 1] are called **leverages** and identify influential observations.

---

**Q10.8** Define R² (coefficient of determination) and interpret its values.

**Answer:**

$$R^2 = 1 - \frac{SS_{res}}{SS_{total}} = \frac{SS_{reg}}{SS_{total}}$$

where SSₜₒₜₐₗ = SSᵣₑᵍ + SSᵣₑₛ.

**Interpretation:**

- R² ∈ [0, 1].
- R² = 1: the model explains all variation in Y (perfect fit).
- R² = 0: the model explains none of the variation (as good as just using Ȳ).
- R² = 0.8 means 80% of the variance in Y is explained by the predictors.

*Caution: R² always increases when you add predictors. Use **adjusted R²** to penalise for extra parameters.*

---

**Q10.9** Explain multicollinearity: what causes it, what are its consequences, and how is it detected?

**Answer:**

**Cause:** Two or more predictors are strongly linearly correlated with each other (e.g., income and wealth, height in cm and height in inches).

**Consequences:**
- XᵀX becomes nearly singular → (XᵀX)⁻¹ has large entries → large variances for β̂.
- Individual coefficient estimates are unstable and have large standard errors.
- Hypothesis tests for individual coefficients may fail even when the overall F-test is significant.
- Signs of coefficients may be counterintuitive.

**Detection:**
- Correlation matrix of predictors (large |r_{ij}| suggests pairwise collinearity).
- **Variance Inflation Factor (VIF):** VIF_j = 1/(1 − R²_j) where R²_j is R² from regressing Xⱼ on all other predictors. VIF > 5 or 10 is a warning sign.

---

**Q10.10** Write the t-statistic for testing H₀ : βⱼ = 0. Under what distribution is it evaluated?

**Answer:**

The t-statistic for coefficient βⱼ is:

$$t_j = \frac{\hat{\beta}_j}{\text{SE}(\hat{\beta}_j)} = \frac{\hat{\beta}_j}{\hat{\sigma}\sqrt{(X^\top X)^{-1}_{jj}}}$$

Under H₀ : βⱼ = 0 and assuming ε ~ N(0, σ²Iₙ):

$$t_j \sim t_{n-p-1}$$

Reject H₀ at level α if |tⱼ| > t_{n−p−1, α/2}. In R output, this corresponds to the column of p-values in the summary table.

---

## Chapter 11: One-Way ANOVA

---

**Q11.1** State the one-way ANOVA model and list its assumptions.

**Answer:**

**Model:**

$$Y_{ij} = \mu + \tau_j + \varepsilon_{ij}, \quad i = 1,\ldots,n_j,\; j = 1,\ldots,k, \quad \text{s.t.} \sum_{j=1}^k n_j\tau_j = 0$$

where μ is the overall mean, τⱼ is the treatment effect for group j, and εᵢⱼ is random error.

**Assumptions:**
1. εᵢⱼ are independently distributed
2. εᵢⱼ ~ N(0, σ²)
3. Var(εᵢⱼ) = σ² for all i, j (equal variance / homoscedasticity)
4. Treatment effects are additive

**Hypotheses:** H₀ : τ₁ = τ₂ = ··· = τₖ = 0 vs H₁ : some τⱼ ≠ 0.

---

**Q11.2** For the data below, compute the group means and overall mean:

| Group | Observations |
|-------|-------------|
| 1 | 4, 6 |
| 2 | 5, 7, 9 |
| 3 | 8, 10 |

**Answer:**

$$\bar{y}_{1\bullet} = \frac{4+6}{2} = 5, \quad \bar{y}_{2\bullet} = \frac{5+7+9}{3} = 7, \quad \bar{y}_{3\bullet} = \frac{8+10}{2} = 9$$

$$\bar{y}_{\bullet\bullet} = \frac{4+6+5+7+9+8+10}{7} = \frac{49}{7} = 7$$

---

**Q11.3** For the dataset in Q11.2, compute SSᵣₑᵍ, SSᵣₑₛ, SStotal and verify the ANOVA identity.

**Answer:**

$$SS_{reg} = \sum_{j=1}^3 n_j(\bar{y}_{j\bullet} - \bar{y}_{\bullet\bullet})^2 = 2(5-7)^2 + 3(7-7)^2 + 2(9-7)^2 = 8 + 0 + 8 = 16$$

$$SS_{res} = \sum_{i,j}(y_{ij}-\bar{y}_{j\bullet})^2 = (4-5)^2+(6-5)^2+(5-7)^2+(7-7)^2+(9-7)^2+(8-9)^2+(10-9)^2$$
$$= 1+1+4+0+4+1+1 = 12$$

$$SS_{total} = \sum_{i,j}(y_{ij}-\bar{y}_{\bullet\bullet})^2 = (4-7)^2+(6-7)^2+(5-7)^2+(7-7)^2+(9-7)^2+(8-7)^2+(10-7)^2$$
$$= 9+1+4+0+4+1+9 = 28$$

**ANOVA identity:** SSₜₒₜₐₗ = SSᵣₑᵍ + SSᵣₑₛ = 16 + 12 = 28 ✓

---

**Q11.4** For the dataset in Q11.2, construct the ANOVA table and compute the F-statistic.

**Answer:**

n = 7 total observations, k = 3 groups.

| Source | SS | df | MS | F |
|--------|-----|-----|-----|---|
| Treatment | 16 | k−1 = 2 | 16/2 = 8 | 8/3 ≈ 2.67 |
| Error | 12 | n−k = 4 | 12/4 = 3 | |
| Total | 28 | n−1 = 6 | | |

**F = MSᵣₑᵍ / MSᵣₑₛ = 8/3 ≈ 2.67 ~ F(2, 4) under H₀.**

The critical value F(2,4) at α = 0.05 is approximately 6.94. Since 2.67 < 6.94, we **fail to reject H₀** — insufficient evidence of a treatment effect.

---

**Q11.5** State the distributions of SSᵣₑᵍ/σ² and SSᵣₑₛ/σ² in the ANOVA framework.

**Answer:**

Under the ANOVA model (11.1):

**Error sum of squares:**

$$\frac{SS_{res}}{\sigma^2} \sim \chi^2_{n-k}$$

(always, regardless of whether H₀ holds)

**Regression sum of squares** (under H₀ : τ₁ = ··· = τₖ = 0):

$$\frac{SS_{reg}}{\sigma^2} \sim \chi^2_{k-1}$$

**Moreover:** SSᵣₑᵍ and SSᵣₑₛ are **independent** (Cochran's theorem).

Therefore, under H₀:

$$F = \frac{SS_{reg}/(k-1)}{SS_{res}/(n-k)} \sim F(k-1, n-k)$$

---

**Q11.6** Show that MSᵣₑₛ = SSᵣₑₛ/(n−k) is an unbiased estimator of σ².

**Answer:**

From the distributional result SSᵣₑₛ/σ² ~ χ²_{n-k}, and since E[χ²ᵥ] = ν:

$$E\left[\frac{SS_{res}}{\sigma^2}\right] = n - k$$

$$E[SS_{res}] = (n-k)\sigma^2$$

$$E[MS_{res}] = E\left[\frac{SS_{res}}{n-k}\right] = \sigma^2 \quad \square$$

---

**Q11.7** Explain the null and alternative hypotheses in one-way ANOVA. What does it mean practically when H₀ is rejected?

**Answer:**

$$H_0 : \tau_1 = \tau_2 = \cdots = \tau_k = 0 \quad \text{vs} \quad H_1 : \tau_j \neq 0 \text{ for some } j$$

Equivalently, since the group mean is μ + τⱼ:

$$H_0 : \mu_1 = \mu_2 = \cdots = \mu_k \quad \text{(all group means are equal)}$$

When H₀ is **rejected**, we conclude that at least one group mean differs significantly from the others. We do **not** know which groups differ — a **post-hoc test** (e.g., Tukey, Bonferroni) is required to make pairwise comparisons.

---

**Q11.8** What are the ANOVA diagnostic plots, and what do they check?

**Answer:**

The same assumptions as regression apply (normality, constant variance, independence). Key plots:

1. **Residuals vs Group (or Fitted values):** Checks constant variance — the spread of residuals should be similar across groups. Funnel patterns indicate heteroscedasticity.

2. **Normal Q-Q plot of residuals:** Checks normality — points should lie on a straight line.

3. **Box plots by group:** Visually compare the spread across groups; similar box widths support the equal-variance assumption.

Formal tests for equal variance include **Levene's test** (robust) and **Bartlett's test** (sensitive to non-normality).

---

**Q11.9** What is E[SSᵣₑᵍ] in general (not just under H₀)?

**Answer:**

From the general result in the notes:

$$E[SS_{reg}] = (k-1)\sigma^2 + \sum_{j=1}^k n_j \tau_j^2$$

**Under H₀** (all τⱼ = 0): E[SSᵣₑᵍ] = (k−1)σ²

**Under H₁** (some τⱼ ≠ 0): E[SSᵣₑᵍ] > (k−1)σ²

This explains why a large F-statistic provides evidence against H₀ — the numerator MSᵣₑᵍ is inflated by the true treatment effects, while the denominator MSᵣₑₛ always estimates σ² regardless.

---

**Q11.10** Explain how one-way ANOVA is a special case of multiple linear regression with a design matrix consisting of dummy variables.

**Answer:**

For k groups, encode group membership using k−1 dummy variables (one group is the reference). For k = 3 groups (n = 7 observations as in Q11.2):

$$X = \begin{pmatrix}1&1&0\\1&1&0\\1&0&1\\1&0&1\\1&0&1\\1&0&0\\1&0&0\end{pmatrix}, \quad \boldsymbol{\beta} = \begin{pmatrix}\mu+\tau_3\\\tau_1-\tau_3\\\tau_2-\tau_3\end{pmatrix}$$

The overall F-test in regression (H₀ : β₁ = β₂ = 0) corresponds exactly to the ANOVA F-test (H₀ : τ₁ = τ₂ = τ₃). The ANOVA table is the regression ANOVA table. The OLS estimator gives β̂ that is equivalent to the group means ȳⱼ•.

---

*End of Question Bank — 110 Questions across 11 Chapters*

---

**Summary of Chapters:**

| Chapter | Topic | Questions |
|---------|-------|-----------|
| 1 | Probability Distributions (Gamma, F, Joint) | Q1.1–Q1.10 |
| 2 | Moments (Raw, Central, Covariance, Correlation) | Q2.1–Q2.10 |
| 3 | Functions of a Random Variable (CDF, Jacobian) | Q3.1–Q3.10 |
| 4 | Random Vectors (Mean, Covariance Matrix, MVN) | Q4.1–Q4.10 |
| 5 | Moment Generating Functions | Q5.1–Q5.10 |
| 6 | Limit Theorems (Markov, Chebyshev, WLLN, CLT) | Q6.1–Q6.10 |
| 7 | Estimation Methods (MLE, MOM, Bayes, Fisher) | Q7.1–Q7.10 |
| 8 | Data and Statistical Modelling (Robustness, Diagnostics) | Q8.1–Q8.10 |
| 9 | Hypothesis Testing (NP Lemma, LRT, t, F, χ²) | Q9.1–Q9.10 |
| 10 | Linear Regression (OLS, Inference, Model Selection) | Q10.1–Q10.10 |
| 11 | One-Way ANOVA (F-test, SS decomposition) | Q11.1–Q11.10 |
