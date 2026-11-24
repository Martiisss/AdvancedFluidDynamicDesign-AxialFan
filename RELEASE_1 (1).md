# Axial Fan Design — Release 1

**Advanced Fluid Dynamic Design | Noctua NF-A12x25 PWM**

This release establishes the reference fan specifications, preliminary geometry, material selection and mean-line aerodynamic analysis. Radial analysis and final blade design are reserved for Release 2.

## 1. Specification and dimensionless parameters

### 1.1 Reference fan and operating point

The selected fan is a 120 mm axial fan for electronic cooling, with a nine-blade rotor and PWM speed control.

| Parameter | Value | Basis |
|---|---:|---|
| Maximum rotational speed | 2,000 rpm | Manufacturer |
| Maximum free-air flow | 102.1 m³/h | Manufacturer |
| Maximum static pressure | 2.34 mmH₂O | Manufacturer |
| Rated voltage | 12 V | Manufacturer |
| Typical / maximum electrical input | 1.20 / 1.68 W | Manufacturer |
| Maximum acoustic noise | 22.6 dB(A) | Manufacturer |
| Selected volume flow, $Q$ | 45.6 m³/h | Published P/Q curve |
| Selected static pressure rise, $\Delta p_s$ | 1.52 mmH₂O = 14.906 Pa | Published P/Q curve |
| Air density, $\rho$ | 1.20 kg/m³ | Assumed |
| Dynamic viscosity, $\mu$ | 1.81 × 10⁻⁵ Pa·s | Assumed |

The operating point is selected from matched pressure and flow data at approximately 2,000 rpm. It is not claimed to be the best-efficiency point. Maximum flow and maximum static pressure occur at different operating conditions.

| Flow (m³/h) | Static pressure (mmH₂O) |
|---:|---:|
| 0 | 2.34 |
| 18.7 | 1.92 |
| **45.6** | **1.52** |
| 76.5 | 0.87 |
| 102.1 | 0 |

For the initial lossless Euler calculation, the measured-type static pressure specification is used as a proxy for ideal total pressure rise, $\Delta p_{0,E}\approx\Delta p_s$. This is a modelling assumption, not a physical equivalence. The static fluid-output power is $Q\Delta p_s=0.1888$ W. Actual shaft efficiency cannot be determined from the rated electrical input alone.

### 1.2 Dimensionless parameters (D1)

The definitions follow the course notebooks, using the assumed rotor diameter in Section 2 and angular velocity $\Omega=2\pi N/60=209.440$ rad/s.

| Parameter | Definition | Result |
|---|---|---:|
| Flow coefficient | $\phi=Q/(\Omega D^3)$ | 0.04082 |
| Head coefficient (proxy) | $\psi=\Delta p_s/(\rho\Omega^2D^2)$ | 0.02179 |
| Fluid power coefficient (proxy) | $\hat P_h=\phi\psi$ | 0.00089 |
| Diameter Reynolds number | $Re_D=\rho c_x D/\mu$ | 11,613 |
| Specific speed (proxy) | $\Omega_s=\Omega\sqrt Q/(\Delta p_s/\rho)^{3/4}$ | 3.562 |
| Specific diameter (proxy) | $D_s=D(\Delta p_s/\rho)^{1/4}/\sqrt Q$ | 1.902 |

The Cordier diagram in D1 locates the provisional point at $(D_s,\Omega_s)=(1.902,3.562)$, for comparison with axial-machine design ranges. The location is tentative because of the pressure assumption and does not establish optimum efficiency.

## 2. Geometry description of all the parts of the axial fan

| Component / parameter | Geometry or dimension | Basis |
|---|---|---|
| Frame | Square, 120 × 120 × 25 mm (without pads) | Manufacturer |
| Frame with pads | 120 × 120 × 27 mm | Manufacturer |
| Mounting hole spacing | 105 × 105 mm | Manufacturer |
| Rotor tip diameter | 114 mm | Release 0 assumption; verify |
| Hub diameter | 50 mm | Release 0 assumption; verify |
| Blades | Nine curved, swept blades | Manufacturer description cited in D2 |
| Nominal radial tip clearance | 0.5 mm | Manufacturer |
| Inner frame bore | 115 mm if assumed rotor diameter and nominal clearance are combined | Derived, not measured |
| Blade radial span | 32 mm | Derived from assumed diameters |
| Hub / motor assembly | Central cylindrical assembly containing motor and bearing | Qualitative; axial dimensions pending |
| Motor supports | Struts connecting central motor housing to outer frame | Qualitative; count and dimensions pending |
| Anti-vibration pads | Located at frame corners | Manufacturer |

