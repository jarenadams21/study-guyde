# Calculus and Physical Equations: A Lesson Plan
## From High School Algebra to Frontier Nuclear Physics

> *"It seems that if one is working from the point of view of getting beauty in one's equations,
> and if one has really a sound insight, one is on a sure line of progress."*
> — P.A.M. Dirac, 1963

---

## How to Use This Document

This lesson is written so that **high school algebra is the only prerequisite**. Every concept is
introduced from scratch, defined in plain language, and then connected to a real equation from this
project. By the end you will have built, step by step, every mathematical tool needed to read,
derive, and explore the frontier physics problems in `PROPOSED_DIRECTIONS.md`.

The progression is deliberate:

```
PART I — MATHEMATICAL FOUNDATION
  Module 1:  Algebra, Functions, Exponents, Logarithms
  Module 2:  Limits
  Module 3:  The Derivative
  Module 4:  Integration
  Module 5:  Differential Equations

PART II — LINEAR ALGEBRA  ← backbone of QM
  Module 6:  Vectors and Vector Spaces
  Module 7:  Matrices, Eigenvalues, and Hermitian Operators

PART III — ANALYSIS TOOLS
  Module 8:  Complex Numbers and Euler's Formula
  Module 9:  ħ, Planck's Constant, and Quantization
  Module 10: Vector Calculus (∇, ∇², spherical coordinates)
  Module 11: Fourier Transforms

PART IV — QUANTUM MECHANICS FROM SCRATCH
  Module 12: The Postulates of Quantum Mechanics
  Module 13: Dirac Bra-Ket Notation
  Module 14: Particle in a Box (quantization from boundary conditions)
  Module 15: The Harmonic Oscillator (ladder operators, phonons, QFT)
  Module 16: Angular Momentum and Nuclear Shell Structure
  Module 17: Spin and Pauli Matrices
  Module 18: Commutators and the Uncertainty Principle

PART V — ADVANCED QUANTUM TOOLS
  Module 19: Perturbation Theory
  Module 20: Statistical Mechanics (Boltzmann, Fermi-Dirac, thermal neutrons)
  Module 21: Density Matrices and Open Quantum Systems
  Module 22: WKB Approximation — Derived From the Schrödinger Equation

PART VI — PHYSICS APPLICATIONS
  Module 23: The Breit-Wigner Formula (Xe-135 giant resonance)
  Module 24: The Gamow Tunneling Integral (Am-241 alpha decay)
  Module 25: Compton Scattering and Klein-Nishina (Cs-137 backscatter)
  Module 26: Fisher Information and the Cramér-Rao Bound (attribution limits)

PART VII — SYNTHESIS
  Module 27: Reading a Frontier Paper — Worked Example
  Module 28: Equation Toolkit — Complete Quick Reference
  Module 29: How to Build Your Own Equations
```

Do not skip sections. Each one gives vocabulary to the next.

---

## The Equations You Are Building Toward

These are the specific formulas from the Chernobyl physics problems. Everything in this lesson exists
to make these readable — not as black boxes, but as things you can derive, modify, and question.

```
RADIOACTIVE DECAY
  N(t) = N₀ · exp(-λt)

BATEMAN CHAIN  (Am-241 environmental peak, 2058)
  N_Am(t) = N_Pu(0) · [λ_Pu/(λ_Am - λ_Pu)] · [exp(-λ_Pu·t) - exp(-λ_Am·t)]

POINT KINETICS  (reactor runaway, April 26 1986 01:23:40)
  dP/dt = [(ρ - β)/Λ] · P + Σ λᵢ Cᵢ

GAMOW TUNNELING  (Am-241 alpha decay through Coulomb barrier)
  T = exp(-2G),   G = (√(2μ)/ħ) · ∫[r₁ to r₂] √[V(r) - Q] dr

BREIT-WIGNER RESONANCE  (Xe-135 absorption, the xenon pit)
  σ(E) = πλ̄² · g · (Γ_n Γ_γ) / [(E - E_r)² + (Γ/2)²]

KLEIN-NISHINA  (Compton scattering, Cs-137 184 keV backscatter peak)
  dσ/dΩ = (r_e²/2) · (ω'/ω)² · [(ω/ω') + (ω'/ω) - sin²θ]

CRAMÉR-RAO BOUND  (quantum limit on isotopic attribution)
  Var(θ̂) ≥ 1 / (N · F_Q(θ))
```

---

# Part I — Foundation

## Module 1: The Language of Algebra, Reviewed Precisely

High school algebra gave you variables, functions, and operations. Here we nail down exactly what
they mean before calculus, because precision matters in physics.

### 1.1 What a Function Is

A function `f` is a rule that takes an input and produces exactly one output.

```
f(x) = x²         — squaring function
g(t) = 3t + 7     — linear function of time
N(t) = N₀ · 2^(-t/t½)   — exponential decay
```

The input variable is a placeholder. `f(x)`, `f(t)`, `f(E)` are all the same shape of rule —
the letter just names the input.

**Physics convention:** Time is almost always `t`. Energy is `E`. Position is `x`, `r`, or `r⃗`.
Frequency is `ω` (omega) or `ν` (nu). This is not a law — it is vocabulary to learn.

### 1.2 Exponents and Logarithms — the Two Functions That Govern Nuclear Physics

Every equation in this project either has an exponential or is derived from one.

**The rules (these must be fluent):**

```
Multiplication:     aᵐ · aⁿ = aᵐ⁺ⁿ
Division:           aᵐ / aⁿ = aᵐ⁻ⁿ
Power of power:     (aᵐ)ⁿ = aᵐⁿ
Zero exponent:      a⁰ = 1   (for any a ≠ 0)
Negative exponent:  a⁻ⁿ = 1/aⁿ
Fractional exp:     a^(1/2) = √a
```

**The number e.**  The base `e ≈ 2.71828...` is not arbitrary. It is the unique base for which the
exponential function is its own derivative. (We will prove this in Module 3.) Every decay equation,
every growth equation, every resonance formula uses e.

**Logarithm as inverse:**  `ln(x)` is the inverse of `eˣ`. This means:

```
ln(eˣ) = x       for all x
e^(ln(x)) = x    for all x > 0
```

**The logarithm rules:**

```
ln(ab) = ln(a) + ln(b)
ln(a/b) = ln(a) - ln(b)
ln(aⁿ) = n · ln(a)
ln(e) = 1
ln(1) = 0
```

**Example — solving for half-life:**  Given `N(t) = N₀ · e^(-λt)`, find the time when N = N₀/2.

```
N₀/2 = N₀ · e^(-λt)
1/2 = e^(-λt)           (divide both sides by N₀)
ln(1/2) = -λt           (take ln of both sides — ln undoes e)
-ln(2) = -λt            (since ln(1/2) = -ln(2))
t = ln(2)/λ             (half-life formula)
```

This is where `t½ = ln(2)/λ ≈ 0.693/λ` comes from.

### 1.3 Proportionality — the Physical Intuition Behind Equations

When we write `dN/dt ∝ N` (proportional to N), we mean: double N, double the rate. Triple N,
triple the rate. This proportionality, combined with e, produces exponential behavior.

The general pattern in physics:

```
"Rate of change ∝ current value"  →  exponential solution
"Rate of change = constant"       →  linear solution
"Rate of change ∝ distance from equilibrium"  →  sinusoidal solution (oscillation)
```

Recognizing which type of proportionality governs a system tells you the solution before you solve.

---

## Module 2: Limits — The Foundation of Calculus

Calculus is built on one idea: asking what happens to a ratio as the denominator shrinks to zero.

### 2.1 What a Limit Is

The notation `lim[x→a] f(x) = L` means: as x gets closer and closer to a (without necessarily
equaling a), the value f(x) gets closer and closer to L.

**Example:**

```
lim[x→0] (sin x / x) = 1
```

At x=0 this is 0/0, which is undefined. But as x approaches 0 from either side, the ratio
approaches 1. This specific limit underlies every oscillation equation in wave physics.

**The limit that defines the derivative:**

```
lim[Δt→0] [N(t + Δt) - N(t)] / Δt
```

This is the ratio of the change in N to the change in t, as the time interval shrinks to zero.
It asks: what is the *instantaneous* rate of change? This is the derivative.

### 2.2 Why This Matters Physically

An ionization chamber reading in the CEZ gives you average dose rate over a measurement interval.
A derivative gives you the instantaneous rate. The RBMK power meters during the accident gave
readings averaged over instrument response time. The actual power excursion was faster than the
instruments could track — they were showing time-averaged values while the reactor crossed the
prompt-critical threshold. That gap between average and instantaneous is exactly what limits
tell you about.

---

## Module 3: The Derivative

### 3.1 Definition

The derivative of f(t) with respect to t is:

```
f'(t) = df/dt = lim[Δt→0] [f(t + Δt) - f(t)] / Δt
```

It is the slope of the tangent line to the curve f(t) at every point t.

**Notation:** All of these mean the same thing:

```
f'(t)     — Newton's prime notation
df/dt     — Leibniz fraction notation (most common in physics)
Df(t)     — operator notation
ḟ(t)      — dot notation (used in mechanics and thermodynamics)
```

In Leibniz notation, `df/dt` is read as "d-f d-t" — the infinitesimal change in f divided by the
infinitesimal change in t. It is not literally a fraction, but it behaves like one in most contexts.

### 3.2 The Power Rule

For any function `f(t) = tⁿ`:

```
d/dt [tⁿ] = n · tⁿ⁻¹
```

**Examples:**
```
d/dt [t²]    = 2t
d/dt [t³]    = 3t²
d/dt [t^(1/2)] = (1/2) t^(-1/2) = 1/(2√t)
d/dt [1/t]   = d/dt [t⁻¹] = -1 · t⁻² = -1/t²
d/dt [constant] = 0
```

### 3.3 The Exponential Rule — The Most Important Rule in This Project

For `f(t) = eᵃᵗ`:

```
d/dt [eᵃᵗ] = a · eᵃᵗ
```

**Proof from the limit definition:**

```
d/dt [eᵃᵗ] = lim[Δt→0] [eᵃ⁽ᵗ⁺ᐩᵗ⁾ - eᵃᵗ] / Δt
            = lim[Δt→0] eᵃᵗ · [eᵃᐩᵗ - 1] / Δt
```

The key fact: `lim[Δt→0] (eᵃᐩᵗ - 1)/Δt = a`. This is the defining property of e. At a=1:

```
lim[Δt→0] (eᐩᵗ - 1)/Δt = 1
```

No other base has this clean property. Base 2 would give `lim = ln(2) ≈ 0.693`. Base 10 would
give `lim = ln(10) ≈ 2.303`. Only base e gives exactly 1 — which is why every physicist uses e.

**Therefore:**

```
d/dt [e^(-λt)] = -λ · e^(-λt)
```

The derivative of a decay is the decay itself, scaled by -λ. This is why the differential equation
`dN/dt = -λN` has the solution `N(t) = N₀ e^(-λt)` — the equation and its solution are the same
function. The exponential is the fixed point of differentiation.

### 3.4 The Product Rule and Chain Rule

You will need these for every composite equation in the project.

**Product rule:** For `f(t) = u(t) · v(t)`:

```
d/dt [u · v] = u' · v + u · v'
```

In words: derivative of first times second, plus first times derivative of second.

**Chain rule:** For `f(t) = g(h(t))` (a function of a function):

```
d/dt [g(h(t))] = g'(h(t)) · h'(t)
```

In words: derivative of the outer function evaluated at the inner function, times derivative of
the inner function.

**Chain rule example — decay:**

```
N(t) = N₀ · e^(-λt)

Outer function: g(u) = N₀ · eᵘ,   g'(u) = N₀ · eᵘ
Inner function: h(t) = -λt,        h'(t) = -λ

dN/dt = N₀ · e^(-λt) · (-λ) = -λN(t)   ✓
```

**Chain rule example — compound nucleus:**

In the Breit-Wigner formula, the denominator is `[(E - E_r)² + (Γ/2)²]`. To differentiate σ(E)
with respect to E, the chain rule gives:

```
d/dE [(E - E_r)²] = 2(E - E_r) · d/dE [E - E_r] = 2(E - E_r)
```

This is how you find that the resonance peak sits exactly at E = E_r (where the derivative is zero
and σ is maximum).

### 3.5 Partial Derivatives — When Functions Have Multiple Inputs

Most physical quantities depend on several variables simultaneously. A partial derivative holds
all variables constant except the one you are differentiating with respect to.

Notation: `∂f/∂x` (curly d, "partial derivative of f with respect to x").

**Example — reactivity of the RBMK:**

```
ρ = ρ(T_fuel, α_void, rod_positions, ...)
```

The **void coefficient** is:

```
∂ρ/∂α_void = rate of change of reactivity with steam void fraction,
              holding all other variables constant.
```

For the RBMK at low power: `∂ρ/∂α_void > 0` — this is the positive void coefficient, the
fundamental design flaw that caused the accident.

The **Doppler coefficient** is:

```
∂ρ/∂T_fuel < 0    (negative — stabilizing)
```

As fuel temperature rises, U-238 absorption resonances broaden (Doppler broadening), absorbing
more neutrons and reducing reactivity. This negative feedback was too slow to prevent the accident
once prompt criticality was crossed.

The **total differential** (how reactivity changes for any perturbation):

```
dρ = (∂ρ/∂T_fuel)dT_fuel + (∂ρ/∂α_void)dα_void + (∂ρ/∂rods)drods + ...
```

This is the multivariate chain rule. When one positive term in this sum dominates over all the
negative ones, the reactor has a net positive feedback and will diverge.

---

## Module 4: Integration

Integration is the reverse of differentiation. But it also computes areas, totals, and cumulative
quantities — and this second interpretation is what makes it physically essential.

### 4.1 The Antiderivative

If `d/dx [F(x)] = f(x)`, then `F(x)` is an antiderivative of `f(x)`.

The **indefinite integral** notation:

```
∫ f(x) dx = F(x) + C
```

The `dx` tells you which variable you are integrating over. The `C` is a constant of integration
(because differentiating any constant gives zero, so the antiderivative is not unique).

**Basic integral table — these must be fluent:**

```
∫ xⁿ dx = xⁿ⁺¹/(n+1) + C     (n ≠ -1)
∫ 1/x dx = ln|x| + C
∫ eᵃˣ dx = eᵃˣ/a + C
∫ sin(x) dx = -cos(x) + C
∫ cos(x) dx = sin(x) + C
∫ 1/√x dx = 2√x + C
∫ √x dx = (2/3)x^(3/2) + C
∫ √(a - x) dx = -(2/3)(a - x)^(3/2) + C    ← needed for Gamow
```

### 4.2 The Definite Integral — Area and Cumulative Quantity

The **definite integral** from a to b:

```
∫[a to b] f(x) dx = F(b) - F(a)
```

This is the **Fundamental Theorem of Calculus**: differentiation and integration are inverse
operations, and definite integration equals the change in the antiderivative.

**Physical meaning:** The integral is a sum of infinitely many infinitesimally thin slices.
`f(x) dx` is the area of one rectangle of height f(x) and width dx. The integral adds them all up.

**Example — total activity released over time:**

If the daily I-131 release rate is `R(t)` (PBq/day), then the total I-131 released from April 26
to May 5 (t=0 to t=9 days) is:

```
Total = ∫[0 to 9] R(t) dt
```

If R(t) = R₀ · e^(-λt) (exponential decrease as fire died down):

```
Total = ∫[0 to 9] R₀ e^(-λt) dt = R₀ · [-e^(-λt)/λ] from 0 to 9
      = R₀/λ · [1 - e^(-9λ)]
```

For I-131 with t½ = 8.02 days → λ = 0.0864 day⁻¹:

```
Total = R₀/0.0864 · [1 - e^(-0.778)] = R₀ · 11.57 · [1 - 0.459] = 6.27 R₀
```

If R₀ = 1 PBq/day, approximately 6.3 PBq released over 9 days. This is the kind of calculation
behind the source term totals in `01_source_term.csv`.

### 4.3 Integration by Substitution

Substitution is the chain rule run backwards. When an integrand has a composite structure, you
substitute a new variable to simplify it.

**The method:**

1. Choose a substitution `u = g(x)` to simplify the integrand.
2. Compute `du = g'(x) dx`, then solve for `dx = du/g'(x)`.
3. Rewrite the entire integral in terms of u.
4. Integrate in u.
5. Substitute back to x.

**Example 1 — simple substitution:**

```
∫ e^(-λt) dt
```

Let `u = -λt`, so `du = -λ dt`, therefore `dt = -du/λ`:

```
∫ eᵘ · (-du/λ) = (-1/λ) ∫ eᵘ du = (-1/λ) eᵘ + C = -e^(-λt)/λ + C   ✓
```

**Example 2 — Bateman equation integrating factor:**

The ODE for Am-241:

```
dN_Am/dt + λ_Am · N_Am = λ_Pu · N_Pu(0) · e^(-λ_Pu · t)
```

Multiply both sides by `e^(λ_Am · t)` (this is the integrating factor):

```
e^(λ_Am·t) · dN_Am/dt + λ_Am · e^(λ_Am·t) · N_Am = λ_Pu · N_Pu(0) · e^((λ_Am - λ_Pu)t)
```

Recognize the left side as a product rule derivative: `d/dt [N_Am · e^(λ_Am·t)]`.

So the equation becomes:

```
d/dt [N_Am · e^(λ_Am·t)] = λ_Pu · N_Pu(0) · e^((λ_Am - λ_Pu)t)
```

Now integrate both sides:

```
N_Am · e^(λ_Am·t) = λ_Pu · N_Pu(0) · e^((λ_Am - λ_Pu)t) / (λ_Am - λ_Pu)  + C
```

Apply initial condition N_Am(0) = 0: C = -λ_Pu · N_Pu(0) / (λ_Am - λ_Pu).

Multiply through by `e^(-λ_Am·t)`:

```
N_Am(t) = N_Pu(0) · [λ_Pu / (λ_Am - λ_Pu)] · [e^(-λ_Pu·t) - e^(-λ_Am·t)]
```

This is the full Bateman solution — derived using only substitution, the integrating factor trick,
and initial conditions.

**Example 3 — Gamow substitution:**

The Gamow integral (simplified Coulomb barrier, pure 1/r potential):

```
G ∝ ∫[r₁ to r₂] √[kZ₁Z₂e²/r - Q] dr
```

Factor out Q:

