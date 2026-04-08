Citation (Chicago): Dirac, Paul A. M. *The Principles of Quantum Mechanics*. 4th ed. Oxford: Oxford University Press, 1958.

## Challenges of the Theory

**Non-vanishing infinities.** One historical difficulty in the Dirac picture is the appearance of infinities when one tries to interpret the vacuum as an "Electron Sea" of filled negative-energy states. In that picture, vacuum fluctuations make it difficult to assign a stable, frame-independent density to an electron–positron pair. This already suggests that a literal particle-density interpretation is not fundamental.

This becomes clearer once one recalls that no Lorentz frame is preferred. Any physically meaningful description of an electron–positron pair must therefore be written in a Lorentz-covariant form, rather than in terms of a frame-dependent density of an “electron sea.”

---

### Step 1: What is the Dirac field?

The symbol ψ(x) denotes the **Dirac field**. Informally, a field assigns mathematical data to each point x in spacetime. In this case, the data are not a single number, but a four-component object called a **spinor**.

We may write:

ψ(x) = (ψ₁(x), ψ₂(x), ψ₃(x), ψ₄(x))

The variable x labels a point in spacetime. The four components of ψ are needed because the theory must account for:

- spin-up electron states  
- spin-down electron states  
- spin-up positron states  
- spin-down positron states  

Thus, the Dirac field is the relativistic mathematical object used to describe electrons and positrons together.

---

### Step 2: What is a spinor?

A **spinor** is not the same thing as an ordinary vector. A vector transforms in a familiar way under rotations and Lorentz transformations. A spinor transforms differently: it is the kind of object required to describe particles of spin 1/2, such as electrons.

This is why the Dirac field has internal components. Those components are not simply spatial coordinates; they encode the spin and particle–antiparticle structure of the theory.

The following image illustrates the idea that spinor components encode spin structure:

<img width="358" height="219" alt="Spinor structure" src="https://github.com/user-attachments/assets/036d955d-1000-49d0-93ae-abb4f90672ce" />

A useful first intuition is this:

- a two-component spinor is enough for a non-relativistic spin-1/2 particle  
- a four-component Dirac spinor is needed for a relativistic theory that includes both electrons and positrons  

---

### Step 3: Why do we need the Dirac adjoint?

If ψ is a complex spinor, one might first think that its complex conjugate transpose ψ† is enough to build physical quantities. However, relativity places a stronger requirement on the theory: the equations and observables must transform correctly under Lorentz transformations.

For this reason, one defines the **Dirac adjoint**:

ψ̄ = ψ†γ⁰

This is not an arbitrary modification. The extra factor γ⁰ is needed so that combinations built from ψ̄ and ψ transform properly in relativistic spacetime.

So:

- ψ† is the ordinary Hermitian conjugate of ψ  
- ψ̄ is the relativistically correct adjoint used in Dirac theory  

Without the Dirac adjoint, the simplest scalar and current expressions would not have the correct transformation properties.

---

### Step 4: What are the gamma matrices?

The symbols γ⁰, γ¹, γ², and γ³ are the **Dirac gamma matrices**. Together they are written as γ^μ, where the index μ runs over spacetime directions:

μ = 0, 1, 2, 3

Here:

- γ⁰ corresponds to the time direction  
- γ¹, γ², γ³ correspond to the three spatial directions  

These matrices are introduced so that the Dirac equation becomes a relativistic wave equation for spin-1/2 particles. They encode the structure of spacetime directly into the algebra of the theory.

The gamma matrices satisfy specific algebraic relations that make the Dirac equation compatible with special relativity. For the present discussion, the important point is that they allow us to combine spinors into quantities that transform correctly under Lorentz transformations.

---

### Step 5: What is a bilinear?

A **bilinear** is an expression built from two factors of the field, typically one adjoint spinor and one spinor.

The simplest important example is:

ψ̄ψ = ψ†γ⁰ψ

This is called a bilinear because it is linear in ψ̄ and linear in ψ.

Why is this useful? Because ψ by itself is not directly an observable quantity. Its components depend on the representation and on how the spinor transforms. But particular combinations of ψ̄ and ψ can produce quantities with clear physical meaning.

