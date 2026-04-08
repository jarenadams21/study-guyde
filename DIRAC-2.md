Citation (Chicago): Dirac, Paul A. M. *The Principles of Quantum Mechanics*. 4th ed. Oxford: Oxford University Press, 1958.

## Why ψ†ψ Fails and ψ̄ψ is Required in Relativistic Quantum Mechanics

This worked example shows why the quantity ψ†ψ cannot serve as a relativistic observable, and why it must be replaced by ψ̄ψ = ψ†γ⁰ψ.

---

### 1. Non-relativistic expectation (probability density)

In ordinary quantum mechanics, a wavefunction ψ(x) satisfies:

|ψ(x)|² = ψ*(x)ψ(x)

This represents **probability density**.

Probability density answers the question:
> “If we measure the position of the particle, how likely are we to find it at point x?”

For a particle such as an electron:
- ∫|ψ(x)|² dx = 1  
- meaning the particle must be somewhere in space  

For multi-component wavefunctions (e.g., spin), this generalizes to:

ψ†ψ = Σ |ψ_i|²

This remains:
- positive  
- conserved  
- physically meaningful  

So ψ†ψ is naturally interpreted as a density.

---

### 2. Two-component model (physical interpretation)

To isolate the issue, consider a simplified two-component object:

ψ = (ψ₁, ψ₂)

We interpret:

- ψ₁ → electron-like contribution  
- ψ₂ → positron-like contribution  

This is a simplification of the full Dirac field, which has four components, but it captures the essential feature: **components can mix under relativistic transformations**.

---

### 3. Define the candidate density

We extend the usual rule:

ρ = ψ†ψ = |ψ₁|² + |ψ₂|²

Interpretation:
- ρ is a candidate **probability density** or **charge density**
- it measures “how much of the field is present” at a point

---

### What is charge density?

**Charge density** tells us how much electric charge is located in a small region of space.

For example:
- A single electron has total charge −e  
- If its charge is spread out (quantum mechanically), the density tells us how that charge is distributed in space  

Mathematically:
- ∫ ρ(x) d³x = total charge  

So if ρ were a true charge density, all observers must agree on its total value.

---

### 4. Initial state

Take a simple state:

ψ = (1, 0)

This corresponds to:
- purely electron-like state  
- no positron contribution  

Then:

ρ = 1

---

### 5. Transformation between observers

In relativity, different observers are related by Lorentz transformations.

The Dirac field transforms as:

ψ → S(Λ) ψ

The matrix S(Λ) is not unitary, and it **mixes components**.

For illustration, consider:

S = ( a   b  
      b   a )

with real coefficients.

Apply to the state:

ψ = (1, 0)

Then:

ψ' = (a, b)

---

### 6. Evaluate ψ†ψ carefully

Before transformation:

ρ = ψ†ψ = 1

---

After transformation:

ρ' = ψ'†ψ' = |a|² + |b|²

---

### What determines whether this is valid?

If S were unitary (as in ordinary quantum mechanics), then:

|a|² + |b|² = 1

and ρ would remain unchanged.

However:

> Lorentz transformations are not unitary.

So in general:

|a|² + |b|² ≠ 1

---

### Explicit consequence

ρ → ρ' ≠ ρ

So the value of the “density” changes depending on the observer.

---

### 7. Physical interpretation of the failure

Suppose ρ represented a real observable:

- probability density  
- or charge density  

Then:

- Observer A measures ρ = 1  
- Observer B measures ρ' ≠ 1  

This would imply:

> the same physical system has different total probability or charge depending on the observer

This is not physically acceptable.

- Probability must always sum to 1  
- Charge of an electron must always be −e  

Therefore:

ψ†ψ cannot represent a relativistic observable.

---

### 8. The correct relativistic quantity: j⁰

In relativistic theory, the physically meaningful density is:

j⁰ = ψ̄γ⁰ψ

where:

ψ̄ = ψ†γ⁰

---

### What is j⁰?

j⁰ is the **charge density**.

It tells us:
> how much electric charge is present at a point in space and time

If we integrate it:

∫ j⁰ d³x = total charge

For a single electron:
- this always gives −e  
- all observers agree on this  

So j⁰ is a true observable.

---

### 9. What is current (j¹, j², j³)?

The full object:

j^μ = ψ̄γ^μψ

is called the **current**.

Its components are:

- j⁰ → charge density  
- j¹, j², j³ → flow of charge (current)

---

### Physical meaning of current

Current tells us:
> how charge is moving through space

Example:
- In a wire, current = flow of electrons  
- In quantum theory, j describes how probability/charge flows  

Together:
- j⁰ tells “how much charge is here”  
- jᵢ tells “how it is moving”

---

### 10. Why ψ̄ fixes the problem

Define:

ψ̄ = ψ†γ⁰

In a two-component analogue, use:

G = (1   0  
     0  -1)

Then define:

ρ_correct = ψ† G ψ

---

### Evaluate corrected density

Before transformation:

ψ = (1, 0)

ρ_correct = 1

---

After transformation:

ψ' = (a, b)

ρ_correct = a² − b²

---

### Key property

The Dirac representation satisfies:

S(Λ)† γ⁰ S(Λ) = γ⁰

This ensures:

ρ_correct → ρ_correct

So:

ψ̄ψ is invariant  
ψ†ψ is not  

---

### 11. Physical meaning of the correction

The difference:

ψ†ψ = |ψ₁|² + |ψ₂|²  
ψ̄ψ = |ψ₁|² − |ψ₂|²  

reflects a deeper structure:

- particle and antiparticle contributions enter differently  
- not all components contribute equally  

This matches relativity, where:

s² = t² − x² − y² − z²

Time and space are fundamentally different.

---

### 12. Connection to full Dirac theory (4 components)

In the full Dirac field:

ψ = (ψ₁, ψ₂, ψ₃, ψ₄)

- ψ₁, ψ₂ → electron components  
- ψ₃, ψ₄ → positron components  

The same issue occurs:

- ψ†ψ is not invariant  
- ψ̄ψ and j^μ are invariant  

---

### Final conclusion

The failure of ψ†ψ arises because Lorentz transformations mix components in a non-unitary way.

As a result:
- ψ†ψ depends on the observer  
- ψ̄ψ does not  

The quantities:

ψ̄ψ and j^μ  

are constructed so that they:
- correspond to measurable physical properties (charge and current)  
- remain consistent across all observers  

Thus, relativistic quantum theory requires replacing ψ†ψ with ψ̄ψ = ψ†γ⁰ψ.
