This repository contains sub-repositories of MD simulations of subcritical crack growth in a model glass.

[Required LAMMPS Version]
	This simulation uses a customized GPU-enabled version of LAMMPS with a modified bump. Download the required version here:
	https://github.com/mppotter/lammps.git

[conventional-uniaxialtension-and-sample-preparation] Conventional uniaxialtension test on a bulk glass of 24000 atoms, together with the glass sample preparation.
	--s: LAMMPS script
	--log.lammps Log file during sample preparation
	--log.mech Log file during mechanical test (stress_zz vs strain can be obtained from column 14 and column 10 in log.mech)
	--tobemelted.initial.readdata Initial glass configuration with an average atomic volume of 0.0173 nm^3. This is chosen such that upon NVT cooling, the final glass is stress-free.
	--Other output files include MD trajectories which are not included in this repository.

[glass-sample-preparation] Slab-shaped glass sample preparation (36000 atoms). This slab will be used as the input glass sample for the constant-K MD simulation.
	--s: LAMMPS script (almost identical to the previous script except for the size of the sample)
	--log.lammps Log file during sample preparation
	--tobemelted.initial.readdata Initial glass configuration with an average atomic volume of 0.0173 nm^3. This is chosen such that upon NVT cooling, the final glass is stress-free.
	--glass.readdata Output glassy sample in readdata format (to be read by read_data command).
	--Other output files include MD trajectories which are not included in this repository.

[constant-K-tension-test] Constant K simulation for subcritical crack growth of a glassy sample. This particular script is for T=0.12 (210 Kelvin), and K=19 (0.38 MPa*sqrt(m)).
	--in.notch: LAMMPS script for constant-K MD runs
	--log.lammps: Log file during constant-K MD runs
	--glass.readdata: Glassy sample made in the previous step, which will be duplicated and a precrack will be created.
	--cracklength.dat: 2nd column is timestep, 3rd coumn is 2c, 4th is instantaneous K, 5th is instantaneous strainrate and 6th is Ly (system size in Y-direction).
	--Other output files include MD trajectories which are not included in this repository.

[Unit conversion]
	1 RU velocity is 540 m/s.
	1 RU K is 0.02 MPa*Sqrt(m)
	1 RU length 0.27 nm
	1 RU energy 0.151 eV
	1 RU time 0.5 ps
	1 RU pressure 1.23 Gpa
	1 RU Temperature 1752 Kelvin