```
G ∝ ∫[r₁ to r₂] √Q · √[r₂/r - 1] dr    where r₂ = kZ₁Z₂e²/Q
```

Substitute `x = r/r₂`, so `r = r₂x`, `dr = r₂ dx`, and the limits become r₁/r₂ to 1:

```
G ∝ √Q · r₂ · ∫[r₁/r₂ to 1] √[1/x - 1] dx
```

The remaining integral `∫[u to 1] √(1/x - 1) dx` has the analytic solution:

```
= arccos(√u) - √(u(1-u))    for 0 < u < 1
```

Since `u = r₁/r₂ ≈ 0.18` for Am-241 (r₁ ≈ 8.7 fm, r₂ ≈ 48.8 fm):

```
arccos(√0.18) - √(0.18 · 0.82) ≈ arccos(0.424) - 0.384 ≈ 1.133 - 0.384 = 0.749
```

Therefore `G ≈ 0.749 · √Q · r₂ / (ħ/√(2μ))`. Plugging in the numbers gives the
experimental Am-241 half-life of 432.2 years to within a factor of 2 using only a square
barrier nuclear potential.

### 4.4 Integration by Parts

For integrals of products where substitution doesn't apply directly:

```
∫ u · dv = u · v - ∫ v · du
```

This is the product rule for differentiation, rearranged.

**How to choose u and dv:** Use the LIATE priority — whatever comes first in this list is u:
Logarithms, Inverse trig, Algebraic (polynomials), Trig, Exponential.

**Example (relevant to Fourier transforms):**

```
∫ t · e^(-at) dt

Let u = t,     dv = e^(-at) dt
    du = dt,    v = -e^(-at)/a

= t · (-e^(-at)/a) - ∫ (-e^(-at)/a) dt
= -te^(-at)/a - e^(-at)/a²  + C
```

---

## Module 5: Differential Equations

A differential equation (DE) is any equation involving a function and its derivatives. The
solution is the function itself — not a number, but a function of time or space.

### 5.1 First-Order Linear ODEs

The general form:

```
dy/dt + P(t) · y = Q(t)
```

The solution method: multiply by the integrating factor `μ(t) = e^(∫P(t)dt)`, which converts
the left side into the derivative of a product `d/dt [μ · y]`, then integrate.

**The decay ODE:**

```
dN/dt + λN = 0          (P = λ, Q = 0)
μ = e^(∫λ dt) = e^(λt)
d/dt [N · e^(λt)] = 0
N · e^(λt) = C
N(t) = C · e^(-λt) = N₀ · e^(-λt)  (using N(0) = N₀)
```

**The Bateman ODE:**

```
dN_Am/dt + λ_Am · N_Am = λ_Pu · N_Pu(0) · e^(-λ_Pu · t)
```

This is the same form with Q ≠ 0. The method is identical — integrating factor, then integrate —
as worked through in Module 4.3 above.

### 5.2 Coupled Systems of ODEs — Point Kinetics

The reactor is described by **seven coupled ODEs** (1 for power, 6 for delayed precursor groups):

```
dP/dt = [(ρ - β)/Λ] · P  +  Σᵢ λᵢ Cᵢ  +  S
dCᵢ/dt = (βᵢ/Λ) · P  -  λᵢ Cᵢ         (i = 1, 2, ..., 6)
```

**Variables:**

| Symbol | Meaning | RBMK value |
|--------|---------|------------|
| P(t)   | Reactor power (MW thermal) | ~200 before excursion |
| Cᵢ(t)  | Concentration of delayed neutron precursor group i | varies |
| ρ      | Reactivity (dimensionless) | ~0 at normal operation |
| β      | Effective delayed neutron fraction | 0.0065 for RBMK |
| βᵢ     | Delayed fraction for group i | 6 values summing to β |
| λᵢ     | Decay constant of precursor group i (s⁻¹) | 0.0124 to 3.01 s⁻¹ |
| Λ      | Prompt neutron generation time | 0.001 s (RBMK) |
| S      | External neutron source | ~0 at power |

**The physical meaning of the two terms in dP/dt:**

- `[(ρ - β)/Λ] · P` = contribution from prompt neutrons. If ρ < β, this term is negative —
  prompt neutrons alone cannot sustain the chain reaction; delayed neutrons are needed.
- `Σ λᵢ Cᵢ` = contribution from delayed neutrons — the precursors decaying and releasing
  their delayed neutrons. These set the timescale for controllability.

**The bifurcation at ρ = β (prompt critical threshold):**

When ρ < β: the `(ρ-β)/Λ` term is negative. The precursors stabilize P on a timescale of
seconds to minutes. Operators can respond with control rods.

When ρ > β: the `(ρ-β)/Λ` term is positive. P grows exponentially on the prompt neutron timescale
Λ = 0.001 s, regardless of the precursors. Control rods take ~1 second to insert — far too slow.

**The accident calculation:**

At 01:23:40, ρ exceeded β by approximately a factor of 10 (ρ ≈ 0.065, β = 0.0065). The dominant
term in dP/dt is then:

```
dP/dt ≈ [(0.065 - 0.0065)/0.001] · P = 58.5 · P
```

This is `dP/dt = kP` with k = 58.5 s⁻¹. Solution: `P(t) = P₀ · e^(58.5t)`.

Power doubling time:

```
t_double = ln(2) / 58.5 ≈ 0.012 s = 12 milliseconds
```

From 200 MWth to 30,000 MWth in about 3 seconds: approximately `ln(150)/58.5 ≈ 0.086 s` of
pure exponential growth before physical feedback (steam void collapse, Doppler broadening,
mechanical fuel disruption) ended the excursion. In practice the rise was nonlinear because
void fraction changed simultaneously, but the exponential is the core mechanism.

### 5.3 Finding Extrema — Where to Set the Derivative to Zero

The maximum or minimum of a function occurs where the derivative is zero.

**The Am-241 peak year:**

```
N_Am(t) = N_Pu(0) · [λ_Pu/(λ_Am - λ_Pu)] · [e^(-λ_Pu·t) - e^(-λ_Am·t)]
```

Differentiate and set to zero:

```
dN_Am/dt = N_Pu(0) · [λ_Pu/(λ_Am - λ_Pu)] · [-λ_Pu·e^(-λ_Pu·t) + λ_Am·e^(-λ_Am·t)] = 0
```

The bracket must be zero:

```
λ_Am · e^(-λ_Am·t) = λ_Pu · e^(-λ_Pu·t)
```

Divide both sides by `e^(-λ_Am·t)`:

```
λ_Am = λ_Pu · e^((λ_Am - λ_Pu)·t)
λ_Am / λ_Pu = e^((λ_Am - λ_Pu)·t)
ln(λ_Am / λ_Pu) = (λ_Am - λ_Pu) · t_max
```

Therefore:

```
t_max = ln(λ_Am / λ_Pu) / (λ_Am - λ_Pu)
```

Substituting: λ_Pu = 0.04851 yr⁻¹, λ_Am = 0.001604 yr⁻¹:

```
t_max = ln(0.001604 / 0.04851) / (0.001604 - 0.04851)
      = ln(0.03306) / (-0.04691)
      = (-3.409) / (-0.04691)
      ≈ 72.7 years after 1986  →  2058.7
```

The Am-241 environmental inventory in the exclusion zone peaks in 2058. This number is not
an estimate — it follows directly from two measured half-lives and a derivative set to zero.

---

# Part II — Linear Algebra

Quantum mechanics is not an extension of classical physics — it is a different mathematical
structure. That structure is linear algebra. Understanding quantum mechanics without linear
algebra is like understanding calculus without algebra: you can follow specific examples but
cannot derive anything new. These two modules build the backbone before we touch quantum mechanics.

## Module 6: Vectors and Vector Spaces

### 6.1 Why This Matters First

Every quantum state is a vector. The Schrödinger equation is an eigenvalue problem. Spin states
live in a 2-dimensional complex vector space. The nuclear shell model is a matrix diagonalization.
Density matrices are matrices. These are not metaphors — they are literal descriptions of the
mathematical objects involved. Linear algebra is not background material for quantum mechanics.
It is quantum mechanics, in the right language.

### 6.2 Geometric Vectors

A vector in 2D or 3D is an arrow: a magnitude and a direction. You can add them (tip-to-tail)
and scale them (stretch/shrink).

In component form **v** = (v₁, v₂, v₃):

```
Addition:          (a₁,a₂,a₃) + (b₁,b₂,b₃) = (a₁+b₁, a₂+b₂, a₃+b₃)
Scalar multiply:   c·(v₁,v₂,v₃) = (cv₁, cv₂, cv₃)
Dot product:       a·b = a₁b₁ + a₂b₂ + a₃b₃ = |a||b|cosθ
Norm (length):     |v| = √(v·v) = √(v₁² + v₂² + v₃²)
Orthogonality:     a·b = 0  (the angle between them is 90°)
Unit vector:       û = v/|v|  (length 1, same direction)
```

### 6.3 Abstract Vector Spaces

Linear algebra generalizes far beyond arrows in 3D. An abstract **vector space** V over
the complex numbers ℂ is any set of objects (called "vectors") with addition and scalar
multiplication satisfying:

```
1. u + v ∈ V                       (closure under addition)
2. c·v ∈ V  for c ∈ ℂ             (closure under scalar multiplication)
3. u + v = v + u                   (commutativity)
4. (u+v)+w = u+(v+w)               (associativity)
5. ∃ zero vector 0: v + 0 = v      (zero element)
6. c(u+v) = cu + cv                (distributivity)
7. 1·v = v                         (unit scalar)
```

**Why this abstraction is useful:** the rules work identically for tuples of numbers, for
functions, for matrices, and for quantum states — once you prove something holds for an
abstract vector space, it holds in all of them at once.

**Examples of vector spaces:**

- ℝⁿ: tuples of n real numbers. Ordinary n-dimensional space.
- ℂⁿ: tuples of n complex numbers. Home of spin states.
- L²(ℝ): square-integrable functions (∫|f|²dx < ∞). Home of quantum wavefunctions. Two
  wavefunctions can be added: (ψ₁+ψ₂)(x) = ψ₁(x)+ψ₂(x). A wavefunction scaled by a
  complex number is still a valid wavefunction.

### 6.4 Basis, Coordinates, and Dimension

A set of vectors {e₁, e₂, ..., eₙ} is a **basis** for V if every vector in V can be
written *uniquely* as v = c₁e₁ + c₂e₂ + ... + cₙeₙ (a linear combination).

**Linear independence:** {e₁,...,eₙ} are linearly independent if c₁e₁+...+cₙeₙ = 0
requires every cᵢ = 0. No vector in the set can be written as a combination of the others.

**Dimension:** the number of basis vectors needed to span V.

- Spin-1/2: dimension 2 (two basis states |↑⟩ and |↓⟩)
- Two spin-1/2 particles: dimension 4 (four basis states |↑↑⟩, |↑↓⟩, |↓↑⟩, |↓↓⟩)
- Particle in a 1D box: dimension ∞ (infinitely many energy eigenstates)

An **orthonormal basis** (ONB): basis vectors that are mutually orthogonal and all have
length 1. Standard example: the unit vectors e₁=(1,0,0), e₂=(0,1,0), e₃=(0,0,1) in ℝ³.
Working in an ONB simplifies every calculation.

### 6.5 Complex Inner Products

In a complex vector space the inner product must conjugate one argument:

```
⟨u, v⟩ = Σᵢ uᵢ* vᵢ     (for column vectors in ℂⁿ)
          ∫ φ*(x)ψ(x)dx  (for functions in L²(ℝ))
```

Requirements:
1. ⟨u, v⟩ = ⟨v, u⟩*              (conjugate symmetry)
2. ⟨u, αv+βw⟩ = α⟨u,v⟩+β⟨u,w⟩   (linear in second slot)
3. ⟨v, v⟩ ≥ 0, = 0 iff v = 0     (positive definite)

The **norm**: ‖v‖ = √⟨v,v⟩.

**Orthonormality condition**: ⟨eᵢ, eⱼ⟩ = δᵢⱼ (= 1 if i=j, = 0 otherwise).

**Expanding in an ONB**: if {e₁,...,eₙ} is an ONB, then any vector v = Σᵢ cᵢeᵢ where the
coordinates are given by projections: cᵢ = ⟨eᵢ, v⟩.

### 6.6 Hilbert Space — The Home of Quantum States

A **Hilbert space** ℋ is a complex vector space with an inner product that is *complete*:
every limit of a sequence of vectors that should converge (a Cauchy sequence) actually converges
to something in ℋ. This technical condition ensures calculus works freely inside the space.

In practice: ℂⁿ with standard inner product is always Hilbert space. L²(ℝ) is Hilbert space
(this is why wavefunctions must be normalizable — non-normalizable functions fall outside the
space and are not valid states).

**The quantum postulate:** Every quantum state is a normalized vector |ψ⟩ ∈ ℋ with ⟨ψ|ψ⟩ = 1.
Physical superposition is vector addition. Relative phase between components (the imaginary
parts) governs interference. The inner product ⟨φ|ψ⟩ gives the probability amplitude for
finding |ψ⟩ in state |φ⟩.

---

## Module 7: Matrices, Eigenvalues, and Hermitian Operators

### 7.1 Matrices as Linear Maps

A matrix A is a rectangular array of numbers encoding a **linear map** — a function from
vectors to vectors that preserves addition and scalar multiplication.

An m×n matrix maps n-vectors to m-vectors: Av = w.

```
Matrix-vector multiplication:  (Av)ᵢ = Σⱼ Aᵢⱼ vⱼ

Example:
  A = [[2, 1],    v = [3]     Av = [2·3 + 1·4]   [10]
       [0, 3]]        [4]          [0·3 + 3·4] =  [12]
```

### 7.2 Matrix Multiplication

For A (m×n) and B (n×p), the product C = AB is m×p:

```
Cᵢⱼ = Σₖ Aᵢₖ Bₖⱼ
```

Think of it as: the (i,j) entry of AB is the dot product of row i of A with column j of B.

**Critical: AB ≠ BA in general.** Matrix multiplication does not commute. This is not
a technicality — it is the algebraic source of the Heisenberg uncertainty principle. When
quantum operators don't commute, the corresponding observables cannot be simultaneously
measured. The non-commutativity of matrices is the mathematical home of this physics.

**Concrete example:**

```
σx = [[0,1],[1,0]]    σz = [[1,0],[0,-1]]

σxσz = [[0·1+1·0, 0·0+1·(-1)],   =  [[0,-1],
         [1·1+0·0, 1·0+0·(-1)]]       [1, 0]]

σzσx = [[1·0+0·1, 1·1+0·0],      =  [[0, 1],
         [0·0+(-1)·1, 0·1+(-1)·0]]    [-1,0]]

σxσz ≠ σzσx     ← these are the Pauli matrices for spin
```

### 7.3 Special Matrix Types

```
Identity matrix I:         Iᵢⱼ = δᵢⱼ,  Iv = v
Transpose Aᵀ:              (Aᵀ)ᵢⱼ = Aⱼᵢ  (flip rows and columns)
Conjugate transpose A†:    (A†)ᵢⱼ = Aⱼᵢ*  (transpose + conjugate every entry)
                           Also called: dagger, Hermitian adjoint
Hermitian matrix:          A† = A     diagonal entries real, off-diagonal in conjugate pairs
Unitary matrix:            U†U = UU† = I   (U† = U⁻¹)
Trace:                     Tr(A) = Σᵢ Aᵢᵢ  (sum of diagonal entries)
```

**Trace properties** (you will use these constantly with density matrices):

```
Tr(AB) = Tr(BA)                  (cyclic property)
Tr(A+B) = Tr(A) + Tr(B)          (linearity)
Tr(A) = sum of eigenvalues of A
Tr(|ψ⟩⟨φ|) = ⟨φ|ψ⟩              (crucial for expectation values)
```

### 7.4 The Eigenvalue Equation

For a square matrix A, the **eigenvalue equation** is:

```
Av = λv
```

The nonzero vector v is an **eigenvector**; the scalar λ is the **eigenvalue**. What makes
eigenvectors special: A doesn't rotate them, only scales them by λ.

**Finding eigenvalues:** Rearrange Av = λv as (A - λI)v = 0. A nonzero solution exists
only when A - λI is singular (non-invertible):

```
det(A - λI) = 0     ← the characteristic equation
```

For an n×n matrix this gives a degree-n polynomial in λ. Its n roots (counted with
multiplicity, possibly complex) are the eigenvalues.

**Full worked example:** Find eigenvalues and eigenvectors of A = [[3, 1], [1, 3]].

```
det(A - λI) = det([[3-λ, 1],[1, 3-λ]])
            = (3-λ)² - 1
            = λ² - 6λ + 8
            = (λ-4)(λ-2) = 0

Eigenvalues: λ₁ = 4,  λ₂ = 2.

For λ₁ = 4:  (A - 4I)v = 0
  [[-1,1],[1,-1]]v = 0  →  v₁ = v₂  →  eigenvector = [1,1]/√2

For λ₂ = 2:  (A - 2I)v = 0
  [[1,1],[1,1]]v = 0   →  v₁ = -v₂  →  eigenvector = [1,-1]/√2

Check: A[1,1]/√2 = [4,4]/√2 = 4·[1,1]/√2  ✓
       A[1,-1]/√2 = [2,-2]/√2 = 2·[1,-1]/√2  ✓
```

### 7.5 The Spectral Theorem — Why Hermitian Operators Are Everything

**Spectral Theorem:** A Hermitian matrix A (A† = A) has:
1. All eigenvalues are **real**.
2. Eigenvectors for distinct eigenvalues are **orthogonal**.
3. There exists a complete **orthonormal basis** of eigenvectors.

**Proof that Hermitian eigenvalues are real (complete):**

```
Let Av = λv with A† = A. Take the inner product ⟨v, ·⟩ of both sides:
  ⟨v, Av⟩ = λ⟨v, v⟩                    ... (i)
Also: ⟨v, Av⟩ = ⟨A†v, v⟩ = ⟨Av, v⟩*
             = (λ⟨v,v⟩)* = λ*⟨v,v⟩     ... (ii)
From (i) and (ii): λ = λ* → λ is real.  □
```

**Why this is foundational for physics:** Every physical observable — energy, momentum,
position, spin, angular momentum — is represented by a Hermitian operator. The spectral
theorem guarantees:
- Measurement outcomes (eigenvalues) are always real numbers.
- The states with definite values (eigenstates) are mutually orthogonal — distinct outcomes
  are genuinely different, non-overlapping possibilities.
