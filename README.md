# Neutrino Direction Regression using CNN

This project focuses on the regression of neutrino directions using Convolutional Neural Networks (CNN). The task involves treating each neutrino class separately to determine if different neutrinos exhibit the same or different directions.

## Meaning of Parameters

### Reconstructed Parameters
- **jmuon_E**: Particle energy reconstructed using the Jmuon algorithm.
- **jmuon_JENERGY_ENERGY**: Reconstructed particle energy.
- **jmuon_JENERGY_CHI2**: Chi-squared value from the reconstructed energy fit.
- **jmuon_JENERGY_NDF**: Number of degrees of freedom from the reconstructed energy fit.
- **jmuon_t**: Time.
- **jmuon_likelihood**: Likelihood of the track reconstruction fit.
- **jmuon_pos_x, jmuon_pos_y, jmuon_pos_z**: Particle position coordinates (x, y, z).
- **jmuon_dir_x, jmuon_dir_y, jmuon_dir_z**: Particle direction coordinates (x, y, z).
- **jmuon_JSHOWERFIT_ENERGY**: Shower energy.
- **jmuon_JGANDALF_CHI2**: Chi-squared value from the energy reconstruction fit using the JGandalf toolkit.
- **jmuon_JGANDALF_BETA0_RAD, jmuon_JGANDALF_BETA1_RAD**: Parameters from the fit.
- **jmuon_JGANDALF_NUMBER_OF_HITS**: Number of hits from which the particle track is reconstructed.
- **jmuon_AASHOWERFIT_ENERGY**: Shower energy from the AANET toolkit.

### True (Generated) Variables
These variables are needed to estimate the efficiency of regressions:
- **energy**: True particle energy.
- **dir_x, dir_y, dir_z**: True particle direction coordinates (x, y, z).

## Task
### Neutrino Direction Regression using CNN

1. **Objective**:
   - Treat each neutrino class separately to evaluate whether different neutrinos have the same or different directions.
   
2. **Neutrino Classes**:
   - There are eight neutrino classes:
     - `atm_neutrino_classA.h5`
     - `atm_neutrino_classB.h5`
     - `atm_neutrino_classC.h5`
     - `atm_neutrino_classD.h5`
     - `atm_neutrino_classE.h5`
     - `atm_neutrino_classF.h5`
     - `atm_neutrino_classG.h5`
     - `atm_neutrino_classH.h5`

3. **Model Training**:
   - Train the model with the following parameters:
     ```python
     (reco_dir_x, reco_dir_y, reco_dir_z) = f(jmuon_dir_x, jmuon_dir_y, jmuon_dir_z, jmuon_likelihood)
     ```
   
4. **Prediction Comparison**:
   - Compare the predicted direction with the true value:
     ```python
     true_direction = f(dir_x, dir_y, dir_z)
     ```

5. **File Reading**:
   - To read the HDF5 files, use the following Python code:
     ```python
     import pandas as pd
     df = pd.read_hdf("file.h5", "y")
     ```

## Getting Started

### Prerequisites
- Python 3.x
- Required libraries: `pandas`, `numpy`, `matplotlib`, `tensorflow` (or `keras`)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/xShadeen/ML_Project.git