The rotor has twisted and swept blades; the chord varies along the span. The apparent frontal width is not necessarily the true section chord. Actual radial chord, thickness, twist, sweep and hub depth require measurements or a suitable geometric reference. The manufacturer CAD download can support dimensional inspection, subject to its stated limitations.

The assumed annular flow geometry gives:

$$r_h=25\,\mathrm{mm},\qquad r_t=57\,\mathrm{mm},\qquad r_m=\sqrt{\frac{r_h^2+r_t^2}{2}}=44.011\,\mathrm{mm}$$

$$A=\pi(r_t^2-r_h^2)=0.008244\,\mathrm{m^2},\qquad s_m=\frac{2\pi r_m}{Z}=30.726\,\mathrm{mm}$$

The hub-to-tip ratio is 0.439. The preliminary mean-section chord and blade angles are evaluated in Section 4; these are design estimates, not measured dimensions of the commercial fan. Detailed spanwise geometry will be determined during Release 2.

## 3. Materials and characteristics. Justification

The following material descriptions are based on the manufacturer's specifications. The justification is an engineering interpretation of their function; numerical mechanical properties are not assumed without grade-specific data.

| Component | Material / technology | Engineering justification |
|---|---|---|
| Impeller (blades and polymer hub) | Sterrox® LCP GF30 | Dimensional stability, low creep and thermal expansion help preserve the small tip gap; strength and damping are useful under centrifugal loading and vibration. |
| Frame and integrated supports | PBT ABS GF30 (manufacturer designation) | Glass-fibre reinforcement supports stiffness and dimensional stability of the stationary structure. |
| Corner pads | Silicone rubber | Compliance helps reduce vibration transmission to the mounting structure. |
| Motor hub reinforcement and shaft | Metal; exact alloy not specified | Supports alignment and dimensional precision. |
| Bearing | SSO2 bearing system | Supports rotation and stable rotor positioning; detailed material composition not specified. |
| Motor and electronics | Exact material grades not specified | Provide electromagnetic drive and PWM speed regulation; no quantitative material model is assigned. |

The small tip clearance is particularly relevant to material selection because deformation of the impeller can reduce the available clearance, while a larger clearance increases leakage. No structural or material-property validation is claimed at this stage.

## 4. Mean line analysis (D2)

### 4.1 Velocity triangles

Assuming incompressible flow, uniform axial velocity and no inlet swirl, the mean-section relations are:

$$c_x=Q/A,\qquad U=\Omega r_m,\qquad c_{\theta1}=0,\qquad c_{\theta2}\approx\frac{\Delta p_s}{\rho U}$$

$$\beta_1=\tan^{-1}(U/c_x),\qquad \beta_2=\tan^{-1}[(U-c_{\theta2})/c_x]$$

The relative angles are positive magnitudes measured from the axial direction; they are flow angles, not blade metal angles.

| Quantity | Inlet | Outlet |
|---|---:|---:|
| Axial velocity (m/s) | 1.537 | 1.537 |
| Tangential absolute velocity (m/s) | 0 | 1.348 |
| Absolute flow angle (°) | 0 | 41.25 |
| Relative flow angle (°) | 80.536 | 78.953 |
| Blade speed (m/s) | 9.218 | 9.218 |

The relative velocity ratio is $w_2/w_1=0.8581$, above the conventional De Haller threshold of 0.72. The local flow and work coefficients are $c_x/U=0.166696$ and $c_{\theta2}/U=0.146196$, respectively. They use different definitions from the global D1 coefficients.

### 4.2 Cascade geometry and diffusion factor

For the mean-section cascade, $s=30.726$ mm, $l$ is the chord, and $\sigma=l/s$ is solidity. The D2 model uses the Lieblein diffusion factor and a drag coefficient $C_D=0.02$:

$$DF=1-\frac{\cos\beta_1}{\cos\beta_2}+\frac{s}{2l}\cos\beta_1(\tan\beta_1-\tan\beta_2)$$

$$\tan\beta_m=\frac{\tan\beta_1+\tan\beta_2}{2}$$

$$C_L=2\frac{s}{l}\cos\beta_m(\tan\beta_1-\tan\beta_2)-C_D\tan\beta_m$$