- The eigenstates form a complete basis — any quantum state can be decomposed into a sum
  of eigenstates of any observable.

**Spectral decomposition:** A Hermitian operator A can always be written as:

```
A = Σᵢ λᵢ |vᵢ⟩⟨vᵢ|
```

a sum of projection operators weighted by eigenvalues. This is the most useful form in QM.

### 7.6 Unitary Operators and Quantum Time Evolution

A unitary operator U satisfies U†U = I. It preserves inner products and norms:
⟨Uu, Uv⟩ = ⟨u,v⟩. Unitary operations are quantum mechanical "rotations" in Hilbert space.

**Time evolution:** For a time-independent Hamiltonian Ĥ, the Schrödinger equation has solution:

```
|ψ(t)⟩ = e^(-iĤt/ħ) |ψ(0)⟩
```

The operator Û(t) = e^(-iĤt/ħ) is unitary (since Ĥ is Hermitian → iĤ is anti-Hermitian →
e^(anti-Hermitian) is unitary). This means: total probability is always conserved.

**In the energy eigenbasis** (Ĥ|n⟩ = Eₙ|n⟩):

```
Û(t)|n⟩ = e^(-iEₙt/ħ)|n⟩     (eigenstates just acquire phase factors)

|ψ(t)⟩ = Σₙ cₙ e^(-iEₙt/ħ)|n⟩    where cₙ = ⟨n|ψ(0)⟩
```

Each energy eigenstate evolves independently, accumulating phase at rate Eₙ/ħ. Interference
between states at different frequencies Eₙ/ħ produces the time-dependence of observables.

### 7.7 The Pauli Matrices — Preview

The three Pauli matrices are the central 2×2 matrices of quantum mechanics:

```
σx = [[0, 1],     σy = [[0, -i],    σz = [[1,  0],
      [1, 0]]           [i,  0]]          [0, -1]]
```

All three are Hermitian (σᵢ† = σᵢ) and unitary (σᵢ†σᵢ = I). Eigenvalues: ±1 for all three.

Key algebraic identity: σᵢσⱼ = δᵢⱼI + iεᵢⱼₖσₖ where εᵢⱼₖ is the Levi-Civita symbol
(antisymmetric: ε₁₂₃=1, ε₂₁₃=-1, etc.). This implies [σᵢ, σⱼ] = 2iεᵢⱼₖσₖ.

Spin operators: Ŝᵢ = (ħ/2)σᵢ. Full treatment in Module 17.

---

# Part III — Analysis Tools

## Module 8: Complex Numbers and Euler's Formula

Physics at the quantum scale is fundamentally complex — not in the colloquial sense, but in the
mathematical sense: the numbers are literally complex. Before Fourier transforms or quantum
mechanics make sense, you need to own this number system completely.

### 6.1 The Problem with Real Numbers

Solve `x² = 4`. Answer: x = ±2. Fine.

Solve `x² = -1`. There is no real number that squares to a negative. Rather than declare this
unsolvable, mathematicians defined a new number to fill the gap.

The **imaginary unit**:

```
i = √(-1)    →    i² = -1
```

This is not a trick or a placeholder. It is a genuine extension of the number line into a plane.

### 6.2 The Complex Plane

A **complex number** z has a real part and an imaginary part:

```
z = a + bi    where a, b are real numbers
```

Plot this as a point in the **complex plane** (Argand plane):
- Horizontal axis: real part, Re(z) = a
- Vertical axis: imaginary part, Im(z) = b

The distance from the origin is the **modulus**:

```
|z| = √(a² + b²)
```

The angle from the positive real axis is the **argument**:

```
arg(z) = arctan(b/a)
```

In **polar form**, any complex number can be written as:

```
z = r · (cosθ + i·sinθ)    where r = |z|, θ = arg(z)
```

This is just a point at distance r from the origin, at angle θ — Pythagorean theorem.

### 6.3 The Taylor Series — How Functions Become Infinite Sums

Before Euler's formula, one more tool: the **Taylor series**.

Any smooth function f(x) can be written as an infinite polynomial around x = 0:

```
f(x) = f(0) + f'(0)·x + f''(0)·x²/2! + f'''(0)·x³/3! + ...
     = Σ[n=0 to ∞] f⁽ⁿ⁾(0) · xⁿ / n!
```

where `n! = n·(n-1)·...·2·1` (n factorial) and `f⁽ⁿ⁾` means the nth derivative.

The key three series (memorize their shapes):

```
eˣ  = 1 + x + x²/2! + x³/3! + x⁴/4! + x⁵/5! + ...

sin(x) = x - x³/3! + x⁵/5! - x⁷/7! + ...    (odd powers, alternating signs)

cos(x) = 1 - x²/2! + x⁴/4! - x⁶/6! + ...    (even powers, alternating signs)
```

Notice: sin(x) has all the odd terms of eˣ (with alternating signs), and cos(x) has all the
even terms. They are not coincidentally related to eˣ — they are literally parts of it.

### 6.4 Euler's Formula — The Most Beautiful Equation in Mathematics

Substitute `x = iθ` (an imaginary number) into the Taylor series for eˣ:

```
e^(iθ) = 1 + (iθ) + (iθ)²/2! + (iθ)³/3! + (iθ)⁴/4! + (iθ)⁵/5! + ...
```

Evaluate the powers of i:

```
i¹ = i
i² = -1
i³ = i²·i = -i
i⁴ = i²·i² = (-1)(-1) = +1
i⁵ = i⁴·i = i     (cycle repeats with period 4)
```

Substitute:

```
e^(iθ) = 1 + iθ - θ²/2! - iθ³/3! + θ⁴/4! + iθ⁵/5! - ...
```

Separate real and imaginary terms:

```
Real:      1 - θ²/2! + θ⁴/4! - ...  =  cos(θ)
Imaginary: θ - θ³/3! + θ⁵/5! - ...  =  sin(θ)
```

Therefore:

```
┌─────────────────────────────────────┐
│   e^(iθ) = cos(θ) + i·sin(θ)       │
└─────────────────────────────────────┘
```

This is **Euler's formula**. It was not guessed or observed — it falls out of the Taylor series
with nothing but algebra. The exponential function, when given an imaginary exponent, traces a
circle in the complex plane of radius 1.

**Euler's identity** (set θ = π):

```
e^(iπ) = cos(π) + i·sin(π) = -1 + i·0 = -1

∴  e^(iπ) + 1 = 0
```

Five fundamental constants — e, i, π, 1, 0 — in one equation. Every physicist has a moment with
this. It is not a coincidence or a curiosity. It is the statement that exponential growth, rotation,
and the geometry of the circle are the same mathematical object seen from different angles.

### 6.5 What Euler's Formula Does for Physics

**Oscillations become exponentials.** Instead of writing:

```
A·cos(ωt) + B·sin(ωt)
```

physicists write:

```
Re[C · e^(iωt)]    where C = A - iB is a complex amplitude
```

The exponential is easier to differentiate (d/dt [e^(iωt)] = iω·e^(iωt)), easier to multiply,
and easier to integrate. The real physical observable is the real part — but you do all the work
in the complex plane and take the real part at the end.

**Rotation in the complex plane.** Multiplying a complex number z by e^(iθ) rotates it by angle
θ in the complex plane without changing its magnitude. This is the mathematical language of quantum
spin states, polarization, and phase.

**Waves.** A traveling wave moving in the +x direction at speed v:

```
ψ(x,t) = A · e^(i(kx - ωt))
```

where k = 2π/λ is the wave number and ω = 2πf is angular frequency. The real part is
A·cos(kx - ωt) — a cosine wave. The complex form carries both the amplitude and the phase in a
single compact expression.

**The quantum wavefunction.** The state of a quantum particle is literally a complex-valued
function ψ(x,t). The probability of finding the particle at position x is |ψ(x,t)|² — the square
of the modulus. The imaginary part is not fiction — it carries the phase information that determines
interference, diffraction, and tunneling.

### 6.6 Complex Conjugate and Modulus Squared

The **complex conjugate** of z = a + bi is:

```
z* = a - bi
```

(flip the sign of the imaginary part).

Key identity: `z · z* = (a+bi)(a-bi) = a² + b² = |z|²` — always real and non-negative.

In quantum mechanics, probabilities are always real and non-negative, which is why probability
densities are always written as |ψ|² = ψ* · ψ rather than just ψ².

**For Fourier transforms:** The power spectral density is `|F(ω)|²` — the modulus squared of the
Fourier transform — which is always real and represents the actual power at each frequency.

---

## Module 9: ħ, Planck's Constant, and Quantization

This module answers: what is ħ, where does it come from, and why does it appear in every quantum
equation?

### 6b.1 The Problem Planck Solved (1900)

A hot object glows. Classical physics predicted that a perfect absorber/emitter (a "blackbody")
would emit infinite power at high frequencies — the **ultraviolet catastrophe**. This was not a
small discrepancy; it was the theory predicting infinity where experiments found a peak and a falloff.

Max Planck fixed it in 1900 by proposing that electromagnetic energy is not continuous but comes
in discrete chunks — **quanta**. The energy of each quantum is proportional to frequency:

```
E = h · f = h · ν     where h is Planck's constant
```

The value Planck fitted to the blackbody spectrum:

```
h = 6.626 × 10⁻³⁴ J·s   (joule-seconds)
```

This is a very small number. It sets the scale at which quantum effects become important. Objects
with energies much larger than hf behave classically; objects at the scale of hf behave quantum
mechanically.

### 6b.2 Why ħ = h/2π Instead of h

Oscillations and waves are naturally described by angular frequency ω = 2πf rather than ordinary
frequency f. The factor of 2π appears constantly and clutters equations. Define:

```
ħ = h / (2π) = 1.055 × 10⁻³⁴ J·s
```

Read as "h-bar." Now write the quantum energy as:

```
E = hf = h·(ω/2π) = ħ·ω
```

The factor of 2π is absorbed into ħ. This is purely notational convenience — but in physics,
notational choices that reduce clutter are adopted universally.

**ħ in context:**

```
ħ = 6.582 × 10⁻¹⁶ eV·s     (in electron-volt units — useful for atomic/nuclear physics)
ħc = 197.3 MeV·fm            (in nuclear units — memorize this one)
```

The last identity is extremely useful: it lets you convert between length and energy in nuclear
physics without tracking unit conversions separately.

### 6b.3 The de Broglie Relation — Everything Has a Wavelength

Einstein showed (1905) that photons have momentum `p = E/c = hf/c = h/λ`. Louis de Broglie
proposed (1924) that this works in reverse for matter too:

```
λ_dB = h / p
```

Every particle with momentum p has an associated quantum wavelength. For a thermal neutron at
room temperature (kinetic energy E = kT ≈ 0.025 eV):

```
p = √(2mₙE) = √(2 × 1.675×10⁻²⁷ × 0.025 × 1.6×10⁻¹⁹) = 3.64×10⁻²⁴ kg·m/s

λ_dB = h/p = 6.626×10⁻³⁴ / 3.64×10⁻²⁴ = 1.82×10⁻¹⁰ m = 1.82 Å
```

A thermal neutron has a wavelength of ~2 Å — comparable to the spacing between atoms in a crystal
lattice. This is why slow neutrons can diffract off crystal structures (neutron diffraction) and
why the nuclear cross-section for slow neutrons is not the geometric size of the nucleus (~1 fm)
but the de Broglie wave size (~Å) — four orders of magnitude larger.

In the Breit-Wigner formula, `πλ̄²` is the geometric cross-section of the neutron's quantum wave,
not its physical size. At thermal energies, `πλ̄² ~ 10⁵ barns`, which is why the Xe-135
cross-section can reach 2.65 × 10⁶ barns — physically impossible for a nucleus of radius 6 fm
(whose geometric cross-section is ~1 barn), but sensible for a quantum wave of radius 2 Å.

### 6b.4 The Heisenberg Uncertainty Principle

One of the most misunderstood results in science. It is not about measurement disturbance — it
is a mathematical theorem about waves. Any wave that is localized in space must contain a spread
of wavelengths (frequencies), and vice versa.

The mathematical statement (derived from Fourier analysis):

```
Δx · Δp ≥ ħ/2
ΔE · Δt ≥ ħ/2
```

where Δx and Δp are the standard deviations of position and momentum measured simultaneously
on identically prepared quantum states. This is not a statement about imprecise instruments — it
is a statement that position and momentum simply do not both have definite values simultaneously.

**Why Δx · Δp ≥ ħ/2 follows from Fourier analysis:**

The position wavefunction ψ(x) and momentum wavefunction φ(p) are Fourier transform pairs:

```
φ(p) = (1/√(2πħ)) ∫ ψ(x) · e^(-ipx/ħ) dx
```

A Gaussian ψ(x) with width σ_x transforms to a Gaussian φ(p) with width σ_p = ħ/(2σ_x).
Therefore σ_x · σ_p = ħ/2. Any other shape gives a larger product. The Gaussian wavepacket
saturates the uncertainty bound — it is the most simultaneously localized state possible.

**Physical consequence for tunneling:** If an alpha particle is confined inside a nucleus of
radius R ~ 8.7 fm (for Am-241), then Δx ~ R sets a minimum momentum uncertainty:

```
Δp ≥ ħ/(2R) = 197.3 MeV·fm / (2 × 8.7 fm) ≈ 11 MeV/c
```

This momentum uncertainty means the alpha particle is not at rest inside the nucleus — it has
kinetic energy `(Δp)²/(2µ) ≈ 0.3 MeV` just from being confined. This zero-point motion is
what continuously drives the alpha against the Coulomb barrier, making tunneling attempts at a
rate ν ~ 10²¹ per second. Without this quantum confinement energy, there would be no tunneling,
no alpha decay, no radioactivity of this type.

**The energy-time uncertainty and the Breit-Wigner width:**

A nuclear state with finite lifetime τ has an energy uncertainty:

```
ΔE · τ ≥ ħ/2    →    ΔE ~ ħ/τ = Γ (the natural linewidth)
```

The width Γ of the Breit-Wigner formula is literally the energy-time uncertainty of the compound
nuclear state. The Ba-136* compound nucleus formed when Xe-135 absorbs a neutron has lifetime
τ = ħ/Γ ~ 7 femtoseconds. That short lifetime corresponds to the ~90 meV energy width of the
resonance. You cannot measure the resonance energy more precisely than Γ — that is not an
instrumental limitation, it is the uncertainty principle applied to the compound nucleus.

### 6b.5 The Schrödinger Equation — Where ħ Lives

The fundamental equation of quantum mechanics is the **time-dependent Schrödinger equation**:

```
iħ · ∂ψ/∂t = Ĥ ψ
```

where:
- `ψ(x,t)` = the quantum wavefunction (complex-valued)
- `Ĥ` = the Hamiltonian operator = kinetic energy + potential energy
- `iħ ∂/∂t` = the energy operator acting on time

For a single particle in a potential V(x):

```
iħ · ∂ψ/∂t = [-ħ²/(2m) · ∂²/∂x² + V(x)] · ψ
```

The term `−ħ²/(2m) · ∂²/∂x²` is the kinetic energy operator. The momentum operator is
`p̂ = -iħ · ∂/∂x`, and kinetic energy is p̂²/(2m) = -ħ²/(2m) · ∂²/∂x². Squaring the
derivative means applying it twice — the second spatial derivative measures curvature, and
curvature in the wavefunction corresponds to kinetic energy.

**Stationary states:** If V does not depend on t, try `ψ(x,t) = φ(x)·e^(-iEt/ħ)`.
Substituting:

```
iħ · (-iE/ħ) · φ · e^(-iEt/ħ) = Ĥφ · e^(-iEt/ħ)
E · φ = Ĥφ
```

The time-dependent phase `e^(-iEt/ħ)` cancels and you get the **time-independent Schrödinger
equation**: `Ĥφ = Eφ`. This is an eigenvalue equation — the allowed energies E are the
eigenvalues and the wavefunctions φ are the eigenstates. In a box, in a well, in a nuclear
potential — the allowed states are the solutions to this equation.

**The phase `e^(-iEt/ħ)` matters.** The energy E sets the rate of phase rotation in the complex
plane. A stationary state with energy E rotates at angular frequency ω = E/ħ. Two states with
energies E₁ and E₂ accumulate phase at different rates — their phase difference oscillates at
frequency (E₁ - E₂)/ħ. This oscillation in phase is the quantum mechanical source of all
interference, all beating, and (in the nuclear context) all coherent oscillations between
quantum states.

### 6b.6 ħ as the Fundamental Quantum of Action

`h` has units of J·s = kg·m²/s — units of action (energy × time, or momentum × distance).
The quantum of action is ħ. Physical processes with action S >> ħ behave classically. Processes
with S ~ ħ are quantum mechanical.

For comparison:
- A baseball thrown at 30 m/s: action ~ 1 J·s ~ 10³⁴ ħ. Completely classical.
- An electron in a hydrogen atom: action ~ ħ. Completely quantum.
- A thermal neutron in a reactor: de Broglie wavelength ~ Å, action ~ ħ. Quantum.
- A fission fragment with 90 MeV kinetic energy: action ~ 10⁴ ħ. Mostly classical trajectory,
  but quantum in its nuclear structure.

The Chernobyl project spans the full range: from individual neutron quantum states (S ~ ħ) to
continental atmospheric transport (S >> ħ). The boundary between these regimes is at the scale
where quantum corrections become measurable — which is precisely what Problems 1–13 in
`PROPOSED_DIRECTIONS.md` are probing.

---

## Module 10: Vector Calculus

Most of the physics in this project happens in three spatial dimensions. Derivatives and
integrals of functions of position require vector calculus — the multivariable extension
of the single-variable tools from Part I.

### 10.1 The Gradient

For a scalar function f(x,y,z), the **gradient** is the vector of partial derivatives:

```
∇f = (∂f/∂x, ∂f/∂y, ∂f/∂z)
```

The gradient points in the direction of steepest increase of f, with magnitude equal to
the rate of increase per unit distance.

**Physical meaning:** The force on a particle in a potential energy field V(r) is:

```
F = -∇V
```

Force points downhill in the energy landscape. This holds for gravity, electromagnetism,
the nuclear potential — any conservative force.

### 10.2 The Divergence

For a vector field F = (Fx, Fy, Fz), the **divergence** is:

```
∇·F = ∂Fx/∂x + ∂Fy/∂y + ∂Fz/∂z
```

Divergence measures the net outflow from an infinitesimal volume element. Positive divergence:
more flowing out than in (a source). Negative: more in than out (a sink).

