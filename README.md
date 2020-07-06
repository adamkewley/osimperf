# osimperf

Script(s) for measuring OpenSim 4's performance

The `osimperf` top-level script contains the steps I use to measure
OpenSim's performance in Linux. The script runs `valgrind` and `perf`
under the cover, so you'll need those (or an api-compatible wrapper
script).


## Exaple Usage

```bash
# system dependencies
sudo apt-get install python3 valgrind linux-tools

# ensure `opensim-cmd` is on your PATH

# list all test cases
./osimperf ls

# measure general top-level stats for a test case
./osimperf stat ToyDropLanding

# record performance with perf + valgrind and write the 
# performance measurements to out/
./osimperf record -o out/ ToyDropLanding
```


## Model Sources

Sources for some models:

- Tutorials [here](https://simtk-confluence.stanford.edu/display/OpenSim/Examples+and+Tutorials)

- opensim-models [here](https://github.com/opensim-org/opensim-models)

- IK sim [here](https://simtk-confluence.stanford.edu/display/OpenSim/Tutorial+3+-+Scaling%2C+Inverse+Kinematics%2C+and+Inverse+Dynamics)

- ToyDroplanding [here](https://simtk-confluence.stanford.edu/display/OpenSim/Simulation-Based+Design+to+Prevent+Ankle+Injuries)
  
- Direct from researchers (e.g. Ajay Seth)
