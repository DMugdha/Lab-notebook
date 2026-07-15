---
title: Ribosomes in FIB-milled lamella
date: 2026-07-15T09:30:00.000Z
operator: M. Researcher
project: Cellular translation atlas
status: in progress
sample_id: CT-2026-014
aim: Resolve the 80S ribosome in situ from lamellae of vitrified HeLa cells.
blocks:
  - type: sample_vitrification
    specimen_type: whole vitrified cells (HeLa)
    organism: Homo sapiens
    grid_type: Quantifoil R2/2 Au 200
    glow_discharge: 30 s, 15 mA
    plunger: Vitrobot Mark IV
    blot_force: 5
    blot_time: 4
    humidity: 100
    chamber_temp: 4
    cryogen: ethane/propane
  - type: fib_milling
    instrument: Aquilos 2
    target_thickness: 180
    milling_angle: 18
    n_lamellae: 12
    pt_coat: true
    milling_software: AutoTEM
  - type: acquisition
    microscope: Titan Krios G4
    voltage: 300
    detector: K3
    slit: 20
    pixel_size: 2.93
    tilt_scheme: dose-symmetric (Hagen)
    tilt_range: -60 to +60
    tilt_increment: 3
    dose_per_tilt: 3.0
    total_dose: 123
    acq_software: PACEtomo
    n_tilt_series: 34
---

Free-text working notes live here. Everything in the block above was captured
through template fields, so it stays structured and searchable; this body is
plain Markdown for anything that doesn't fit a field.