**The continuity equation** (conservation of any quantity with density ρ and current J):

```
∂ρ/∂t + ∇·J = 0
```

For probability density |ψ|² in quantum mechanics, this is automatically satisfied by the
Schrödinger equation. For Cs-137 activity density C in soil, it becomes the diffusion equation.

### 10.3 The Laplacian

The **Laplacian** is the divergence of the gradient — the second-order operator:

```
∇²f = ∇·(∇f) = ∂²f/∂x² + ∂²f/∂y² + ∂²f/∂z²
```

It measures the curvature of f at every point. Positive Laplacian: f is below its average
on a surrounding sphere (a "valley"). Negative: f is above (a "peak").

**In the Schrödinger equation:** the kinetic energy operator is:

```
KE = -ħ²/(2m) ∇²
```

High curvature of the wavefunction ↔ high kinetic energy. A rapidly oscillating wavefunction
(short de Broglie wavelength) has large |∇²ψ| and large kinetic energy.

### 10.4 Spherical Coordinates

Central potentials V = V(r) — which include all nuclear and atomic potentials — are natural
in spherical coordinates (r, θ, φ):

```
x = r sinθ cosφ
y = r sinθ sinφ
z = r cosθ

r = √(x²+y²+z²)   θ = arccos(z/r)   φ = arctan(y/x)
```

The Laplacian in spherical coordinates:

```
∇²f = (1/r²) ∂/∂r (r² ∂f/∂r)  +  (1/r²sinθ) ∂/∂θ (sinθ ∂f/∂θ)  +  (1/r²sin²θ) ∂²f/∂φ²
```

For a central potential, the angular part of the wavefunction separates from the radial part:
ψ(r,θ,φ) = R(r) · Y_l^m(θ,φ). The angular equation gives the spherical harmonics Y_l^m
(Module 16); the radial equation determines the energy levels.

### 10.5 The 3D Schrödinger Equation

For a particle in any potential V(r,θ,φ):

```
[-ħ²/(2m) ∇² + V(r,θ,φ)] ψ = E ψ
```

For a central potential V = V(r), separation of variables gives:

```
Radial equation:   [-ħ²/2m · d²/dr² + V_eff(r)] u(r) = E · u(r)
                   V_eff(r) = V(r) + l(l+1)ħ²/(2mr²)
                   u(r) = r·R(r)

Angular equation:  ∇²_angular Y_l^m = -l(l+1) Y_l^m  →  spherical harmonics
```

The `l(l+1)ħ²/(2mr²)` centrifugal term pushes higher-l states to larger radii, producing
the shell structure of atoms and nuclei (Module 16).

### 10.6 The Diffusion-Decay Equation for Radioactive Transport

Cs-137 activity concentration C(r,t) in soil obeys:

```
∂C/∂t = D ∇²C - λC
```

where D is the diffusion coefficient (m²/s) and λ = ln2/t½ is the decay constant.

For a point source of strength M₀ at r=0, t=0:

```
C(r,t) = M₀/(4πDt)^(3/2) · exp(-r²/4Dt) · exp(-λt)
```

A Gaussian spreading in space (width ∝ √t) decaying exponentially in time. This is the
basic model for subsurface radionuclide transport in the CEZ groundwater system.

---

## Module 11: Fourier Transforms — Seeing the Frequency Structure of Physical Systems

### 11.1 Why Fourier Transforms Exist

Every physical signal — a reactor power trace, a geiger counter reading, a radiation spectrum —
is a function of time. A Fourier transform asks: **what oscillating components make up this signal?**

A guitar string plucked at middle C produces not just 261 Hz but also harmonics at 522 Hz, 783 Hz,
etc. The Fourier transform of the sound tells you the amplitude of each frequency. This decomposition
is so fundamental that it applies everywhere:

- A gamma spectrum (counts vs. energy) is a Fourier-related transform of the detector response
- The neutron flux spatial distribution in a reactor is decomposed into spatial harmonics
- The noise spectrum of reactor power fluctuations encodes the underlying neutron kinetics

### 11.2 The Sine and Cosine Functions

Before Fourier transforms, the building block functions:

```
sin(θ): starts at 0, rises to 1 at θ=π/2, returns to 0 at θ=π, drops to -1 at θ=3π/2, ...
cos(θ): starts at 1, drops to 0 at θ=π/2, reaches -1 at θ=π, ...
```

Their derivatives (important):

```
d/dθ [sin(θ)] = cos(θ)
d/dθ [cos(θ)] = -sin(θ)
```

A sinusoidal wave with angular frequency ω and phase φ:

```
f(t) = A · sin(ωt + φ)
```

- A = amplitude (maximum value)
- ω = angular frequency (radians per second) — related to ordinary frequency by ω = 2πf
- Period T = 2π/ω (time for one full cycle)
- Phase φ = offset at t=0

**Euler's formula** (derived from the Taylor series of e^x, sin, and cos):

```
e^(iθ) = cos(θ) + i·sin(θ)
```

where `i = √(-1)` is the imaginary unit. This means complex exponentials `e^(iωt)` encode
both sine and cosine simultaneously — which is why physicists use complex exponentials rather
than trig functions wherever possible.

```
cos(θ) = Re[e^(iθ)] = (e^(iθ) + e^(-iθ)) / 2
sin(θ) = Im[e^(iθ)] = (e^(iθ) - e^(-iθ)) / (2i)
```

### 11.3 The Fourier Transform

The **Fourier transform** of a function f(t) is:

```
F(ω) = ∫[-∞ to +∞] f(t) · e^(-iωt) dt
```

This takes a function of time and produces a function of frequency ω. `F(ω)` tells you the
amplitude and phase of the frequency component ω in f(t).

The **inverse Fourier transform** recovers f(t) from F(ω):

```
f(t) = (1/2π) ∫[-∞ to +∞] F(ω) · e^(+iωt) dω
```

**Key Fourier pairs:**

| f(t) | F(ω) |
|------|------|
| e^(-λ|t|) | 2λ/(λ² + ω²) — Lorentzian |
| e^(-t²/2σ²) | σ√(2π) e^(-ω²σ²/2) — Gaussian → Gaussian |
| δ(t) (spike at t=0) | 1 (all frequencies equally) |
| 1 (constant) | 2π·δ(ω) (only zero frequency) |
| sin(ω₀t) | iπ[δ(ω+ω₀) - δ(ω-ω₀)] |

**The Gaussian pair is fundamental:** A narrow spike in time has broad frequency content. A broad
smooth signal has narrow frequency content. This is the **time-frequency uncertainty** — the same
mathematics as the quantum mechanical uncertainty principle.

### 11.4 The Breit-Wigner as a Fourier Transform

The Breit-Wigner resonance formula:

```
σ(E) ∝ 1 / [(E - E_r)² + (Γ/2)²]
```

is a **Lorentzian in energy**. The Fourier transform of a Lorentzian in frequency is an
exponentially decaying function in time:

```
FT{ 1/[ω² + λ²] } = (π/λ) · e^(-λ|t|}
```

This has a direct physical interpretation: the Breit-Wigner shape in energy is the Fourier
transform of the time-domain decay of the compound nucleus. The width Γ is the decay rate
of the Ba-136* compound nucleus — a short-lived quantum state that forms when a neutron is
captured by Xe-135.

The compound nucleus decays by gamma emission with lifetime `τ = ħ/Γ`. The energy width and
the lifetime are related by the **energy-time uncertainty relation**:

```
Γ · τ = ħ    (the natural linewidth)
```

For Xe-135: Γ ≈ 90 meV (measured), so τ = ħ/Γ ≈ (6.58 × 10⁻¹⁶ eV·s) / (0.090 eV) ≈ 7 × 10⁻¹⁵ s.
The compound nucleus Ba-136* lives for ~7 femtoseconds before emitting a gamma.

### 11.5 Fourier Transforms in Reactor Physics — Neutron Noise Analysis

The power P(t) of an operating reactor is not perfectly constant — it fluctuates slightly due to
the random nature of nuclear fission (neutrons are discrete events, not a continuous fluid). The
**power spectral density** (PSD) of these fluctuations:

```
S_PP(ω) = |FT{ P(t) - ⟨P⟩ }|²  / (measurement time)
```

encodes the reactor's kinetic parameters. The shape of S_PP(ω) is a Lorentzian with:

- Pole at ω = λ_eff = effective precursor decay rate → measurable from the frequency of the roll-off
- Zero-frequency limit → proportional to 1/(β - ρ)² → measures how close to critical the reactor is

This is called **reactor noise analysis** — a non-intrusive way to measure reactor kinetics by
watching the natural fluctuations. The Chernobyl RBMK reactors were monitored this way in their
later operating years.

### 11.6 The Fourier Transform and Differential Equations — The Most Powerful Combination

Taking the Fourier transform of a differential equation converts it to an algebraic equation.
Derivatives in time become multiplication by iω in frequency space:

```
FT{ df/dt } = iω · F(ω)
FT{ d²f/dt² } = (iω)² · F(ω) = -ω² · F(ω)
```

**Example — the diffusion equation for Cs-137 in soil:**

```
∂C/∂t = D · ∂²C/∂x²   - λC
```

where C(x,t) is the Cs-137 concentration, D is the diffusion coefficient in soil, and λ is
the decay constant. Taking the Fourier transform in x (replacing ∂²/∂x² → -k²):

```
dC̃/dt = -Dk² · C̃ - λ · C̃ = -(Dk² + λ) · C̃
```

This is just a first-order ODE in t. Solution:

```
C̃(k,t) = C̃(k,0) · e^(-(Dk² + λ)t)
```

The spatial distribution C(x,t) is then the inverse Fourier transform of this. For a point
source at x=0 initially:

```
C(x,t) = [M₀/(2√(πDt))] · e^(-x²/4Dt) · e^(-λt)
```

A Gaussian spreading in space with width √(4Dt), decaying exponentially in time with rate λ.
This is the basic transport model for groundwater contamination in the CEZ.

---

# Part IV — Quantum Mechanics From Scratch

## Module 12: The Postulates of Quantum Mechanics

Quantum mechanics is not derived from classical physics. It is a framework — a set of rules
for predicting the outcomes of experiments. These postulates are the axioms of that framework.
Every quantum calculation is an application of them.

### 12.1 Postulate 1: States

**The state of a quantum system is completely described by a normalized vector |ψ⟩ in a
complex Hilbert space ℋ, with ⟨ψ|ψ⟩ = 1.**

"Completely" means: there is no hidden information. Two systems in the same state |ψ⟩ are
physically identical in every respect. The Hilbert space is the state space — its dimension
depends on the system.

**Superposition:** If |ψ₁⟩ and |ψ₂⟩ are valid states, then so is α|ψ₁⟩ + β|ψ₂⟩ (normalized).
Superposition is not ambiguity — the system is genuinely in both states simultaneously.

### 12.2 Postulate 2: Observables

**Every physical observable (energy, position, momentum, spin) corresponds to a Hermitian
operator  on ℋ. The only possible outcomes of measuring  are its eigenvalues.**

This is why Hermitian operators matter: their real eigenvalues are the measurement outcomes.
The Hamiltonian Ĥ is the energy operator. The momentum operator is p̂ = -iħ∂/∂x. The spin
operator in the z-direction is Ŝz = (ħ/2)σz.

### 12.3 Postulate 3: The Born Rule (Measurement)

**If the system is in state |ψ⟩ and you measure observable Â, the probability of obtaining
eigenvalue aₙ is:**

```
P(aₙ) = |⟨n|ψ⟩|²
```

**where |n⟩ is the normalized eigenvector of  with eigenvalue aₙ.**

After the measurement, if outcome aₙ is obtained, the state instantaneously becomes |n⟩
("wavefunction collapse"). This is the irreversible, non-unitary part of quantum mechanics.

**Completeness check:** Σₙ P(aₙ) = Σₙ |⟨n|ψ⟩|² = 1. All probabilities sum to 1 because the
eigenstates |n⟩ form a complete orthonormal basis and ⟨ψ|ψ⟩ = 1.

**Expectation value** (average over many measurements):

```
⟨Â⟩ = Σₙ aₙ P(aₙ) = Σₙ aₙ |⟨n|ψ⟩|² = ⟨ψ|Â|ψ⟩
```

### 12.4 Postulate 4: Time Evolution

**Between measurements, the state evolves according to the Schrödinger equation:**

```
iħ d|ψ⟩/dt = Ĥ|ψ⟩
```

This is **deterministic and linear**: given |ψ(0)⟩, the state at every future time is
uniquely determined. Time evolution is unitary: the norm ⟨ψ(t)|ψ(t)⟩ = 1 is preserved
(probability is conserved).

**The tension:** Between measurements, evolution is deterministic (Postulate 4). At the
instant of measurement, there is a random jump (Postulate 3). This is the quantum measurement
problem — still philosophically contested, fully operationally adequate.

### 12.5 Why This Framework Is Powerful

**Everything in quantum mechanics is a calculation using these four rules:**
1. Identify the Hilbert space and the state.
2. Identify the operator corresponding to the observable.
3. Find the eigenvalues and eigenvectors.
4. Compute inner products and probabilities.

The Breit-Wigner formula, the Gamow tunneling calculation, the radical pair spin dynamics,
the antineutrino spectrum, the quantum Fisher information — all of these are applications
of the Born rule to specific systems.

---

## Module 13: Dirac Bra-Ket Notation

Dirac notation is a compact, basis-independent language for quantum mechanics. It makes
the linear algebra transparent and is universally used in physics papers.

### 13.1 Kets, Bras, and Inner Products

**Ket** |ψ⟩: a quantum state vector. Lives in the Hilbert space ℋ. Read as "ket psi."

**Bra** ⟨ψ|: the "dual vector" corresponding to |ψ⟩. If |ψ⟩ is a column vector, ⟨ψ| is
the conjugated row vector: ⟨ψ| = |ψ⟩†. Read as "bra psi."

**Inner product** ⟨φ|ψ⟩: a complex number. Read as "braket phi psi."

```
For column vectors:  ⟨φ|ψ⟩ = φ†ψ = Σᵢ φᵢ* ψᵢ
For functions:       ⟨φ|ψ⟩ = ∫ φ*(x) ψ(x) dx
```

Properties: ⟨φ|ψ⟩ = ⟨ψ|φ⟩*, ⟨ψ|ψ⟩ ≥ 0, and ⟨ψ|ψ⟩ = 0 iff |ψ⟩ = 0.

**Probability amplitude:** ⟨φ|ψ⟩ is the amplitude for finding the state |ψ⟩ in state |φ⟩.
Probability = |⟨φ|ψ⟩|².

### 13.2 Operators in Dirac Notation

An operator  acts on kets: Â|ψ⟩ is another ket. On bras: ⟨ψ|Â (the operator acts to the
left). These are consistently defined so that ⟨φ|Â|ψ⟩ is unambiguous.

**Eigenvalue equation:**

```
Â|n⟩ = aₙ|n⟩
```

|n⟩ is an eigenstate; aₙ is the eigenvalue. In this state, measuring  always gives aₙ.

**Hermitian conjugate (dagger):** (Â)† is defined by ⟨φ|Â†|ψ⟩ = ⟨ψ|Â|φ⟩* for all |φ⟩,|ψ⟩.
Hermitian means  = Â†: ⟨φ|Â|ψ⟩ = ⟨ψ|Â|φ⟩*.

### 13.3 Orthonormality and Completeness

Eigenstates of a Hermitian operator are orthonormal:

```
⟨m|n⟩ = δₘₙ    (= 1 if m=n, = 0 if m≠n)
```

**Completeness (resolution of identity):**

```
Σₙ |n⟩⟨n| = Î
```

This is the most used identity in quantum mechanics. It says: the eigenstates form a complete
basis — the outer products |n⟩⟨n| (projection operators) sum to the identity operator.

**Expanding any state in an eigenbasis:**

```
|ψ⟩ = Î|ψ⟩ = Σₙ |n⟩⟨n|ψ⟩ = Σₙ cₙ|n⟩    where cₙ = ⟨n|ψ⟩
```

The coefficients cₙ are the projections of |ψ⟩ onto each eigenstate. |cₙ|² = probability
of measuring eigenvalue aₙ.

**Normalization check:** ⟨ψ|ψ⟩ = Σₙ |cₙ|² = 1.

### 13.4 The Outer Product and Projection Operators

The **outer product** |ψ⟩⟨φ| is an operator (a matrix, if you think in components):

```
(|ψ⟩⟨φ|)|χ⟩ = |ψ⟩ (⟨φ|χ⟩) = ⟨φ|χ⟩ · |ψ⟩
```

It projects |χ⟩ onto the direction of |φ⟩, then rescales to |ψ⟩.

The **projection operator** onto |n⟩: P̂ₙ = |n⟩⟨n|. It satisfies P̂ₙ² = P̂ₙ (idempotent).

### 13.5 Matrix Elements and Representations

In a basis {|n⟩}, an operator  has matrix elements:

```
Aₘₙ = ⟨m|Â|n⟩
```

The full operator: Â = Σₘₙ |m⟩⟨m|Â|n⟩⟨n| = Σₘₙ Aₘₙ |m⟩⟨n|.

The matrix representation of  in basis {|n⟩} is literally the matrix of numbers Aₘₙ = ⟨m|Â|n⟩.

### 13.6 Position and Momentum Representations

**Position eigenstate |x⟩:** hypothetical state with definite position x. (Strictly speaking,
it is not normalizable in L², but is defined via distributions.)

**Wavefunction:** ψ(x) = ⟨x|ψ⟩. The wavefunction is the inner product of the state with
the position eigenstate — it tells you the "coordinate" of |ψ⟩ in the continuous position basis.

**Momentum operator in position representation:**

```
⟨x|p̂|ψ⟩ = -iħ ∂ψ(x)/∂x
```

Derived from [x̂, p̂] = iħ and the position-space structure.

**Momentum eigenstate:** p̂|p⟩ = p|p⟩. In position space: ⟨x|p⟩ = e^(ipx/ħ)/√(2πħ).
The wavefunction of a state with definite momentum p is a pure plane wave — completely
delocalized in position, confirming the uncertainty principle.

### 13.7 Worked Example — Spin-1/2

Let the system be a spin-1/2 particle. Hilbert space: ℂ². Basis: |↑⟩ = [1,0]ᵀ, |↓⟩ = [0,1]ᵀ.

A general normalized state: |ψ⟩ = α|↑⟩ + β|↓⟩ with |α|²+|β|² = 1.

