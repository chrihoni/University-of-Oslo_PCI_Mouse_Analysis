

# Overview 
This repository contains the scripts for analysis of neurophysiological data related to the measurement of the perturbational complexity index in rodents (the repository is continously updated and remaining scripts will be added soon).

Analysis pipeline -The diagram lists the workflow used for analysis and visualisation of the manuscript figures.

![Alt text](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/Mouse_pci_analysis_pipeline_uio.drawio.svg)


### ----Aquisition of raw data----

For recordings, we connected EEG electrodes and a 32 channel silicone probe consisting of 2 shanks with 16 channels each (NeuroNexus, A2x16-10mm-100-500-177-CM32) to two amplifier headstages (RHS Stim/Recording System, INTAN technologies) running on a Windows 10 computer. Acquired signals (both EEG and probe) were amplified in respect to a reference connected to the cerebellum ground screw, sampled at 20-25 kHz and band pass filtered between 0.2-8000 Hz. 


### ----Preprocessing of EEG, LFP data----

EEG data: The notebook [1_Preprocessing_EEG](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/1_Preprocessing_EEG.ipynb) contains functions for preprocessing of EEG data including removal of the stimulation artefact, bandpass filtering (0.5 to 80 Hz), downsampling (from 20-25kHz to 500 Hz), offset removal, and trial rejection of artefacts. The script plots EEG data for visual inspection and saves the retained EEG channels and retained trials as .npy files. 

LFP data: The notebook [2_Preprocessing_LFP](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/2_Preprocessing_LFP.ipynb) contains functions for preprocessing of LFP data, including pairwise referencing between electrodes at the same cortical depth, removal of the stimulation artefact, bandpass filtering (0.5 to 80 Hz), downsampling (from 20-25kHz to 500 Hz), offset removal, and trial rejection of artefacts. 


### ----Power and phase of EEG and LFP----

The notebook [3_fig2_plot_erp_traces](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/3_fig2_plot_erp_traces.ipynb) plots EEG and LFP example traces on top of each other (Figure 2).  

The notebook [4_fig2_eeg_lfp_power_phase_locking_heatmaps](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/4_fig2_eeg_lfp_power_phase_locking_heatmaps.ipynb) extracts power and phase of preprocessed EEG data (returned by 1_Preprocessing_EEG) using Wavelet convolution. The returned function values are saved to a pandas dataframe for further analysis (repeated for each mouse). The ERP, power and itpc phase-locking values are plotted for each frequency and channel (left plot, top-bottom) and for a certain frequency band across channels (right plot, top-bottom). The latter (right side) plot is shown in Fig. 2.

The notebook [5_fig2_itpc_eeg_lfp_layer_summary](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/5_fig2_itpc_eeg_lfp_layer_summary.ipynb) plots itpc drop time of eeg and lfp data (phase-locking values saved to pandas dataframe returned by notebook 4) and performs hypothesis tests . 

The notebook [6_fig3_pci_eeg_lfp](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/6_fig3_pci.ipynb) calculates the timecourse of Pci_st values derived from EEG and LFP data and appends the results to a dataframe.

The notebook [7_fig3_plot_pci_summary](https://github.com/chrihoni/University-of-Oslo_PCI_Mouse_Analysis/blob/main/7_fig3_plot_pci_summary.ipynb) plots the timecourse of PCIst values derived from EEG and LFP data and performs hypothesis tests.
