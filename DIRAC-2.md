Citation (Chicago): Dirac, Paul A. M. *The Principles of Quantum Mechanics*. 4th ed. Oxford: Oxford University Press, 1958.

## Worked Example: On the Failure of ψ†ψ and the Role of the Adjoint ψ̄

This example illustrates, in a simplified setting, why the quantity ψ†ψ cannot serve as a relativistic observable, and why the Dirac adjoint ψ̄ = ψ†γ⁰ is introduced.

---

### 1. Non-relativistic expectation

In ordinary quantum mechanics, a wavefunction ψ(x) satisfies:

|ψ(x)|² = ψ*(x)ψ(x)

This quantity represents **probability density**, and is invariant under allowed transformations (unitary transformations).

For multi-component systems (e.g., spin), this generalizes to:

ψ†ψ = Σ |ψ_i|²

which remains positive and conserved.

---

### 2. Dirac field structure

In relativistic theory, the Dirac field ψ has multiple components (four in full theory). For illustration, consider a reduced two-component model:

ψ = (ψ₁, ψ₂)

These components may be interpreted schematically as different internal degrees of freedom (e.g., particle/antiparticle contributions).

---

### 3. Lorentz transformations are not unitary

In relativistic quantum theory, changes of inertial frame are described by Lorentz transformations.

The Dirac field transforms as:

ψ → S(Λ) ψ

where S(Λ) is the **spinor representation** of the Lorentz transformation.

Crucially:
> S(Λ) is not unitary.

This distinguishes relativistic transformations from ordinary quantum rotations.

---

### 4. Explicit mixing example

Let us model a transformation by a non-unitary matrix:

S = ( a   b  
      b   a )

with real coefficients.

Take an initial state:

ψ = (1, 0)

Then:

ψ' = Sψ = (a, b)

---

### 5. Evaluate ψ†ψ

Before transformation:

ψ†ψ = 1

After transformation:

ψ'†ψ' = |a|² + |b|²

If S were unitary, this would equal 1.  
But for a non-unitary transformation, in general:

|a|² + |b|² ≠ 1

So:

ψ†ψ → ψ'†ψ' ≠ ψ†ψ

---

### 6. Physical consequence

If ψ†ψ represented a physical density (probability or charge), then:

- Observer A would measure ψ†ψ  
- Observer B would measure ψ'†ψ'  

These would differ.

This contradicts the requirement that physical quantities must be **frame-independent**.

---

### 7. Correct relativistic construction

To obtain a Lorentz-consistent quantity, define the Dirac adjoint:

ψ̄ = ψ†γ⁰

In a two-component analogue, introduce:

G = (1   0  
     0  -1)

and define:

ψ̄ = ψ†G

---

### 8. Evaluate corrected quantity

Compute:

ψ̄ψ = ψ†Gψ

Before transformation:

ψ = (1, 0)

ψ̄ψ = 1

---

After transformation:

ψ' = (a, b)

ψ̄'ψ' = (a, b) · (1   0  
                   0  -1) · (a, b)ᵀ  
         = a² − b²

---

### 9. Invariance condition

The defining property of the Dirac representation is:

S(Λ)† γ⁰ S(Λ) = γ⁰

This ensures:

ψ̄ψ → ψ̄ψ

So although ψ†ψ changes under transformation, ψ̄ψ does not.

---

### 10. Physical interpretation

In the full Dirac theory:

- ψ̄ψ is a Lorentz scalar  
- j^μ = ψ̄γ^μψ is the conserved 4-current  
- j⁰ gives charge density  

These quantities correspond to measurable observables:
- total charge is invariant  
- current transforms consistently  

---

### Conclusion

The failure of ψ†ψ arises because Lorentz transformations are not unitary.

The introduction of ψ̄ = ψ†γ⁰ corrects this by incorporating the structure of spacetime into the definition of inner products.

Thus, relativistic observables must be constructed from ψ̄ψ and ψ̄γ^μψ, not from ψ†ψ.