**Operator Ŝz = (ħ/2)σz = (ħ/2)[[1,0],[0,-1]]:**

```
Eigenstates: Ŝz|↑⟩ = +ħ/2·|↑⟩,   Ŝz|↓⟩ = -ħ/2·|↓⟩
```

**Probabilities of measuring Sz:**

```
P(+ħ/2) = |⟨↑|ψ⟩|² = |α|²
P(-ħ/2) = |⟨↓|ψ⟩|² = |β|²
```

**Expectation value:**

```
⟨Ŝz⟩ = ⟨ψ|Ŝz|ψ⟩ = (α*,β*)·(ħ/2)[[1,0],[0,-1]]·[α,β]ᵀ
       = (ħ/2)(|α|² - |β|²)
```

For |ψ⟩ = (|↑⟩+|↓⟩)/√2: α = β = 1/√2.
P(+ħ/2) = P(-ħ/2) = 1/2. ⟨Ŝz⟩ = 0. Equal probability of up or down; zero average.

---

## Module 14: Solving the Schrödinger Equation I — Particle in a Box

### 14.1 Setup

A particle of mass m in 1D. Infinite square well potential:

```
V(x) = 0       for 0 ≤ x ≤ L
V(x) = ∞       for x < 0 or x > L
```

Why solve this: it is the simplest bound system, it shows exactly how boundary conditions
force quantization, and every more complex bound system (nuclear potential well, atomic
orbitals, quantum dots) is a variation on this structure.

### 14.2 Solving the Schrödinger Equation

Inside the box (V=0), the time-independent Schrödinger equation is:

```
-ħ²/2m · d²ψ/dx² = Eψ

Rearrange:  d²ψ/dx² = -(2mE/ħ²)ψ

Define k² = 2mE/ħ²,  so:  d²ψ/dx² = -k²ψ
```

Solutions to d²ψ/dx² = -k²ψ are oscillatory (for E > 0):

```
ψ(x) = A sin(kx) + B cos(kx)
```

**Boundary conditions:** The wavefunction must vanish at the walls (infinite potential
means zero probability outside):

```
ψ(0) = 0:  B cos(0) = B = 0  →  ψ(x) = A sin(kx)
ψ(L) = 0:  A sin(kL) = 0
```

Since A ≠ 0 (that would give the trivial zero solution), we need sin(kL) = 0, which requires:

```
kL = nπ    for n = 1, 2, 3, ...   (n = 0 is excluded: ψ = 0 everywhere)

Therefore:  kₙ = nπ/L
```

### 14.3 Quantized Energies

Substituting kₙ = nπ/L into k² = 2mE/ħ²:

```
Eₙ = ħ²kₙ²/2m = n²π²ħ²/(2mL²)    n = 1, 2, 3, ...
```

Only discrete energies are allowed. n is the **quantum number**. The energy grows as n² —
the nth state has kinetic energy n² times the ground state energy.

**Normalization:** ∫₀ᴸ |ψₙ(x)|² dx = A² ∫₀ᴸ sin²(nπx/L) dx = A²L/2 = 1  →  A = √(2/L).

**Complete solution:**

```
ψₙ(x) = √(2/L) · sin(nπx/L)       (wavefunction)
Eₙ = n²π²ħ²/(2mL²)               (energy eigenvalue)
```

### 14.4 Zero-Point Energy

The ground state n=1 has energy E₁ = π²ħ²/(2mL²) > 0. The particle is never at rest.

**Origin:** If the particle were at rest at the center x=L/2, it would have Δx ~ L and
Δp ~ 0, violating Δx·Δp ≥ ħ/2. The uncertainty principle forces kinetic energy even in
the ground state. Confine to length L → Δp ≥ ħ/(2L) → ⟨KE⟩ ≥ ħ²/(8mL²) ~ E₁.

**Connection to nuclear physics:** Nucleons inside a nucleus are confined to radius R ~ 1-5 fm.
Their zero-point kinetic energy is ~10-50 MeV (from the particle-in-a-box formula with
L = R). This is why nuclear binding energies are tens of MeV — not eV as in atomic physics.
The particle-in-a-box gives the correct order of magnitude for nuclear energy scales.

---

## Module 15: Solving the Schrödinger Equation II — The Harmonic Oscillator

### 15.1 The Potential V = ½mω²x²

A parabolic potential. Any potential near a stable equilibrium looks parabolic (Taylor expand:
V(x₀+ε) ≈ V(x₀) + ½V''(x₀)ε²). The harmonic oscillator therefore describes:
- Molecular bond vibrations
- Crystal lattice vibrations (phonons)
- Electromagnetic field modes (photons)
- Any small oscillation around equilibrium

Classical solution: x(t) = A cos(ωt + φ), with ω = √(k_spring/m).

### 15.2 The Ladder Operator Method

Instead of solving the differential equation, define two operators:

```
â  = √(mω/2ħ) (x̂ + ip̂/mω)     "lowering" or "annihilation" operator
â† = √(mω/2ħ) (x̂ - ip̂/mω)     "raising" or "creation" operator
```

**Step 1:** Compute the commutator [â, â†].

```
[â, â†] = (mω/2ħ)[x̂ + ip̂/mω, x̂ - ip̂/mω]
        = (mω/2ħ)([x̂,-ip̂/mω] + [ip̂/mω, x̂])
        = (mω/2ħ)(2i[p̂,x̂]/mω)
        = (1/ħ)(i(-iħ)) = 1
```

So [â, â†] = 1. This is the fundamental commutation relation of the harmonic oscillator.

**Step 2:** Express the Hamiltonian in terms of ladder operators.

From the definitions: x̂ = √(ħ/2mω)(â + â†) and p̂ = i√(mħω/2)(â† - â).

```
Ĥ = p̂²/2m + ½mω²x̂²
  = ħω(â†â + ½) = ħω(N̂ + ½)
```

where N̂ = â†â is the **number operator**.

**Step 3:** Find the eigenvalues of N̂.

N̂ is positive semi-definite: ⟨ψ|N̂|ψ⟩ = ⟨ψ|â†â|ψ⟩ = ‖â|ψ⟩‖² ≥ 0. So all eigenvalues n ≥ 0.

The ladder operators step between eigenstates: if N̂|n⟩ = n|n⟩, then:

```
N̂(â|n⟩) = (n-1)(â|n⟩)     → â lowers by 1: â|n⟩ = √n |n-1⟩
N̂(â†|n⟩) = (n+1)(â†|n⟩)   → â† raises by 1: â†|n⟩ = √(n+1)|n+1⟩
```

Since n ≥ 0, there must be a ground state |0⟩ with â|0⟩ = 0 (cannot lower further).

**Step 4:** The energy spectrum.

```
Ĥ|n⟩ = ħω(N̂+½)|n⟩ = ħω(n+½)|n⟩

Eₙ = ħω(n + ½),    n = 0, 1, 2, ...
```

The energy levels are equally spaced by ħω, with zero-point energy E₀ = ħω/2.

**Step 5:** The ground-state wavefunction.

â|0⟩ = 0 means (x̂ + ip̂/mω)|0⟩ = 0. In position space (using p̂ = -iħd/dx):

```
(x + ħ/mω · d/dx)ψ₀(x) = 0
dψ₀/dx = -(mω/ħ)x · ψ₀
```

This ODE has solution: ψ₀(x) ∝ e^(-mωx²/2ħ) — a Gaussian centered at the origin.

### 15.3 Zero-Point Energy and Its Consequences

E₀ = ħω/2 > 0. The oscillator never rests at x=0. The ground state has expectation values
⟨x⟩ = 0 and ⟨p⟩ = 0, but spreads of ⟨x²⟩ = ħ/(2mω) and ⟨p²⟩ = mħω/2.

**Wigner energy in graphite (Problem 6):** Interstitial carbon atoms in radiation-damaged
RBMK graphite sit in potential wells created by the surrounding lattice. Each interstitial is
a quantum oscillator. Its zero-point energy ħω_interstitial/2 contributes to the stored Wigner
energy. The question (Problem 6) is whether quantum tunneling between adjacent wells (at rates
controlled by the oscillator wavefunctions) allows the interstitials to annihilate with vacancies
even when thermal energy k_BT is below the classical activation barrier.

**Phonons:** The normal modes of a crystal lattice are harmonic oscillators. The nth phonon
mode with frequency ωₖ has energy levels Eₙ = ħωₖ(n+½). A "phonon" is one quantum of
lattice vibration — a†|n⟩ = |n+1⟩ creates one phonon. Thermal energy is absorbed by exciting
higher phonon states. Radiation damage that disrupts the lattice creates localized phonon modes
and disrupts thermal conductivity.

**Connection to QFT:** A quantum field is an infinite collection of harmonic oscillators at
every point in space. â† creates a particle; â destroys it. The Fock space of many-particle
states IS the Hilbert space of harmonic oscillator energy eigenstates. The Polyakov paper
referenced in your project (QFT on curved spacetime) is built on this structure.

---

## Module 16: Angular Momentum and Nuclear Shell Structure

### 16.1 Classical Angular Momentum

In classical mechanics: L = r × p (cross product). A vector with three components Lx, Ly, Lz.
It is conserved when the potential is spherically symmetric (V = V(r) only).

### 16.2 Quantum Angular Momentum Operators

Define L̂x = ŷp̂z - ẑp̂y, L̂y = ẑp̂x - x̂p̂z, L̂z = x̂p̂y - ŷp̂x. These inherit the
position-momentum commutator [x̂ᵢ, p̂ⱼ] = iħδᵢⱼ.

The fundamental commutators of angular momentum:

```
[L̂x, L̂y] = iħL̂z
[L̂y, L̂z] = iħL̂x
[L̂z, L̂x] = iħL̂y
```

Consequence: Lx, Ly, Lz cannot all be simultaneously known. Measuring Lx disturbs Ly and Lz.

**What CAN be simultaneously known:** L̂² = L̂x² + L̂y² + L̂z² commutes with all components:
[L̂², L̂z] = 0. So the total magnitude |L| and one component (by convention Lz) can both
have definite values simultaneously.

### 16.3 The Eigenvalue Equations

```
L̂²|l,m⟩ = l(l+1)ħ²|l,m⟩       l = 0, 1, 2, 3, ...
L̂z|l,m⟩ = mħ|l,m⟩              m = -l, -l+1, ..., l-1, l
```

For a given l, there are 2l+1 values of m.

**Notation (spectroscopic):** l=0 (s), l=1 (p), l=2 (d), l=3 (f), l=4 (g). This labels
both atomic orbitals and nuclear single-particle states.

### 16.4 Spherical Harmonics

In spherical coordinates (r,θ,φ) with θ the polar angle and φ the azimuthal angle, the
angular momentum eigenstates are the **spherical harmonics** Y_l^m(θ,φ):

```
L̂²Y_l^m = l(l+1)ħ²Y_l^m
L̂zY_l^m = mħY_l^m
```

They form a complete orthonormal basis for functions on the sphere:

```
∫₀^π ∫₀^{2π} (Y_l^m)* Y_{l'}^{m'} sinθ dθ dφ = δll' δmm'
```

First few:

```
Y₀⁰ = 1/(2√π)                      (s-wave: spherically symmetric)
Y₁⁰ = √(3/4π) cosθ                 (p-wave: lobes along z)
Y₁^{±1} = ∓√(3/8π) sinθ e^{±iφ}   (p-wave: lobes in xy plane)
```

### 16.5 Solving the 3D Schrödinger Equation for a Central Potential

For V = V(r) (no angular dependence), separate variables: ψ(r,θ,φ) = R(r) · Y_l^m(θ,φ).

The radial equation becomes:

```
[-ħ²/2m · d²/dr² + V_eff(r)] u(r) = E · u(r)

where u(r) = rR(r)  and  V_eff(r) = V(r) + l(l+1)ħ²/(2mr²)
```

The second term `l(l+1)ħ²/(2mr²)` is the centrifugal barrier — it pushes states with higher
l to larger radii, creating the shell structure.

### 16.6 Nuclear Shell Structure and Magic Numbers

Nucleons (protons and neutrons) move in the nuclear potential — approximately a Woods-Saxon
well. Solving the 3D Schrödinger equation for this potential gives discrete energy levels
labeled (n, l). Each level holds 2(2l+1) nucleons (factor 2 for spin up/down).

Adding **spin-orbit coupling** Ĥ_SO = -ξ(r)L̂·Ŝ splits each l level into two levels with
j = l + 1/2 and j = l - 1/2. This produces energy gaps at specific nucleon numbers:

```
Magic numbers: 2, 8, 20, 28, 50, 82, 126
```

Nuclei with Z or N equal to a magic number are extra stable (spherical, tightly bound,
narrow resonance widths).

**Connection to the Chernobyl project:**

```
N = 50  →  Sr-90 (N=50) is the dominant A≈90 fission product (Problem 5)
N = 82  →  Cs-137 (N=82), I-131 (N=78), Ba-136 (N=80) are dominant A≈130-140 products
           The double-hump fission yield distribution IS the N=50 and N=82 shell structure
N = 80  →  Ba-136 compound nucleus (two neutrons below N=82 shell closure)
           The near-magic configuration places a level at E_r ≈ 0.084 eV (Problem 1)
```

The Xe-135 giant resonance — the most important nuclear physics fact in the Chernobyl accident
— is a direct consequence of the N=82 nuclear magic number.

---

## Module 17: Spin and Pauli Matrices

### 17.1 Spin as Intrinsic Angular Momentum

Electrons, protons, neutrons, and many nuclei carry "spin" — an intrinsic angular momentum
with no classical analogue. Unlike orbital angular momentum (L), spin cannot be reduced to
position and momentum. It is a fundamental property like charge or mass.

For spin-1/2 particles (electrons, protons, neutrons): spin s = 1/2. The two eigenstates of
Ŝz have eigenvalues ±ħ/2. No matter what axis you choose, only two outcomes are possible.

### 17.2 Spin-1/2 States and the Pauli Matrices

**Basis:** |↑⟩ = [1,0]ᵀ (spin up, Sz = +ħ/2) and |↓⟩ = [0,1]ᵀ (spin down, Sz = -ħ/2).

**Pauli matrices:**

```
σx = [[0, 1],     σy = [[0, -i],    σz = [[1,  0],
      [1, 0]]           [i,  0]]          [0, -1]]
```

**Spin operators:** Ŝᵢ = (ħ/2)σᵢ for i = x,y,z.

**Verify eigenvalues:**

```
Ŝz|↑⟩ = (ħ/2)[[1,0],[0,-1]][1,0]ᵀ = (ħ/2)[1,0]ᵀ = (ħ/2)|↑⟩     ✓
Ŝz|↓⟩ = (ħ/2)[[1,0],[0,-1]][0,1]ᵀ = (ħ/2)[0,-1]ᵀ = -(ħ/2)|↓⟩   ✓
```

**Spin commutators (same structure as orbital):**

```
[Ŝx, Ŝy] = iħŜz    [Ŝy, Ŝz] = iħŜx    [Ŝz, Ŝx] = iħŜy
```

**Pauli matrix algebra:** σᵢσⱼ = δᵢⱼI + iεᵢⱼₖσₖ. Key consequences:

```
σᵢ² = I           (each Pauli matrix squares to identity)
σxσy = iσz        σyσz = iσx        σzσx = iσy
[σᵢ, σⱼ] = 2iεᵢⱼₖσₖ
```

### 17.3 General Spin States and the Bloch Sphere

A general normalized spin-1/2 state: |ψ⟩ = α|↑⟩ + β|↓⟩ with |α|²+|β|² = 1.

Write α = cos(θ/2) and β = e^(iφ)sin(θ/2) (absorbing a global phase). Then:

```
|ψ⟩ = cos(θ/2)|↑⟩ + e^(iφ)sin(θ/2)|↓⟩
```

The angles (θ,φ) parameterize the **Bloch sphere**: every point on the unit sphere is a
distinct spin-1/2 state. North pole = |↑⟩, south pole = |↓⟩, equator = equal superpositions.
The Bloch sphere makes visible that all spin states are equivalent — there is no privileged basis.

### 17.4 Two Spin-1/2 Particles — Tensor Product

When two spin-1/2 systems combine, the joint Hilbert space is the **tensor product**:

```
ℋ_total = ℋ₁ ⊗ ℋ₂     (4-dimensional)
Basis: |↑↑⟩, |↑↓⟩, |↓↑⟩, |↓↓⟩
```

Operators act as: Ŝ₁z ⊗ Î acts on the first spin, Î ⊗ Ŝ₂z acts on the second.

Total spin operator: Ŝ_total = Ŝ₁ + Ŝ₂ = (Ŝ₁ ⊗ Î) + (Î ⊗ Ŝ₂).

**Singlet and triplet states** (total angular momentum eigenstates):

```
Singlet (S=0):  |S⟩ = (|↑↓⟩ - |↓↑⟩)/√2     Ŝ²_total|S⟩ = 0
Triplet (S=1):  |T₊⟩ = |↑↑⟩
                |T₀⟩ = (|↑↓⟩ + |↓↑⟩)/√2     Ŝ²_total|T⟩ = 2ħ²|T⟩
                |T₋⟩ = |↓↓⟩
```

The singlet is antisymmetric under exchange of the two spins: swapping particle labels gives
−|S⟩. The triplet states are symmetric.

### 17.5 The Radical Pair Hamiltonian (Problem 11)

Two hydroxyl radicals OH• are created by gamma radiation in close proximity. Each has one
unpaired electron. The spin Hamiltonian has three terms:

```
Ĥ = ĤZeeman + Ĥ_HFI + Ĥ_exchange

ĤZeeman = -γ_e ħ (Ŝ₁z + Ŝ₂z) B₀        (interaction with external magnetic field)
Ĥ_HFI   = A · Î · Ŝ₁                    (hyperfine coupling: electron spin ↔ proton spin)
Ĥ_exchange = J · (Ŝ₁ · Ŝ₂)             (exchange interaction, decays with separation)
```

The hyperfine term A·Î·Ŝ mixes singlet and triplet states: it drives |S⟩ ↔ |T₀⟩
interconversion. Without this mixing, a pair created in the singlet state would stay singlet
and always recombine; a triplet pair would never recombine. The HFI creates a time-dependent
probability oscillation between singlet and triplet character — and the Earth's magnetic field
B₀ shifts the energy gap between |T₀⟩ and |T±⟩, modulating the interconversion rate.

This is why the Earth's magnetic field affects radiation chemistry: quantum coherence in
spin states of short-lived radical pairs.

