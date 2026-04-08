Citation (Chicago): Dirac, Paul A. M. *The Principles of Quantum Mechanics*. 4th ed. Oxford: Oxford University Press, 1958.

## Challenges of the Theory

**Non-vanishing infinities.** One historical difficulty in the Dirac picture is the appearance of infinities when one tries to interpret the vacuum as an "Electron Sea" of filled negative-energy states. In that picture, vacuum fluctuations make it difficult to assign a stable, frame-independent density to an electron–positron pair.

This suggests that a literal “density of particles in space” is not a reliable or fundamental description.

This becomes clearer once one recalls that no Lorentz frame is preferred. A *frame* is simply an observer’s point of view (for example, moving at constant velocity). A physically meaningful quantity must not depend on which observer describes it.

---

### Step 1: What is a field?

A **field** assigns a value to every point in space and time.

Examples:
- Temperature → a number at each point  
- Electric field → a vector at each point  

In quantum theory, fields are used because particles cannot be consistently described as localized objects alone. Instead, measurable quantities arise from the field.

---

### Step 2: What is the Dirac field?

The Dirac field ψ(x) describes electrons and positrons.

It has four components:

ψ(x) = (ψ₁, ψ₂, ψ₃, ψ₄)

Each component is a complex number.

These correspond to:
- electron spin up  
- electron spin down  
- positron spin up  
- positron spin down  

Thus ψ does not describe a single particle, but all possible local states of the electron–positron system.

---

### Step 3: What is a spinor?

A **spinor** is the mathematical object required to describe particles with spin 1/2.

The distinction is not cosmetic:

- Scalars remain unchanged under rotation  
- Vectors rotate geometrically  
- Spinors transform in a way that cannot be reduced to either  

This difference is experimentally real. For example, electron spin measurements (in units of ℏ/2) cannot be reproduced using ordinary vectors alone.

<img width="358" height="219" alt="Spinor structure" src="https://github.com/user-attachments/assets/036d955d-1000-49d0-93ae-abb4f90672ce" />

---

### Step 4: Why ψ is not directly observable

The components of ψ depend on:
- the observer  
- the coordinate system  

So ψ itself is not observable.

This is similar to classical vectors: their coordinates depend on axes, but physical quantities do not. We therefore seek combinations of ψ that all observers agree on.

---

### Step 5: Why we try ψ†ψ (connection to probability)

In ordinary quantum mechanics:

|ψ(x)|² = ψ*(x)ψ(x)

This gives the **probability density** of finding a particle.

For example, for an electron:
- ∫|ψ(x)|² dx = 1  
- meaning the electron must be somewhere

---

If ψ has multiple components, we extend this idea:

ψ†ψ = |ψ₁|² + |ψ₂|² + |ψ₃|² + |ψ₄|²

Where ψ† means:
- take complex conjugate (i → -i)
- transpose column → row

ψ† = (ψ₁*, ψ₂*, ψ₃*, ψ₄*)

---

#### Why complex conjugation is necessary

If we squared components directly, the result could be complex or negative.

Example:
(1 + i)² = 1 + 2i − 1 = 2i

This is not meaningful as a probability.

Taking the conjugate ensures:

|ψ₁|² = ψ₁*ψ₁ ≥ 0

---

#### Why transpose is needed

ψ is a column vector. To form a scalar:

(row) × (column) → number

So we must convert ψ† into a row.

---

#### Why ψ†ψ seems physically correct

- always non-negative  
- matches probability density  
- consistent with earlier quantum mechanics  

So one expects ψ†ψ to represent a measurable density.

---

### Step 6: Why ψ†ψ fails in relativity

Relativity requires all observers to agree on physical quantities.

The Dirac field transforms as:

ψ(x) → S_Λ ψ(Λ⁻¹x)

Here:
- Λ changes spacetime coordinates  
- S_Λ mixes the components of ψ  

---

#### What S_Λ does (component mixing)

After transformation, components mix:

ψ₁' = a·ψ₁ + b·ψ₃  

So an electron component becomes partly positron.

---

#### Why this breaks ψ†ψ

Originally:

ψ†ψ = |ψ₁|² + |ψ₂|² + |ψ₃|² + |ψ₄|²

After transformation:

|ψ₁'|² = |aψ₁ + bψ₃|²  
= |a|²|ψ₁|² + |b|²|ψ₃|² + cross terms  

So ψ†ψ changes.

---

#### Physical contradiction

If ψ†ψ were a density:
- Observer A gets one value  
- Observer B gets another  

That would mean:
> the same electron has different total probability or charge depending on motion

This is not physically acceptable.

---

### Step 7: The Dirac adjoint ψ̄

To fix this, define:

ψ̄ = ψ†γ⁰

This is the **Dirac adjoint**.

It modifies ψ† so that combinations with ψ behave correctly under transformations.

---

#### Why γ⁰ is needed

Relativity treats time differently from space:

s² = t² − x² − y² − z²

Not all components contribute equally.

γ⁰ ensures that ψ† is corrected so that ψ̄ψ respects this structure.

---

#### Practical effect

- ψ†ψ → changes between observers  
- ψ̄ψ → does not  

So γ⁰ fixes the transformation behavior.

---

### Step 8: Physical quantities (bilinears)

We now construct:

ψ̄ψ = ψ†γ⁰ψ  
j^μ = ψ̄γ^μψ  

---

#### Physical meaning

- ψ̄ψ → scalar (same for all observers)  
- j^μ → charge-current density  

In particular:
- j⁰ = charge density  
- ∫ j⁰ d³x = total charge  

All observers agree on this.

---

#### What “observable” means

An observable quantity:
- can be measured  
- gives the same result for all observers  

Example:
- electron charge is always −e  

ψ̄ψ and j^μ satisfy this.

ψ†ψ does not.

---

### Step 9: Why particle density fails

To define particles:

ψ(x) = Σ_p (a_p u_p + b_p† v_p)

But under transformation:

a_p → αa_p' + βb_p'†  

So particle definition changes.

---

### Conclusion

Particle density depends on observer choice.

ψ̄ψ and j^μ do not.

---

### Step 10: Vacuum fluctuations

Even vacuum has structure:

⟨0 | j^μ | 0⟩ = 0  
⟨0 | j^μ j^ν | 0⟩ ≠ 0  

So empty space is not a collection of static particles.

---

### Final interpretation

The Dirac field ψ is more fundamental than any particle picture.

The “electron sea” interpretation leads to infinities and observer dependence.

By contrast, ψ̄ψ and j^μ:
- correspond to measurable quantities  
- remain consistent across observers  

Thus, an electron–positron pair is best understood as an excitation of the field, not a density of particles in space.
