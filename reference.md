# Reconstruction from pulse shape software
## https://github.com/CaltechPrecisionTiming/TimingDAQ

#### core code for waveform analysis https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/master/src/DatAnalyzer.cc

calculation of the baseline/pedestal: https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/0bb5c289ce52b3b5f9db7d312595f2904053e268/src/DatAnalyzer.cc#L84-L119 

calculatet the charge or (V*s) of pulse:

https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/0bb5c289ce52b3b5f9db7d312595f2904053e268/src/DatAnalyzer.cc#L1191-L1201

command to reconstruct the pulse:

./NetScopeStandaloneDat2Root --input_file=xxx.root --config=config/KeySightScope_v1_test.config --N_evts=4000


add the following to confi/KeySightScope_v1_test.config

ConstantFraction 2 3 4 5 6 7 8 10 20 30 40 50 60
ConstantThreshold -10
z_DUT -50. 50. 1500.
# CH (#) | POLARITY (+/-) | Baseline start time | Baseline stop time | AMPLIFICATION (dB) | ATTENUATION (dB) | ALGORITHM (None, Re, G) | WEIERSTRASS FILTER_WIDTH (0 for no filter)
0 - -1e-6 0. 0. 0. LP2  0.
1 - -1e-6 0. 0. 0. LP2  0.
2 - -1e-6 0. 0. 0. LP2  0.
3 - -1e-6 0. 0. 0. LP2  0.


# Talks on LO measurement with module/single channel

## CERN measurement

https://indico.cern.ch/event/1021736/contributions/4291361/attachments/2215107/3749856/BTL%20bars%20absolute%20light%20output%20measurements%20with%20SiPMs.pdf

## LO measurement with single LYSO tiles

Dawn Tang SURF 2018: https://indico.cern.ch/event/744397/

# Data

Taken by Lautaro in June:

/storage/af/user/nlu/MTD/FQNET-Agilent-Scope/datatest/module2021/*root

pulse->Draw("channel[0]:time[0]","i_evt==3")