---

## Module 18: Commutators and the Uncertainty Principle

### 18.1 The Commutator

For operators Â and B̂:

```
[Â, B̂] = ÂB̂ - B̂Â
```

If [Â, B̂] = 0: the operators **commute**. They share a common eigenbasis. Both observables
can be simultaneously measured — knowing one does not disturb the other.

If [Â, B̂] ≠ 0: they do **not** commute. No common eigenbasis. Measuring one necessarily
disturbs the other.

**Commutator algebra:**

```
[Â, B̂] = -[B̂, Â]                   (antisymmetry)
[Â, B̂+Ĉ] = [Â,B̂] + [Â,Ĉ]          (linearity)
[Â, B̂Ĉ] = [Â,B̂]Ĉ + B̂[Â,Ĉ]         (product rule)
[ÂB̂, Ĉ] = Â[B̂,Ĉ] + [Â,Ĉ]B̂
```

### 18.2 The Canonical Commutation Relation

**Theorem:** [x̂, p̂] = iħ.

**Proof in position representation:**

```
(x̂p̂ - p̂x̂)ψ(x) = x·(-iħ dψ/dx) - (-iħ d/dx)(xψ)
                 = -iħx(dψ/dx) + iħ(ψ + x dψ/dx)
                 = iħψ(x)
```

Since this holds for all ψ: [x̂, p̂] = iħ. □

This single equation encodes the entire wave-particle duality of quantum mechanics.

### 18.3 The Robertson Uncertainty Relation

For any two observables Â and B̂, the product of their standard deviations obeys:

```
σ_A · σ_B ≥ |⟨[Â, B̂]⟩| / 2
```

where σ_A = √(⟨Â²⟩ - ⟨Â⟩²) is the standard deviation of A in state |ψ⟩.

**For position and momentum:** [x̂, p̂] = iħ, so |⟨[x̂,p̂]⟩| = ħ:

```
σx · σp ≥ ħ/2
```

This is the Heisenberg uncertainty principle. It is not about measurement disturbance —
it is a theorem about the mathematical structure of Hilbert space. The Gaussian wavepacket
saturates the bound (equality holds) — it is the minimum uncertainty state.

### 18.4 Compatible and Incompatible Observables

**Compatible:** [Â, B̂] = 0 → simultaneous eigenstates exist → both measurable at once.
Example: [L̂², L̂z] = 0 → l and m can both be sharp simultaneously.

