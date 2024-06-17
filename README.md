Meaning of parameters:

    jmuon_E - particle energy reconstructed using Jmuon algoritm

    jmuon_JENERGY_ENERGY - reconstructed particle energy

    jmuon_JENERGY_CHI2 - chi2 from reconstructed energy fit
    
    jmuon_JENERGY_NDF - number of degrees of freedom from reconstructed energy fit

    jmuon_t - time

    jmuon_likelihood - likelihood of track reconstruction fit

    jmuon_pos_x, jmuon_pos_y, jmuon_pos_z - particle position, coordinates x, y, z

    jmuon_dir_x, jmuon_dir_y, jmuon_dir_z - particle direction, coordinates x, y, z

    jmuon_JSHOWERFIT_ENERGY - shower energy

    jmuon_JGANDALF_CHI2 - chi2 from energy reconstruction fit using JGandalf toolkit

    jmuon_JGANDALF_BETA0_RAD, jmuon_JGANDALF_BETA1_RAD - parameters from fit

    jmuon_JGANDALF_NUMBER_OF_HITS - number of hits from which particle track is reconstructed

    jmuon_AASHOWERFIT_ENERGY - shower energy from AANET toolkit



True (genereted) variables needed to estimate efficiency of regressions:

    energy  - true particle energy

    dir_x, dir_y, dir_z - true particle direction, coordinates x, y, z

#TASK
Neutrino direction regression using CNN

    Treat each neutrino class separately. It allows to check whether different neutrinos
    have the same or different direction.

    There are eight neutrino classes: 
             atm_neutrino_classA.h5  atm_neutrino_classE.h5
             atm_neutrino_classB.h5  atm_neutrino_classF.h5
             atm_neutrino_classC.h5  atm_neutrino_classG.h5
             atm_neutrino_classD.h5  atm_neutrino_classH.h5

    Train the model with parameters:
             (reco_dir_x, reco_dir_y, reco_dir_z) = f(jmuon_dir_x, jmuon_dir_y, jmuon_dir_z, jmuon_likelihood)

    Predicted direction can be compared with true value:  true_direction = f(dir_x, dir_y, dir_z)

    To read file:  import pandas as pd
                   df = pd.read_hdf("file.h5", "y")
