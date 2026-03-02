# Asset: [Asset-ID]

## Description
[Description of the asset]

## Revision
[Revision information]

## Content
- [Link to content]

## SOP: Review, Test, and Update Procedure — TVS Device Substitution

### Purpose
Define a repeatable process to evaluate, validate, and document a proposed transient-voltage-suppression (TVS) diode substitution on a PCBA.

### Scope
Applies to all TVS substitutions for production and prototype PCBAs used in product lines covered by this repository.

### Responsibilities
- Requestor: supply proposed part number, reason, and required performance.
- Design engineer: perform electrical/footprint review, simulations, and BOM updates.
- Test engineer: execute bench and on-board tests; record results.
- Quality/Change Control: approve final release and update documentation.

### Prerequisites
- Original and proposed TVS datasheets (full electrical, thermal, and mechanical specs).
- Reference schematic and PCB layout files.
- BOM and procurement data for both parts.
- Test equipment: oscilloscope, pulse generator/surge simulator, source meter, LCR meter, thermal chamber, ESD simulator (IEC 61000-4-2), surge tester (IEC 61000-4-5).
- Assembly capability for prototypes.

### Materials
- Sample quantity: minimum 5–10 populated PCBAs and 5–10 individual components (adjust per product risk).
- Test fixtures and harnesses.
- Inspection tooling (microscope, X‑ray if BGAs).

### Procedure

1. Initial Review
    - Confirm application: unidirectional/bidirectional, working/standoff voltage, expected transients.
    - Compare datasheet key parameters: standoff voltage (VWM), breakdown voltage (VBR), clamping voltage (Vc at specified surge current), peak pulse power (PPP), leakage current, capacitance, response time, and thermal resistance.
    - Verify package/footprint, polarity and pinout, mounting and pad dimensions, and recommended land pattern.
    - Check reliability/qualification: AEC‑Q/automotive grade, moisture sensitivity level (MSL), temperature rating.
    - Identify any differences that could affect circuit behavior (capacitance affecting high-speed lines, leakage adding bias current, lower clamp voltage causing false trips).

2. Risk Assessment
    - Classify risk level (Low/Medium/High) based on functional impact and parameter differences.
    - Determine additional test requirements based on risk (e.g., full surge testing for high-risk changes).

3. Schematic and PCB Impact
    - Validate no schematic changes required. If polarity or footprint differs, prepare schematic/PCB updates and variant documentation.
    - Update 3D models and PCB footprint if necessary; run DRC/DFM checks.

4. Simulation and Analysis
    - Run SPICE or transient simulations using both original and candidate TVS models for representative surge events.
    - Evaluate clamping behavior, voltage seen by protected nodes, and thermal stress.

5. Prototype Build
    - Order samples and populate a minimum set of prototype PCBAs (include control boards with original part).
    - Ensure identical assembly process (reflow profile) to production unless solderability changes require variation.

6. Verification Tests (Bench)
    - Visual and mechanical inspection (microscope; solder fillet, orientation).
    - Continuity and polarity check.
    - DC measurements: leakage current at VWM, reverse stand-off verification.
    - Clamping and breakdown:
      - Apply standardized surge pulses (e.g., 8/20 µs, 10/1000 µs) and record clamping voltage at specified surge current.
      - Compare to original part and datasheet.
    - Energy and power test: verify peak pulse power handling.
    - Capacitance and dynamic impedance (especially for signal-line TVS).
    - Thermal test: power and surge cycles while monitoring device temperature.
    - ESD/surge testing: perform IEC 61000-4-2 (ESD) and IEC 61000-4-5 (surge) tests as applicable.
    - Reflow and solderability: subject sample components to reflow cycles per product profile and inspect.

7. On‑Board Functional Tests
    - Functional verification of the protected circuit (normal operation).
    - Induce representative transients and verify system behavior (no unintended resets, data corruption, or damage).
    - Burn‑in or accelerated stress tests if required.

8. Data Analysis and Pass/Fail Criteria
    - Compare measured values vs original part and datasheet limits.
    - Pass if:
      - Clamping voltage, leakage, capacitance, and energy handling meet or improve upon original requirements.
      - No functional regressions observed.
      - Reliability/thermal performance acceptable.
    - Otherwise classify failure mode and determine corrective action (reject, further evaluation, or design changes).

9. Documentation and Change Control
    - Populate test report with measurements, waveforms, photos, and assembly notes.
    - Update BOM with approved part number, manufacturer, and approved manufacturer list (AML).
    - Update schematic, PCB footprints, and procurement documents if footprints or polarity changed.
    - Submit Engineering Change Notice (ECN) or equivalent for approval; include rollback plan.
    - Obtain sign-offs from design, test, QA, and procurement.

10. Production Release
    - Release updated BOM and fabrication/assembly data to production.
    - Communicate change to stakeholders and update field-support documentation if needed.

### Test Matrix (example)
- Visual inspection: 5 pcs — Pass/fail
- Leakage at VWM: 5 pcs — ≤ original spec
- Clamping @ Ipp (e.g., 10 A): 5 pcs — ≤ original clamping V
- IEC 61000-4-2: 3 boards — functional/no damage
- IEC 61000-4-5 surge: 3 boards — functional/no damage
- Reflow solderability: 5 pcs — no defects

### Sign‑off Checklist
- Datasheet comparison completed
- Simulation results acceptable
- Prototype build completed
- Bench and on‑board tests passed
- BOM, schematic, and footprint updated (if needed)
- ECN approved and signed by Design, Test, QA
- Production notification issued

### Rollback / Contingency
- Keep qualified original part on AML until new part has passed field reliability window.
- If failures occur in production, revert BOM and perform root-cause analysis.

End of procedure.