**Incompatible:** [Â, B̂] ≠ 0 → no simultaneous eigenstates → measuring one randomizes the other.
Examples: [L̂x, L̂y] = iħL̂z ≠ 0 (can't know two components of angular momentum);
[x̂, p̂] = iħ ≠ 0 (can't know position and momentum).

### 18.5 The Heisenberg Equation of Motion

For any observable Â (with no explicit time dependence):

```
dÂ/dt = (i/ħ)[Ĥ, Â]
```

This is the quantum analogue of Hamilton's equations in classical mechanics.

**Conservation law:** If [Ĥ, Â] = 0, then dÂ/dt = 0 — the observable is conserved.
Angular momentum is conserved when [Ĥ, L̂] = 0 (i.e., when V = V(r) is spherically symmetric).

**Worked example — L̂z commutes with spherical Hamiltonian:**

For Ĥ = p̂²/2m + V(r): [Ĥ, L̂z] = 0 (the potential depends only on |r|, not on angle φ).
Therefore m is a good quantum number for any central potential — it is conserved.

---

# Part V — Advanced Quantum Tools

## Module 19: Perturbation Theory

When the Hamiltonian is Ĥ = Ĥ₀ + Ĥ', where Ĥ₀ is exactly solvable and Ĥ' is small,
perturbation theory gives corrections order by order in the size of Ĥ'.

### 19.1 Non-Degenerate Time-Independent Perturbation Theory

**Setup:** Ĥ₀|n⁰⟩ = Eₙ⁰|n⁰⟩ is known. Find corrections due to Ĥ'.

**Expand:** Eₙ = Eₙ⁰ + Eₙ¹ + Eₙ² + ...  and  |n⟩ = |n⁰⟩ + |n¹⟩ + |n²⟩ + ...

Substitute into (Ĥ₀ + Ĥ')|n⟩ = Eₙ|n⟩ and collect by order:

**Zeroth order:** Ĥ₀|n⁰⟩ = Eₙ⁰|n⁰⟩  (the unperturbed problem — already solved by assumption).

**First-order energy correction:**

```
Eₙ¹ = ⟨n⁰|Ĥ'|n⁰⟩
```

The first-order energy shift is the expectation value of the perturbation in the unperturbed
state. This is by far the most-used formula in perturbation theory.

**First-order wavefunction correction:**

```
|n¹⟩ = Σ_{m≠n}  [⟨m⁰|Ĥ'|n⁰⟩ / (Eₙ⁰ - Eₘ⁰)]  |m⁰⟩
```

Other states mix into |n⟩, weighted by their matrix elements with Ĥ' and inverse energy
gaps. States far in energy are mixed in less; states close in energy are mixed in more.

**Second-order energy correction:**

```
Eₙ² = Σ_{m≠n}  |⟨m⁰|Ĥ'|n⁰⟩|² / (Eₙ⁰ - Eₘ⁰)
```

Always negative for the ground state (all denominators Eₙ⁰-Eₘ⁰ < 0).

**Convergence condition:** The series converges when |⟨m⁰|Ĥ'|n⁰⟩| << |Eₙ⁰-Eₘ⁰| for all m.
The perturbation must be small compared to level spacings.

### 19.2 Degenerate Perturbation Theory

When multiple unperturbed states share the same energy Eₙ⁰, the first-order formula
1/(Eₙ⁰-Eₘ⁰) has zero in the denominator and diverges. The fix: within the degenerate
subspace, diagonalize Ĥ' to find the correct zeroth-order states first, then proceed.

The correct zeroth-order states are the eigenstates of the matrix ⟨k⁰|Ĥ'|j⁰⟩ restricted
to the degenerate subspace.

### 19.3 Applications to the Project

**Chemical shift on Am-241 α-decay Q value (Problem 3a):**

The decay energy Q = [M(Am) - M(Np) - M(α)]c² + ΔE_electron. The chemical environment shifts
electron binding energies by δε (a few eV). The perturbed Gamow factor:

```
δG/G ≈ -(1/2Q) · δε     (from G ∝ Q^(-1/2) and first-order perturbation)
```

For Q = 5.486 MeV = 5.486×10⁶ eV and δε ~ 10 eV: δG/G ~ 10⁻⁶.

The fractional change in half-life: δt½/t½ ≈ -2δG/G ~ 2×10⁻⁶.
This is a ~1 second shift per year of the Am-241 half-life for a 10 eV chemical shift.
Measurable only with extreme precision spectroscopy of chemically distinct Am-241 compounds.

**Doppler broadening of the U-238 resonance:**

At finite temperature, uranium fuel atoms move. In the rest frame of a moving nucleus,
the neutron's energy is Doppler shifted: E' = E(1 ± v·√(m_n/2E)/c). The cross-section
σ(E') has a resonance at the shifted energy. Averaging over the thermal velocity distribution
(Maxwell-Boltzmann) with the perturbation Ĥ' = kinetic energy of U-238 nucleus gives the
thermally broadened (Doppler-broadened) cross-section. This is the physical mechanism of
the negative Doppler coefficient: higher temperature → broader U-238 resonance → more neutron
absorption → less fission → negative feedback. Perturbation theory quantifies how the cross-
section width grows as √T.

**K-shell binding correction to Klein-Nishina (Problem 8):**

In heavy atoms (Pb, Z=82), K-shell electron binding energy ~88 keV is not negligible compared
to 662 keV. The free-electron KN formula is the zeroth-order solution; the binding energy
V_binding is the perturbation. The Impulse Approximation computes the first-order correction
by replacing the free-electron momentum eigenstate in the KN matrix element with the bound
K-shell wavefunction — a perturbation theory calculation.

---

## Module 20: Statistical Mechanics

### 20.1 The Bridge from Quantum to Thermal

A macroscopic system has ~10²³ degrees of freedom. The quantum state is a vector in a
Hilbert space of dimension ~10^(10²³) — incomprehensibly large. Statistical mechanics
replaces the exact quantum state with a probability distribution over states.

### 20.2 Microstates and Entropy

A **microstate** is a complete quantum specification (all quantum numbers for every particle).
A **macrostate** is specified by macroscopic variables: temperature T, volume V, energy E.
Many microstates correspond to the same macrostate.

**Boltzmann entropy:**

```
S = k_B ln(Ω)
```

where Ω is the number of microstates compatible with the macrostate and k_B = 1.381×10⁻²³ J/K
is Boltzmann's constant. Entropy measures ignorance: more microstates → more entropy.

**Temperature from entropy:**

```
1/T = ∂S/∂E     (at fixed V, N)
```

Heat flows from high T to low T because this maximizes total entropy — a theorem, not an
assumption.

### 20.3 The Boltzmann Distribution

For a system in thermal equilibrium with a heat bath at temperature T, the probability of
finding the system in a specific quantum state with energy Eᵢ is:

```
P(Eᵢ) = e^(-Eᵢ/k_BT) / Z
```

**The partition function:**

```
Z = Σᵢ e^(-Eᵢ/k_BT)
```

Sum over all quantum states. Z encodes all thermodynamic information.

**Thermal averages:**

```
⟨E⟩ = -∂ ln Z/∂(1/k_BT) = Σᵢ Eᵢ e^(-Eᵢ/k_BT) / Z
⟨A⟩ = Σᵢ Aᵢ e^(-Eᵢ/k_BT) / Z     (for any observable A)
```

**Free energy:** F = -k_BT ln Z. At fixed T and V, equilibrium minimizes F.

### 20.4 Maxwell-Boltzmann Distribution for Neutrons

Neutrons in a reactor thermalize through collisions with the moderator (graphite in the RBMK)
and reach a Maxwell-Boltzmann equilibrium at the moderator temperature T ~ 600 K.

**Energy distribution:**

```
f(E) = (2π)/(πk_BT)^(3/2) · √E · e^(-E/k_BT)
```

Peak at E_peak = k_BT/2. At T = 600 K: k_BT = 0.052 eV, E_peak ≈ 0.026 eV.

**The Xe-135 resonance at E_r = 0.084 eV:** This sits in the high-energy tail of the thermal
distribution at 600 K. The Boltzmann factor e^(-0.084/0.052) ≈ 0.20 — 20% of thermal
flux. Combined with the 2.65×10⁶ barn cross-section, the effective absorption rate is still
enormous. The thermally-averaged cross-section:

```
⟨σv⟩ = ∫₀^∞ σ(v) v f(v) dv
```

For a 1/v cross-section (low energy): ⟨σ⟩ ∝ 1/√T — higher temperature means lower effective
absorption. But Xe-135 is not 1/v — it has a resonance. This makes the temperature dependence
of Xe-135 poisoning non-trivial and dependent on the exact reactor temperature.

### 20.5 Quantum Statistics: Fermions and Bosons

At low temperatures or high densities, quantum statistics matter:

**Fermions** (half-integer spin: electrons, protons, neutrons): obey the **Pauli exclusion
principle** — no two identical fermions can occupy the same quantum state.

```
Fermi-Dirac distribution: f(E) = 1 / (e^((E-µ)/k_BT) + 1)
```

At T→0: f(E) = 1 for E < µ (Fermi energy) and 0 for E > µ. All states filled up to µ.

**Bosons** (integer spin: photons, pions, alpha particles): no exclusion principle.

```
Bose-Einstein distribution: n(E) = 1 / (e^((E-µ)/k_BT) - 1)
```

**Nuclear shell filling:** Protons and neutrons are fermions. Each nuclear energy level (n,l,j)
holds 2j+1 nucleons (spin degeneracy). The Fermi exclusion principle forces nucleons into
higher and higher energy levels — the nuclear Fermi energy is ~30 MeV. The ground state of
a nucleus is not all nucleons at the lowest level — it is all levels filled up to the Fermi
surface. This is the quantum statistical foundation of the shell model.

---

## Module 21: Density Matrices and Open Quantum Systems

### 21.1 The Need for Density Matrices

The state vector |ψ⟩ describes a system when you have complete quantum knowledge. Two
situations require more:

1. **Statistical mixture:** You know the system is in |ψ₁⟩ with probability p₁ or |ψ₂⟩
   with probability p₂ — classical uncertainty on top of quantum mechanics.
2. **Entanglement with environment:** The system has interacted with external degrees of
   freedom (heat bath, environment). The full system+environment state is pure, but the
   system alone is not.

Both cases are handled by the **density operator (density matrix)** ρ̂.

### 21.2 Definition and Properties

**Pure state:** ρ̂ = |ψ⟩⟨ψ|.

**Mixed state:** ρ̂ = Σᵢ pᵢ |ψᵢ⟩⟨ψᵢ|   with pᵢ ≥ 0 and Σᵢ pᵢ = 1.

Properties (must hold for any valid density matrix):

```
Tr(ρ̂) = 1                      (normalization)
ρ̂ = ρ̂†                         (Hermitian)
Eigenvalues ≥ 0                 (positive semi-definite)
Tr(ρ̂²) ≤ 1, = 1 iff pure        (purity: 1 for pure, < 1 for mixed)
```

**Expectation value:**

```
⟨Â⟩ = Tr(ρ̂ Â)
```

This works for both pure and mixed states, replacing ⟨ψ|Â|ψ⟩.

### 21.3 Time Evolution

**Closed system (von Neumann equation):**

```
iħ dρ̂/dt = [Ĥ, ρ̂]
```

This is the density matrix version of the Schrödinger equation. For a pure state
ρ̂ = |ψ⟩⟨ψ|, it is exactly equivalent to iħ d|ψ⟩/dt = Ĥ|ψ⟩.

In the energy eigenbasis, ρₘₙ(t) = ρₘₙ(0) e^(-i(Eₘ-Eₙ)t/ħ). Diagonal elements ρₙₙ (the
"populations") are constant. Off-diagonal elements ρₘₙ (the "coherences") oscillate.

**Open system (Lindblad master equation):**

When the system interacts with an environment it cannot be avoided — every real system does
— the von Neumann equation must be augmented with dissipation terms:

```
dρ̂/dt = -i[Ĥ,ρ̂]/ħ + Σₖ γₖ (L̂ₖρ̂L̂ₖ† - ½L̂ₖ†L̂ₖρ̂ - ½ρ̂L̂ₖ†L̂ₖ)
```

The **Lindblad operators** L̂ₖ describe the decay/decoherence channels; γₖ are their rates.
Common examples:
- Spontaneous emission: L̂ = |g⟩⟨e| (excited → ground state), rate γ = 1/τ.
- Dephasing: L̂ = σz, rate γ_φ. Decays the off-diagonal elements without changing populations.

### 21.4 Decoherence

When a quantum system interacts with an environment, the off-diagonal elements of ρ̂ decay:

```
ρₘₙ(t) → ρₘₙ(0) e^(-Γ_decoherence t)
```

The system transitions from a quantum superposition (ρ with nonzero off-diagonal elements)
to a classical mixture (ρ that is diagonal in the pointer basis). This is **decoherence** —
the mechanism that makes macroscopic objects behave classically.

For a heavy nucleus or a neutron in a reactor core, decoherence timescales are ~10⁻²⁰ s —
far below any observation timescale. For radical pairs (Problem 11), decoherence from solvent
fluctuations occurs on ~ns timescales, comparable to the radical pair lifetime, making quantum
coherence observable in their chemistry.

### 21.5 The Reduced Density Matrix

For a composite system AB with Hilbert space ℋ_A ⊗ ℋ_B, the **reduced density matrix** for
subsystem A is:

```
ρ̂_A = Tr_B(ρ̂_AB)
```

where Tr_B means trace over the B degrees of freedom (sum over a complete B basis):

```
(ρ_A)ᵢⱼ = Σₖ ⟨i_A, k_B|ρ̂_AB|j_A, k_B⟩
```

The reduced density matrix gives all predictions for measurements on A alone, correctly
accounting for entanglement with B. If A and B are entangled, ρ_A is a mixed state even
though ρ_AB is pure.

### 21.6 The Radical Pair Density Matrix (Problem 11)

The two-electron spin system has a 4×4 density matrix ρ̂ in the basis
{|↑↑⟩, |↑↓⟩, |↓↑⟩, |↓↓⟩}.

Initially (immediately after radical pair creation), the state depends on the reaction that
created it. For a pair created in the singlet state:

```
ρ̂(0) = |S⟩⟨S| = ½ [[0,0,0,0],
                      [0,1,-1,0],
                      [0,-1,1,0],
                      [0,0,0,0]]
```

The Stochastic Liouville Equation (SLE) governs the evolution:

```
dρ̂/dt = -i[Ĥ_spin, ρ̂]/ħ  - kₛ P̂ₛρ̂  - kₜ P̂ₜρ̂
```

where P̂ₛ = |S⟩⟨S| projects onto singlet and P̂ₜ = |T⟩⟨T| projects onto triplet.
kₛ >> kₜ: singlet pairs recombine rapidly; triplet pairs do not.

The **singlet yield** (fraction of pairs that recombine) is:

```
Φₛ = kₛ ∫₀^∞ Tr(P̂ₛ ρ̂(t)) dt
```

This integral over the density matrix evolution, driven by the hyperfine Hamiltonian, is
what the Earth's magnetic field modifies. It is a measurable quantity in radiation chemistry
experiments — and its modification by magnetic fields is the quantum mechanically grounded
source of tissue-specific radiosensitivity variation hypothesized in Problem 11.

---

## Module 22: The WKB Approximation — Derived From the Schrödinger Equation

### 22.1 Starting Point

The time-independent Schrödinger equation in one dimension:

```
d²ψ/dx² = -(2m/ħ²)[E - V(x)] ψ(x) = -p(x)²/ħ² · ψ(x)
```

where p(x) = √(2m[E-V(x)]) is the local classical momentum (real if E > V).

In a classically forbidden region (V > E): p(x) = iκ(x) where κ(x) = √(2m[V(x)-E])/ħ > 0.

### 22.2 The WKB Ansatz

Write ψ(x) = A(x) · exp(iS(x)/ħ) for some complex functions A(x) and S(x).

Substitute into the Schrödinger equation and expand in powers of ħ.

The leading-order (classical) equation for S'(x):

```
[S'(x)]² = p(x)²     →     S'(x) = ±p(x)
```

This is just the classical momentum. The leading-order WKB solution is:

```
Allowed region (E > V):    ψ(x) ≈ C/√p(x) · exp(±i∫ᵡ p(x')dx'/ħ)
Forbidden region (E < V):  ψ(x) ≈ C/√κ(x) · exp(-∫ᵡ κ(x')dx')     (decaying)
```

The 1/√p(x) amplitude factor is physically meaningful: where p is small (near classical
turning points), the particle moves slowly, so the wavefunction amplitude is large. The
WKB fails precisely where p(x) → 0 (the turning points), because the slowly-varying
approximation breaks down.

### 22.3 The Gamow Factor

The transmission probability through a barrier from x₁ to x₂ (the classical turning points):

```
T = exp(-2G)     where G = ∫[x₁ to x₂] κ(x) dx = (1/ħ) ∫[x₁ to x₂] √(2m[V(x)-E]) dx
```

This is the Gamow integral used in Module 24. The WKB is the justification:
- The wavefunction decays as exp(-G) through the barrier.
- The transmission probability is |ψ(x₂)/ψ(x₁)|² ≈ exp(-2G).

**Validity condition:** The approximation requires that the potential varies slowly compared
to the local de Broglie wavelength: |dλ/dx| << 1, or equivalently |dp/dx| << p²/ħ.
For the Coulomb barrier in α decay, this is satisfied well away from the turning points and
the nuclear surface.

### 22.4 Connection Formulas at Turning Points

Near a classical turning point x₀ (where p(x₀) = 0), the potential is approximately linear:
V(x) ≈ E + V'(x₀)(x-x₀). The Schrödinger equation near x₀ becomes Airy's equation:
d²ψ/dz² = zψ, with solution the **Airy functions** Ai(z) and Bi(z).

The WKB wavefunctions on either side must be matched through the Airy function. This matching
gives the **connection formulas** that link the oscillating WKB solution in the classically
allowed region to the decaying WKB solution in the forbidden region.

For a barrier between turning points x₁ and x₂:

```
Allowed (x < x₁):   ψ ~ A/√p · cos(∫[x₁] p dx'/ħ - π/4)
Forbidden (x₁<x<x₂): ψ ~ (A/2)/√κ · exp(-∫[x₁] κ dx'/ħ)
Allowed (x > x₂):   ψ ~ A/√p · sin(∫[x₂] p dx'/ħ + π/4)  × e^(-G)  (transmitted)
```

The factor e^(-G) is the Gamow factor. The transmitted amplitude is suppressed by e^(-G)
relative to the incident amplitude — exponentially small when G >> 1.

### 22.5 Beyond WKB: Pre-Formation Probability

The WKB tunneling factor T = e^(-2G) is necessary but not sufficient for alpha decay.
The full decay rate is:

```
λ = ν · P_α · T
```

- ν ~ 10²¹ s⁻¹: the assault frequency (how often the α "tries" the barrier), computed from
  the de Broglie wavelength inside the nucleus.
- P_α ~ 0.1-0.3: the **pre-formation probability** — the probability that the nuclear
  wavefunction of Am-241 has a configuration where 2 protons + 2 neutrons are simultaneously
  in an alpha-particle cluster at the nuclear surface. This requires computing the overlap
  between the Am-241 ground state and the Np-237 × α product state.
- T = e^(-2G): the tunneling probability from WKB.

P_α requires the full nuclear shell model wavefunction. For Am-241 (Z=95, N=146), this
is a deformed nucleus in the actinide region — the Nilsson model plus BCS pairing theory
is needed to compute P_α from first principles. This is the open calculation in Problem 3b.

---

# Part VI — Physics Applications

## Module 23: The Breit-Wigner Formula in Full

Now that you have partial derivatives, Fourier transforms, and the concept of a resonance,
the Breit-Wigner formula can be read in full.

### 7.1 The de Broglie Wavelength

Quantum mechanics assigns every particle a wavelength:

```
λ_dB = h/p = h/√(2mE)
λ̄ = ħ/p = ħ/√(2mE)     (reduced wavelength)
```

For a thermal neutron at E = 0.025 eV:

```
p = √(2 × 1.675×10⁻²⁷ kg × 0.025 × 1.6×10⁻¹⁹ J) = 3.64×10⁻²⁴ kg·m/s
λ̄ = 1.055×10⁻³⁴ / 3.64×10⁻²⁴ = 2.90×10⁻¹¹ m = 0.29 Å
πλ̄² = 2.64×10⁻²¹ m² = 2.64×10⁷ barns
```

The **geometric cross-section** of the neutron wave is `πλ̄²` — orders of magnitude larger than
the physical nuclear radius (~10 fm = 10⁻¹⁴ m, so πR² ~3 barns). At thermal energies, a neutron
is a quantum wave spread over an Ångström — thousands of times larger than the nucleus.

### 7.2 The Full Formula

```
σ(E) = πλ̄² · g · (Γ_n · Γ_γ) / [(E - E_r)² + (Γ/2)²]
```

- `πλ̄²` = geometric cross-section of the neutron wave — sets the scale
- `g` = statistical spin factor = (2J+1)/[(2s₁+1)(2s₂+1)] — probability of forming the right spin state
- `Γ_n` = neutron width — partial width for the compound nucleus to re-emit a neutron
- `Γ_γ` = radiation width — partial width for the compound nucleus to emit a gamma and "stick"
- `Γ = Γ_n + Γ_γ` = total width (sum over all decay modes)
- `E_r` = resonance energy — the energy at which the compound nuclear level sits

For Xe-135: `E_r = 0.084 eV`, `Γ ≈ 0.090 eV`, `Γ_n/Γ ≈ 10⁻³` (radiation capture dominates).

At `E = E_r`:

```
σ_max = πλ̄² · g · Γ_n · Γ_γ / (Γ/2)²
       = πλ̄² · g · 4Γ_n/Γ · Γ_γ/Γ
```

Even though `Γ_n/Γ ~ 10⁻³`, the `πλ̄²` factor at 0.084 eV is enormous. The result: 2.65 × 10⁶ barns
— the highest thermal neutron absorption cross-section of any nuclide.

**Why the RBMK was vulnerable:** At rated power, Xe-135 builds up to equilibrium poisoning of ~5%.
After a power reduction (as occurred in the hours before the accident), Xe-135 continues to build
because its parent I-135 (t½ = 6.57 hr) decays into more Xe-135 faster than the Xe-135 is burned
out. The xenon pit makes the reactor nearly impossible to restart from low power — which led operators
to withdraw most control rods to maintain criticality, destroying the safety margin.

---

## Module 24: The Gamow Tunneling Integral in Full

### 24.1 Quantum Mechanical Tunneling

In quantum mechanics, the state of a particle is described by a **wavefunction** ψ(x). The
probability of finding the particle at position x is |ψ(x)|².

In classically forbidden regions (where V(x) > E), the Schrödinger equation:

```
-ħ²/(2m) · d²ψ/dx² + V(x)ψ = Eψ
```

has solutions that are **decaying exponentials** rather than oscillating:

```
Inside classically accessible region (V < E):  ψ ~ e^(±ikx)    (oscillating)
Inside classically forbidden region (V > E):   ψ ~ e^(±κx)    (exponential)
```

where `k = √(2m(E-V))/ħ` and `κ = √(2m(V-E))/ħ`.

The wavefunction **does not go to zero** at the classical turning point — it decays exponentially
into the barrier. If the barrier has finite width, the wavefunction emerges on the other side with
reduced amplitude, and the particle has a nonzero probability of having tunneled through.

### 24.2 The WKB Approximation

When the potential V(r) varies slowly compared to the de Broglie wavelength, the **WKB
(Wentzel-Kramers-Brillouin) approximation** gives the tunneling probability:

```
T ≈ exp(-2G)    where G = ∫[r₁ to r₂] κ(r) dr = (1/ħ) ∫[r₁ to r₂] √(2μ[V(r) - E]) dr
```

The integral G is called the **Gamow factor**. The classical turning points are r₁ (nuclear
surface, where the α particle exits the nuclear potential) and r₂ (where V(r₂) = E and the α
becomes classically free).

### 24.3 The Am-241 Calculation

For Am-241 → Np-237 + α (Z₁=2, Z₂=93, Q = 5.486 MeV):

**Step 1:** Outer turning point:

```
r₂ = k_e · Z₁Z₂e² / Q = 1.44 Z₁Z₂ / Q   [in MeV·fm]
   = 1.44 × 2 × 93 / 5.486 = 48.8 fm
```

**Step 2:** The Gamow integral substituting x = r/r₂:

```
G = (√(2μ·Q)·r₂/ħ) · ∫[r₁/r₂ to 1] √(1/x - 1) dx

  = (√(2μ·Q)·r₂/ħ) · [arccos(√u) - √(u(1-u))]    where u = r₁/r₂
```

**Step 3:** Numerical result:

With µ ≈ 3.73 u = 3.73 × 931.5 MeV/c², Q = 5.486 MeV, r₂ = 48.8 fm, u = 0.178:

```
√(2µQ) · r₂ / ħ ≈ 92 (dimensionless Gamow parameter)
∫ ≈ 0.749
G ≈ 69
T = e^(-138) ≈ 10^(-60)
```

**Step 4:** Converting to half-life:

The alpha particle "attempts" the barrier at a rate ν ~ v/2R ~ 10²¹ per second. The decay
probability per second is ν·T. Half-life:

```
t½ = ln(2) / (ν · T) ≈ 0.693 / (10²¹ × 10⁻⁶⁰) = 0.693 × 10³⁹ s ≈ 10³² years
```

Wait — that is vastly longer than 432.2 years. This is because a pure Coulomb barrier overestimates
G. The nuclear potential is attractive at short range (r < r₁), which modifies the effective r₁
and increases the pre-formation probability. The simple Gamow model gives the right *form* (and the
right Z-dependence — the Geiger-Nuttall law) but the exact half-life requires the pre-formation
probability P_α ~ 0.1–0.3 (Problem 3b in your doc): the probability that Am-241 actually has
an α-cluster configuration at the nuclear surface.

**The physical lesson:** The exponential sensitivity of t½ to G (and hence to Z and Q) is the
reason the Geiger-Nuttall law works over 24 orders of magnitude of half-lives across all alpha
emitters: a 1 MeV change in Q changes t½ by 10⁵.

---

## Module 25: Compton Scattering and Klein-Nishina — QED in the Exclusion Zone

### 9.1 The Compton Formula

When a photon scatters off a free electron, energy is transferred and the photon's wavelength
changes. Derived from relativistic energy-momentum conservation:

```
λ' - λ = (h/mₑc)(1 - cosθ) = λ_C · (1 - cosθ)
```

where `λ_C = h/(mₑc) = 2.43 × 10⁻¹² m` is the Compton wavelength of the electron.

In energy form (using E = hc/λ):

```
E' = E₀ / [1 + (E₀/mₑc²)(1 - cosθ)]    mₑc² = 511 keV
```

For Cs-137 at 662 keV, backscatter (θ = 180°):

```
E' = 662 / [1 + (662/511)(2)] = 662 / [1 + 2.59] = 662 / 3.59 = 184 keV
```

This is a purely kinematic result from special relativity — no quantum mechanics required.
The quantum mechanics enters the **probability** (cross-section) of each scattering angle.

### 9.2 The Klein-Nishina Formula

The differential cross-section for Compton scattering per unit solid angle dΩ:

```
dσ/dΩ = (r_e²/2) · (ω'/ω)² · [(ω/ω') + (ω'/ω) - sin²θ]
```

where:
- `r_e = e²/(4πε₀mₑc²) = 2.818 × 10⁻¹⁵ m` is the classical electron radius
- `r_e² = 7.94 × 10⁻³⁰ m²` = 7.94 × 10² mb (mb = millibarn) — this is the scale of the cross-section
- `ω'/ω = E'/E₀` = the energy ratio at scattering angle θ

The total cross-section (integrate over all angles):

```
σ_KN = 2πr_e² · { [(1+ε)/ε³] · [2ε(1+ε)/(1+2ε) - ln(1+2ε)] + ln(1+2ε)/(2ε) - (1+3ε)/(1+2ε)² }

where ε = E₀/(mₑc²) = E₀/511 keV
```

At 662 keV: ε = 1.295.

Classical Thomson scattering (ε → 0): σ_T = (8π/3)r_e² = 6.65 × 10⁻²⁹ m² = 0.665 barn.
Klein-Nishina at 662 keV: σ_KN ≈ 0.202 barn — a factor of ~3 reduction from relativistic QED.

**The physical content:** At low photon energies (ε << 1), the scattered photon has nearly
the same energy as the incident photon (small Compton shift), and the cross-section approaches
the classical Thomson value. At high energies (ε >> 1), photons lose most of their energy in
a single scatter (the Compton shift is large), and the cross-section decreases as ~ln(ε)/ε —
fewer interactions but more dramatic when they occur.

**Observable in the field:** Every HPGe detector measuring Cs-137 in the exclusion zone records
both the 662 keV photopeak and the 184 keV backscatter peak. The **ratio** of these peaks
in a calibrated geometry is a direct measurement of the Klein-Nishina angular distribution at
θ = 180° — and a 1% measurement precision could begin to see the first-order QED corrections
(double Compton scattering, K-shell binding corrections in heavy shielding materials).

---

## Module 26: Statistical Physics and the Cramér-Rao Bound

### 10.1 Probability Distributions

A **probability distribution** P(x) describes the probability of observing outcome x. For
continuous distributions:

```
P(a ≤ x ≤ b) = ∫[a to b] p(x) dx    where ∫[-∞ to +∞] p(x) dx = 1
```

**Key distributions:**

**Gaussian (Normal):**

```
p(x) = (1/σ√(2π)) · exp(-(x-µ)²/2σ²)
```

Mean = µ, Standard deviation = σ. The bell curve. Arises whenever many independent random
effects add together (Central Limit Theorem).

**Poisson:**

```
P(N = k) = (µᵏ/k!) · e^(-µ)
```

Probability of observing k events when the expected number is µ. Governs radioactive decay
counting, neutron detection, and all other counting processes where events occur independently
at a constant average rate.

For Poisson: Var(k) = µ. So the standard deviation of a count of N is √N.
A detector that counts N atoms has statistical uncertainty `σ/N = 1/√N`.

### 10.2 The Fisher Information

The **Fisher information** quantifies how much information a measurement carries about an
unknown parameter θ. For a probability distribution p(x|θ):

```
F(θ) = E[(d/dθ ln p(x|θ))²] = -E[d²/dθ² ln p(x|θ)]
```

The term `d/dθ ln p(x|θ)` is called the **score** — it measures how sensitively the distribution
changes when θ changes.

**Physical meaning:** High Fisher information means the distribution changes dramatically when
θ changes slightly — the measurement is highly diagnostic of θ. Low Fisher information means
many different values of θ give nearly the same distribution — the measurement cannot distinguish
between them.

### 10.3 The Cramér-Rao Bound

For any **unbiased estimator** `θ̂(x)` of the parameter θ:

```
Var(θ̂) ≥ 1 / (N · F(θ))
```

where N is the number of independent measurements. This bound cannot be beaten — it is a
**fundamental theorem of statistical estimation**, not a practical limitation of current technology.
More measurements help (Var ∝ 1/N), but no clever algorithm can exceed the bound.

### 10.4 Application — Isotopic Attribution Limits

For a measurement of the Cs-134/Cs-137 ratio r = N₁/N₂ by counting N total atoms:

```
F_Q(r) = N / [r(1+r)²]
Var(r̂) ≥ r(1+r)² / N
```

In 2026, four decades after the accident:

- Cs-137: decayed by factor e^(-40λ₁₃₇) = e^(-40×0.0230) = e^(-0.92) ≈ 0.40 (40% remains)
- Cs-134: decayed by factor e^(-40λ₁₃₄) = e^(-40×0.336) = e^(-13.4) ≈ 1.5×10⁻⁶

So r ≈ 1.5×10⁻⁶ in 2026.

To achieve 10% precision (σ/r = 0.10, Var/r² = 0.01):

```
N ≥ (1+r)²/(r × 0.01) ≈ 1/(1.5×10⁻⁶ × 0.01) = 6.7 × 10⁷
```

You need to count ~67 million Cs-137 atoms to detect the Cs-134 signal at 10% precision. For
a 10 Bq sample (typical soil activity), this is a counting time of ~77 days. Feasible but
demanding — and as r decreases further each year, the required count time grows as 1/r, making
Cs-134 attribution increasingly impractical.

**The quantum Fisher information** generalizes this to quantum measurement theory, where the
bound includes quantum projection noise in addition to classical Poisson noise:

```
Var(θ̂) ≥ 1 / F_Q(θ)    (quantum Cramér-Rao bound)
```

For isotope ratio measurements by ICP-MS or gamma spectrometry, the dominant noise is Poisson
(classical), so the quantum and classical bounds coincide for this problem.

---

# Part VII — Synthesis

## Module 27: Reading a Frontier Paper — Example Walkthrough

You now have every tool needed to read the equations in `PROPOSED_DIRECTIONS.md`. Here is a
complete worked example connecting all modules.

### Problem: Verify the Xenon Pit Created the Accident Conditions

**Step 1: Write the Xe-135 balance equation.**

Xe-135 is produced from the decay of I-135 (fission product) and directly from fission, and
is destroyed by radioactive decay and neutron absorption:

```
dN_Xe/dt = λ_I · N_I + γ_Xe · Σ_f · φ  -  λ_Xe · N_Xe  -  σ_Xe · φ · N_Xe
```

where:
- `λ_I` = I-135 decay constant = 0.1045 hr⁻¹ (t½ = 6.57 hr)
- `N_I` = I-135 inventory
- `γ_Xe` = direct fission yield of Xe-135 ≈ 0.002
- `Σ_f · φ` = fission rate per cm³
- `λ_Xe` = Xe-135 decay constant = 0.00753 hr⁻¹ (t½ = 9.17 hr)
- `σ_Xe · φ · N_Xe` = neutron absorption burnout rate

**Step 2: At equilibrium (d/dt = 0), find the steady-state Xe-135 inventory.**

Setting dN_Xe/dt = 0 and solving for N_Xe:

```
N_Xe(eq) = (λ_I · N_I(eq) + γ_Xe · Σ_f · φ) / (λ_Xe + σ_Xe · φ)
```

At full power (high φ), the σ_Xe · φ term in the denominator is large — Xe-135 is burned out
almost as fast as it forms. When power is reduced (φ drops), this burnout term decreases while
I-135 continues to decay, sending more Xe-135 into the core. N_Xe transiently rises above its
new equilibrium — the **xenon peak**.

**Step 3: Quantify the reactivity worth.**

The reactivity inserted by xenon is:

```
ρ_Xe = -Σ_Xe_absorption / (Σ_f · k_∞)  ≈ -(σ_Xe · N_Xe) / (Σ_f / k)
```

At the xenon peak after power reduction, ρ_Xe ≈ -10 to -15% (i.e., -15 β). This is why the
operators had to withdraw essentially all control rods to maintain criticality — the control
rods were compensating for the xenon poisoning by removing negative reactivity, but this meant
there was no reserve margin to insert if needed.

**Step 4: The prompt-critical equation closes the argument.**

With ρ (positive, from removing rods) ≈ +15 β and a sudden void fraction increase due to steam
formation: ρ_void = +α_void · Δα. The RBMK void coefficient α_void ≈ +0.005/% void. When ~50%
of the channels flashed to steam simultaneously: ρ_total exceeded β_eff, and the point kinetics
equation gave:

```
dP/dt = [(ρ_total - β)/Λ] · P > 0  with (ρ-β)/Λ ~ 50-60 s⁻¹
```

Exponential doubling every 12 ms. The physical consequences — fuel fragmentation, steam explosion,
prompt criticality excursion releasing ~3% of total fuel energy in under 4 seconds — follow.

---

## Module 28: Your Equation Toolkit — Quick Reference

```
═══════════════════════════════════════════════════════════════
CALCULUS (Modules 3–5)
───────────────────────────────────────────────────────────────
d/dt [tⁿ]        = n·tⁿ⁻¹
d/dt [eᵃᵗ]       = a·eᵃᵗ         ← most important
d/dt [ln t]      = 1/t
d/dt [sin(ωt)]   = ω·cos(ωt)
d/dt [cos(ωt)]   = -ω·sin(ωt)
Product rule:    d/dt [uv] = u'v + uv'
Chain rule:      d/dt [g(h(t))] = g'(h) · h'(t)
Partial:         ∂f/∂x  (hold other variables fixed)

∫ tⁿ dt          = tⁿ⁺¹/(n+1) + C
∫ eᵃᵗ dt         = eᵃᵗ/a + C
∫ 1/t dt         = ln|t| + C
∫ sin(ωt) dt    = -cos(ωt)/ω + C
∫ cos(ωt) dt    = sin(ωt)/ω + C
∫ √(a-t) dt     = -(2/3)(a-t)^(3/2) + C    ← Gamow piece
Substitution:    u = g(t), du = g'(t)dt
By parts:        ∫ u dv = uv - ∫ v du

═══════════════════════════════════════════════════════════════
LINEAR ALGEBRA (Modules 6–7)
───────────────────────────────────────────────────────────────
Inner product:   ⟨u,v⟩ = Σᵢ uᵢ*vᵢ   (complex vectors)
Norm:            ‖v‖ = √⟨v,v⟩
Orthonormal:     ⟨eᵢ,eⱼ⟩ = δᵢⱼ

Matrix product:  (AB)ᵢⱼ = Σₖ AᵢₖBₖⱼ    (AB ≠ BA in general)
Dagger:          (A†)ᵢⱼ = Aⱼᵢ*  (conjugate transpose)
Hermitian:       A† = A   →  real eigenvalues, orthonormal eigenvectors
Unitary:         U†U = I  →  preserves norms; time evolution is unitary
Trace:           Tr(A) = Σᵢ Aᵢᵢ = sum of eigenvalues
                 Tr(AB) = Tr(BA)   (cyclic)

Eigenvalue eq:   Av = λv   →   det(A-λI) = 0  to find λ
Spectral decomp: A = Σᵢ λᵢ |vᵢ⟩⟨vᵢ|

Pauli matrices:
  σx=[[0,1],[1,0]]  σy=[[0,-i],[i,0]]  σz=[[1,0],[0,-1]]
  σᵢ² = I,  [σᵢ,σⱼ] = 2iεᵢⱼₖσₖ,  Ŝᵢ = (ħ/2)σᵢ

═══════════════════════════════════════════════════════════════
COMPLEX NUMBERS & EULER'S FORMULA (Module 8)
───────────────────────────────────────────────────────────────
i² = -1,  z = a+bi,  |z| = √(a²+b²),  z* = a-bi,  z·z* = |z|²
Taylor: eˣ = 1+x+x²/2!+...  sin=x-x³/3!+...  cos=1-x²/2!+...
Euler:     e^(iθ) = cosθ + i·sinθ
Identity:  e^(iπ) + 1 = 0
Wave:      A·cos(ωt) = Re[A·e^(iωt)]
Rotation:  multiply by e^(iφ) rotates by angle φ in complex plane

═══════════════════════════════════════════════════════════════
ħ, PLANCK & QUANTIZATION (Module 9)
───────────────────────────────────────────────────────────────
ħ = 1.055×10⁻³⁴ J·s = 6.582×10⁻¹⁶ eV·s
ħc = 197.3 MeV·fm            ← memorize
E = hf = ħω,  λ = h/p,  Δx·Δp ≥ ħ/2,  ΔE·Δt ≥ ħ/2
Γ = ħ/τ  (natural linewidth)
Schrödinger: iħ∂ψ/∂t = [-ħ²/2m·∂²/∂x² + V]ψ
Stationary:  ψ(x,t) = φ(x)·e^(-iEt/ħ)

═══════════════════════════════════════════════════════════════
VECTOR CALCULUS (Module 10)
───────────────────────────────────────────────────────────────
∇f = (∂f/∂x, ∂f/∂y, ∂f/∂z)          (gradient — steepest ascent)
∇·F = ∂Fx/∂x + ∂Fy/∂y + ∂Fz/∂z     (divergence — outflow)
∇²f = ∂²f/∂x² + ∂²f/∂y² + ∂²f/∂z² (Laplacian — curvature)
3D Schrödinger: [-ħ²/2m ∇² + V(r)]ψ = Eψ
Force: F = -∇V

═══════════════════════════════════════════════════════════════
FOURIER TRANSFORM (Module 11)
───────────────────────────────────────────────────────────────
F(ω) = ∫[-∞,+∞] f(t)·e^(-iωt) dt
f(t) = (1/2π)∫[-∞,+∞] F(ω)·e^(+iωt) dω
d/dt ↔ iω·F(ω)    (derivative → multiply by iω)
FT{e^(-λ|t|)} = 2λ/(λ²+ω²)  [Lorentzian ↔ exponential decay]
FT{Gaussian} = Gaussian      [σ_t·σ_ω = 1/2: time-frequency uncertainty]

═══════════════════════════════════════════════════════════════
QUANTUM MECHANICS POSTULATES & DIRAC NOTATION (Modules 12–13)
───────────────────────────────────────────────────────────────
State:         |ψ⟩ ∈ ℋ,  ⟨ψ|ψ⟩ = 1
Observable:    Hermitian operator Â,  eigenvalues = outcomes
Born rule:     P(aₙ) = |⟨n|ψ⟩|²
Time evol:     iħ d|ψ⟩/dt = Ĥ|ψ⟩

Braket:        ⟨φ|ψ⟩ = inner product (complex number)
Operator:      Â|ψ⟩ = new ket
Eigenvalue:    Â|n⟩ = aₙ|n⟩
Orthonormal:   ⟨m|n⟩ = δₘₙ
Completeness:  Σₙ |n⟩⟨n| = Î
Expand:        |ψ⟩ = Σₙ cₙ|n⟩  where cₙ = ⟨n|ψ⟩
Expectation:   ⟨Â⟩ = ⟨ψ|Â|ψ⟩ = Tr(ρ̂Â)
Matrix elem:   Aₘₙ = ⟨m|Â|n⟩
Time evol:     |ψ(t)⟩ = Σₙ cₙ e^(-iEₙt/ħ)|n⟩

═══════════════════════════════════════════════════════════════
KEY HAMILTONIANS (Modules 14–17)
───────────────────────────────────────────────────────────────
Particle in box:
  Eₙ = n²π²ħ²/(2mL²),  ψₙ = √(2/L) sin(nπx/L),  n=1,2,3,...
  Zero-point E₁ > 0  (confinement forces kinetic energy)

Harmonic oscillator:
  Ĥ = ħω(â†â + ½),  Eₙ = ħω(n+½)
  [â,â†]=1,  â|n⟩=√n|n-1⟩,  â†|n⟩=√(n+1)|n+1⟩
  Ground state: ψ₀ ∝ e^(-mωx²/2ħ)  (Gaussian)

Angular momentum:
  [L̂x,L̂y]=iħL̂z  (and cyclic)
  L̂²|l,m⟩=l(l+1)ħ²|l,m⟩,  L̂z|l,m⟩=mħ|l,m⟩
  l=0,1,2,...  m=-l,...,+l

Spin-1/2:
  |↑⟩=[1,0]ᵀ,  |↓⟩=[0,1]ᵀ,  Ŝz|↑⟩=+ħ/2|↑⟩
  Singlet: (|↑↓⟩-|↓↑⟩)/√2   Triplet: |↑↑⟩, (|↑↓⟩+|↓↑⟩)/√2, |↓↓⟩

Hyperfine (radical pair): Ĥ_HFI = A·Î·Ŝ  (drives S↔T)
Zeeman:                   ĤB = -γ_e ħ Ŝz B₀

═══════════════════════════════════════════════════════════════
COMMUTATORS & UNCERTAINTY (Module 18)
───────────────────────────────────────────────────────────────
[Â,B̂] = ÂB̂ - B̂Â
[x̂,p̂] = iħ  (canonical commutation relation — proved from p̂=-iħ∂/∂x)
Robertson:  σ_A·σ_B ≥ |⟨[Â,B̂]⟩|/2
Heisenberg: σx·σp ≥ ħ/2
Conserved:  [Ĥ,Â]=0 → dÂ/dt = 0

═══════════════════════════════════════════════════════════════
PERTURBATION THEORY (Module 19)
───────────────────────────────────────────────────────────────
Ĥ = Ĥ₀ + Ĥ'  (Ĥ₀ exactly solvable, Ĥ' small)
E¹ₙ = ⟨n⁰|Ĥ'|n⁰⟩                         (1st order energy)
|n¹⟩ = Σ_{m≠n} ⟨m⁰|Ĥ'|n⁰⟩/(Eₙ⁰-Eₘ⁰) |m⁰⟩  (1st order state)
E²ₙ = Σ_{m≠n} |⟨m⁰|Ĥ'|n⁰⟩|²/(Eₙ⁰-Eₘ⁰)    (2nd order energy)

═══════════════════════════════════════════════════════════════
STATISTICAL MECHANICS (Module 20)
───────────────────────────────────────────────────────────────
Boltzmann: P(Eᵢ) = e^(-Eᵢ/k_BT)/Z
Partition:  Z = Σᵢ e^(-Eᵢ/k_BT)
Average:    ⟨A⟩ = Σᵢ Aᵢ e^(-Eᵢ/k_BT)/Z
Entropy:    S = k_B ln Ω
k_B = 1.381×10⁻²³ J/K = 8.617×10⁻⁵ eV/K
At T=300K: k_BT = 0.0259 eV (thermal energy scale)

═══════════════════════════════════════════════════════════════
DENSITY MATRICES (Module 21)
───────────────────────────────────────────────────────────────
Pure:    ρ̂ = |ψ⟩⟨ψ|,  Tr(ρ̂²) = 1
Mixed:   ρ̂ = Σᵢ pᵢ|ψᵢ⟩⟨ψᵢ|,  Tr(ρ̂²) < 1
Always:  Tr(ρ̂) = 1,  ρ̂† = ρ̂,  eigenvalues ≥ 0
Expect:  ⟨Â⟩ = Tr(ρ̂Â)
Evol:    iħ dρ̂/dt = [Ĥ,ρ̂]  (von Neumann equation)
Reduced: ρ_A = Tr_B(ρ_AB)   (trace over environment)
Lindblad: dρ/dt = -i[Ĥ,ρ]/ħ + Σₖ γₖ(LₖρL†ₖ - ½{L†ₖLₖ,ρ})

═══════════════════════════════════════════════════════════════
PHYSICAL EQUATIONS (Modules 23–26)
───────────────────────────────────────────────────────────────
Decay:
  N(t) = N₀ exp(-λt),   t½ = ln2/λ

Bateman (2-body chain):
  N₂(t) = N₁(0)·[λ₁/(λ₂-λ₁)]·[exp(-λ₁t) - exp(-λ₂t)]
  t_peak = ln(λ₂/λ₁)/(λ₂-λ₁)

Point kinetics (reactor power):
  dP/dt = [(ρ-β)/Λ]·P + Σλᵢ Cᵢ
  Prompt-critical: ρ > β  →  t_double = Λ·ln2/(ρ-β)

Breit-Wigner (nuclear resonance):
  σ(E) = πλ̄²·g·ΓₙΓγ / [(E-Eᵣ)²+(Γ/2)²]
  σ_max = πλ̄²·g·4ΓₙΓγ/Γ²   at  E = Eᵣ

Gamow tunneling (WKB):
  T = exp(-2G),   G = (√(2µ)/ħ)·∫[r₁,r₂] √[V(r)-Q] dr

Compton scattering:
  E' = E₀/[1+(E₀/mₑc²)(1-cosθ)]
  Backscatter (θ=180°, E₀=662 keV): E' = 184 keV

Cramér-Rao attribution bound:
  Var(r̂) ≥ 1/(N·F_Q),   F_Q = N/[r(1+r)²]
  For Cs-134/Cs-137 ratio r in 2026 (~10⁻⁶): need N ~ 10⁸

═══════════════════════════════════════════════════════════════
```

---

## Module 29: How to Build Your Own Equations

The equations in `PROPOSED_DIRECTIONS.md` were not looked up — they were assembled from
physical principles using the tools in this lesson. Here is the process.

### The method

**1. Identify what changes and what it changes with respect to.**

Every physical equation starts with: "the rate of change of X with respect to Y is...".
This immediately gives you a differential equation `dX/dY = ...`.

**2. Identify the proportionality.**

- Proportional to X itself → exponential solution
- Proportional to -X → decay
- Proportional to (X_target - X) → exponential approach to equilibrium
- Proportional to position → harmonic oscillator (sine/cosine)

**3. Write the terms, checking dimensions.**

Every term in an equation must have the same physical units. This is not optional — dimension
analysis is the first check that an equation is plausible.

**4. Solve or simplify.**

Use the tools: integrating factor, substitution, Fourier transform.

**5. Find observable consequences.**

Set the derivative to zero to find peaks. Take limits (t→∞, E→E_r) to find asymptotic behavior.
Perturb a parameter and compute the sensitivity using partial derivatives.

### Example: Building the xenon pit equation from scratch

1. What changes? `N_Xe(t)` — the number of Xe-135 atoms.

2. What changes it?

   - I-135 decays into Xe-135 at rate `+λ_I · N_I`
   - Fission directly produces Xe-135 at rate `+γ_Xe · R_fission`
   - Xe-135 decays away at rate `-λ_Xe · N_Xe`
   - Neutrons burn out Xe-135 at rate `-σ_Xe · φ · N_Xe`

3. Write it:

   `dN_Xe/dt = λ_I · N_I + γ_Xe · R_f - (λ_Xe + σ_Xe · φ) · N_Xe`

4. Equilibrium: set dN_Xe/dt = 0, solve for N_Xe(eq).

5. Observable: after a power reduction (φ drops), N_Xe rises transiently above equilibrium.
   The peak occurs when dN_Xe/dt = 0 with the new (lower) φ — a Bateman-type problem.

You just reproduced the xenon poisoning equation from physical reasoning, not from a textbook.
**This is how physics is actually done.**

---

## Appendix: Physical Constants and Units You Will See

```
ħ = 1.055 × 10⁻³⁴ J·s = 6.582 × 10⁻¹⁶ eV·s   (reduced Planck constant)
c = 3.00 × 10⁸ m/s                               (speed of light)
e = 1.602 × 10⁻¹⁹ C                              (elementary charge)
mₑ = 9.109 × 10⁻³¹ kg,  mₑc² = 0.511 MeV        (electron mass)
m_n = 1.675 × 10⁻²⁷ kg, m_n c² = 939.565 MeV    (neutron mass)
1 u (atomic mass unit) = 931.494 MeV/c²
1 barn = 10⁻²⁸ m²                                (nuclear cross-section unit)
1 fm (femtometer) = 10⁻¹⁵ m                       (nuclear size scale)
1 Bq = 1 decay per second                         (activity)
1 PBq = 10¹⁵ Bq
k_e = 1/(4πε₀) = 8.988 × 10⁹ N·m²/C²
k_e e² = 1.44 MeV·fm                             (in nuclear units, very useful)
```

---

## Where to Go Next

This lesson gives you the mathematical language. The frontier questions in `PROPOSED_DIRECTIONS.md`
are now readable — not just as impressive notation but as statements about physical quantities
that can be derived, computed, and tested against data.

The natural next steps in each direction:

| Direction | Next mathematical tool | Problem it unlocks |
|-----------|----------------------|-------------------|
| Numerical computation | `scipy.integrate`, `solve_ivp` | Am-241 Bateman, Gamow integral |
| Complex analysis | Contour integration, residue theorem | Reactor noise spectral density (Prob. 6) |
| Stochastic calculus | Itō SDEs, Fokker-Planck equation | Prompt criticality fluctuations (Prob. 2) |
| Quantum mechanics formalism | Dirac notation `|ψ⟩`, operators, eigenstates | Radical pair spin (Prob. 11), Xenon RMT (Prob. 1) |
| Density matrix formalism | ρ̂ = Σ pᵢ|ψᵢ⟩⟨ψᵢ|, von Neumann equation | Radical pair coherence (Prob. 11) |
| Density functional theory | Variational calculus, functional derivatives | Graphite tunneling (Prob. 6), Proton tunneling (Prob. 10) |
| Information geometry | Riemannian metrics on probability spaces | Quantum Fisher bound in full (Prob. 12) |
| Path integrals | Imaginary-time Feynman path integral | Instanton tunneling rates (Prob. 6, 10) |

---

*Document version: April 2026*
*Lesson designed for: Chernobyl Physics Project — Quantum Investigations, 1986–2058*
*Prerequisites: High school algebra. All calculus derived from first principles within this document.*