The expression

ψ̄ψ

is a **Lorentz scalar**, meaning it has the same value in every Lorentz frame.

---

### Step 6: What is the conserved current?

Another important bilinear is the **Dirac current**:

j^μ = ψ̄γ^μψ

This object is called a **4-current**. It contains both charge density and spatial current in a single relativistic quantity:

- j⁰ is the charge density  
- j¹, j², j³ are the spatial current components  

This current is important because it is conserved. In relativistic notation, that conservation law is written as:

∂_μ j^μ = 0

This means charge is not created or destroyed locally.

So at this stage we have two especially important expressions:

- ψ̄ψ, a Lorentz scalar  
- j^μ = ψ̄γ^μψ, a conserved 4-current  

These are physically meaningful because they do not depend on an arbitrary choice of frame in the way a naive particle-density picture does.

---

### Step 7: Why are these quantities better than particle density?

To understand why bilinears are preferred, one must distinguish between:

- **field quantities**, which are built directly from ψ and transform properly  
- **particle quantities**, which require us to split the field into particle modes  

In relativistic quantum field theory, the field can be expanded into modes:

ψ(x) = Σ_p (a_p u_p(x) + b_p† v_p(x))

Here:

- u_p(x) and v_p(x) are mode functions  
- a_p is an annihilation operator for an electron  
- b_p† is a creation operator for a positron  

This expansion is useful, but it depends on how one chooses the modes. Under a change of Lorentz frame, the particle interpretation can change. Symbolically, the operators may mix:

a_p → αa_p' + βb_p'†

The important idea is that what one observer calls a particle can become mixed with what another observer interprets as antiparticle content. Therefore, **particle number and particle density are not always observer-independent notions**.

By contrast, ψ̄ψ and j^μ remain well-defined because they are built from the field itself in a Lorentz-covariant way.

---

### Step 8: What do vacuum fluctuations have to do with this?

The vacuum in quantum field theory is not simply “nothing.” It is the lowest-energy state of the field, but it still has nontrivial structure.

For example, one finds:

⟨0 | j^μ(x) | 0⟩ = 0

This means the vacuum has no net current or charge expectation value.

However:

⟨0 | j^μ(x) j^ν(y) | 0⟩ ≠ 0

This means there are still correlations in the vacuum. In other words, the vacuum fluctuates.

This is one reason a literal local particle-density picture becomes problematic. Even when the average current vanishes, the field still has nontrivial correlations. The vacuum is structured, but that structure is not best understood as a simple density of tiny particles sitting in space.

---

### Step 9: Why does the Lorentz transformation matter?

Let Λ denote a Lorentz transformation. Let S_Λ denote the corresponding transformation acting on spinors.

Then the Dirac field transforms as:

ψ(x) → S_Λ ψ(Λ⁻¹x)

The matrix S_Λ is called the **spinor representation** of the Lorentz transformation. It tells us how the components of the spinor change when the spacetime coordinates are Lorentz transformed.

The gamma matrices are chosen so that:

S_Λ⁻¹ γ^μ S_Λ = Λ^μ_ν γ^ν

From this it follows that:

- ψ̄ψ → ψ̄ψ  
- j^μ → Λ^μ_ν j^ν  

So:

- ψ̄ψ is invariant as a scalar  
- j^μ transforms correctly as a 4-vector  

This is exactly why these objects are physically meaningful: they survive the change of frame in the right way.

---

### Step 10: Final interpretation

The main lesson is that the field ψ is more fundamental than any one particle interpretation of it.

A literal “electron sea” picture tries to assign a density to negative-energy states, but that density depends on how one decomposes the field and on which frame one uses. This leads to ambiguities and infinities.

The bilinears ψ̄ψ and j^μ avoid that problem because they are constructed to respect the symmetry of spacetime itself.

Thus, in relativistic quantum field theory, an electron–positron pair is better understood not as a literal density of particles in a sea, but as a structured excitation of the Dirac field. Pair creation and annihilation are then described through the operator structure of the field, rather than by imagining a fixed background of negative-energy electrons.