Adopting $DF\leq0.5$ gives a maximum pitch-to-chord ratio of 4.9663 and a minimum chord of 6.1869 mm. At this minimum, the corrected lift coefficient is 1.4307 (1.5419 without drag). Increasing the chord to 8.5847 mm gives the D2 target $C_L=1.0$.

| Chord (mm) | Solidity | DF | Corrected $C_L$ | $Re_c$ |
|---:|---:|---:|---:|---:|
| 6.1869 | 0.2014 | 0.5000 | 1.4307 | 3,833 |
| 8.5847 | 0.2794 | 0.4000 | 1.0000 | 5,319 |
| 9 | 0.2929 | 0.3881 | 0.9487 | 5,576 |
| 12 | 0.3906 | 0.3265 | 0.6837 | 7,435 |
| 15 | 0.4882 | 0.2896 | 0.5248 | 9,293 |
| 20 | 0.6509 | 0.2527 | 0.3658 | 12,391 |
| 25 | 0.8137 | 0.2305 | 0.2704 | 15,489 |
| 30 | 0.9764 | 0.2158 | 0.2068 | 18,587 |

![D2 diffusion factor and lift coefficient versus chord](outputs/D2_DF_CL_vs_cuerda.png)

The 9 mm chord is a rounded aerodynamic candidate satisfying both D2 criteria. A 20 mm chord is retained as a geometric alternative for investigation, not as a confirmed commercial blade dimension. Full numerical results are available in the [D2 case table](outputs/D2_Noctua_casos.csv).

### 4.3 Preliminary blade angles

Using the Carter deviation correlation and zero-incidence assumption implemented in D2, the estimated metal angles and camber are:

| Chord (mm) | Inlet metal angle (°) | Outlet metal angle (°) | Camber angle (°) | Deviation (°) | Stagger (°) |
|---:|---:|---:|---:|---:|---:|
| 8.5847 | 80.536 | 74.586 | 5.950 | 4.366 | 77.561 |
| 9 | 80.536 | 74.946 | 5.590 | 4.007 | 77.741 |
| 20 | 80.536 | 77.486 | 3.050 | 1.466 | 79.011 |

These are preliminary circular-arc-style geometric estimates; the low chord Reynolds numbers and the sensitivity of the deviation correlation limit their reliability. They are not final CAD inputs.

### 4.4 Sensitivity and limitations

| Assumed ideal pressure / static pressure | Outlet relative angle (°) | Minimum chord (mm) | Chord for $C_L=1$ (mm) |
|---:|---:|---:|---:|
| 0.8 | 79.310 | 4.587 | 6.754 |
| 1.0 | 78.953 | 6.187 | 8.585 |
| 1.2 | 78.571 | 8.061 | 10.478 |

The sensitivity factors are hypothetical, not measured efficiencies. The calculations satisfy the internal Euler and cascade balance checks in D2, but do not establish the actual fan performance. Radial variation, tip leakage, profile losses, and three-dimensional effects are not resolved by this mean-line model.

## Conclusions and next steps

Release 1 establishes the operating point, dimensionless parameters, preliminary component geometry, material rationale and mean-section cascade estimates. Remaining geometry measurements should be recorded when available, particularly rotor and hub diameters, blade dimensions and motor supports. The pressure assumption must be reviewed before finalising the rotor design.

Release 2 will address radial analysis, mean-line corrections, blade and rotor design, and expected overall performance. No definitive radial loading or final CAD geometry is selected in this second release.

## References

1. Noctua, [NF-A12x25 PWM — product specifications](https://www.noctua.at/en/products/nf-a12x25-pwm/specifications).
2. Noctua, [NF-A12x25 PWM — technical specification](https://cdn.noctua.at/media/72046e88/Noctua%20NF-A12x25%20PWM%20Specification.pdf?download=true), p. 7, P/Q data (as transcribed in D1 and D2).
3. Course notebooks: [D1 — Fundamentals and dimensional analysis](D1_fundamentals_and_dimensional_analysis.ipynb), [D2 — Mean line analysis and 2D cascade](D2_mean_line_analysis_and_2d_cascade.ipynb).
4. Noctua, [Technical backgrounds and manufacturing challenges](https://www.noctua.at/en/expertise/tech/nf-a12x25-technical-backgrounds).
5. Noctua, [NF-A12x25 PWM — downloads](https://www.noctua.at/en/products/nf-a12x25-pwm/downloads).
6. Dixon, S. L. and Hall, C. A., *Fluid Mechanics and Thermodynamics of Turbomachinery*, 7th ed., 2014, chapters 3 and 5 (equation numbering as used in D2).
