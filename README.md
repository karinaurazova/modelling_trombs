# Simulation of thrombus growth in a blood vessel

An implementation of the solution to the problem of the number of concentrations of fibrin, thrombin and platelets in a two-dimensional case is presented. 3D and growth models will be added later. stay tuned

A blood clot forms in a blood vessel as a result of damage to the vessel wall. A thrombus is formed due to the activation of platelets, their adhesion to the site of injury and the subsequent formation of a fibrin network. It is necessary to model the process of thrombus growth, taking into account the following factors:

## Hydrodynamics of blood

Blood flows through the vessel at a constant speed \(u\). The dynamics of blood are described by the Navier-Stokes equations for an incompressible fluid:

\[
\frac{\partial \mathbf{u}}{\partial t} + (\mathbf{u} \cdot \nabla) \mathbf{u} = -\frac{1}{\rho} \nabla p + \nu \nabla^2 \mathbf{u},
\]
\[
\nabla \cdot \mathbf{u} = 0.
\]

Where:
- \( \mathbf{u} \) — blood speed,
- \( p \) — pressure,
- \( \rho \) — blood density,
- \( \nu \) — kinematic viscosity.

## Platelet activation

Platelets are activated upon contact with a damaged vessel wall. The concentration of activated platelets \(C_p\) is described by the reaction-diffusion equation:

\[
\frac{\partial C_p}{\partial t} + \mathbf{u} \cdot \nabla C_p = D_p \nabla^2 C_p + R_p,
\]

Where:
- \( D_p \) — platelet diffusion coefficient,
- \( R_p \) — rate of platelet activation, which depends on the concentration of thrombin \(\theta\):

\[
R_p = k_p \theta,
\]

Where:
- \( k_p \) — activation rate constant.

## Thrombin formation

Thrombin \(\theta\) is formed as a result of the coagulation cascade and is described by the equation:

\[
\frac{\partial \theta}{\partial t} + \mathbf{u} \cdot \nabla \theta = D_\theta \nabla^2 \theta + R_\theta,
\]

Where:
- \( D_\theta \) — thrombin diffusion coefficient,
- \( R_\theta \) — the rate of thrombin formation, which depends on the concentration of activated platelets:

\[
R_\theta = k_\theta C_p,
\]

Where:
- \( k_\theta \) — thrombin formation rate constant.

## Formation of fibrin network

The fibrin network \(\psi\) is formed under the influence of thrombin and is described by the equation:

\[
\frac{\partial \psi}{\partial t} = \kappa \theta,
\]

Where:
- \( \kappa \) — fibrin formation rate constant.

## Platelet adhesion

The adhesion of platelets to the site of injury and to each other is described using the Cellular Potts Model (CPM). The energy of the system \(E\) includes the energy of adhesion and the energy associated with blood flow:

\[
E = E_{\text{адгезия}} + E_{\text{поток}},
\]

Where:
- \( E_{\text{адгезия}} \) depends on the interaction between platelets and the vessel wall,
- \( E_{\text{поток}} \) depends on blood speed and pressure.

