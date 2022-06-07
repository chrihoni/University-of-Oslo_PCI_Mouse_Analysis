

# This repository contains the scripts for analysis of neurophysiological data related to the article ".....(add title and link)......".

Analysis pipeline -The diagram lists the scripts used for analysis and visualisation of the manuscript figures.

![Alt text](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/Mouse_pci_analysis_pipeline_uio.drawio.svg)

### ----Aquisition of raw data----

For recordings, we connected EEG electrodes and a 32 channel silicone probe consisting of 2 shanks with 16 channels each (NeuroNexus, A2x16-10mm-100-500-177-CM32) to two amplifier headstages (RHS Stim/Recording System, INTAN technologies) running on a Windows 10 computer. Acquired signals (both EEG and probe) were amplified in respect to a reference connected to the cerebellum ground screw, sampled at 20-25 kHz and band pass filtered between 0.2-8000 Hz. 

### ----Preprocessing of EEG, LFP data----

EEG data: The notebook [1_Preprocessing_EEG](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/1_Preprocessing_EEG.ipynb) contains functions for preprocessing of EEG data including removal of the stimulation artefact, bandpass filtering (0.5 to 80 Hz), downsampling (from 20-25kHz to 500 Hz), offset removal, and trial rejection of artefacts. The script plots EEG data for visual inspection and saves the retained EEG channels and retained trials as .npy files. 

LFP data: The notebook [2_Preprocessing_LFP](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/2_Preprocessing_LFP.ipynb) describes preprocessing steps similar to the preprocessing of EEG data including removal of the stimulation artefact, bandpass filtering (0.5 to 80 Hz), downsampling (from 20-25kHz to 500 Hz), offset removal, and trial rejection of artefacts. In addition, LFP channels are pairwise referenced between electrodes at the same cortical depth.  
