# Reconstruction from pulse shape software
## https://github.com/CaltechPrecisionTiming/TimingDAQ

### core code for waveform analysis https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/master/src/DatAnalyzer.cc

calculation of the baseline/pedestal: https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/0bb5c289ce52b3b5f9db7d312595f2904053e268/src/DatAnalyzer.cc#L84-L119 

calculatet the charge or (V*s) of pulse:

https://github.com/CaltechPrecisionTiming/TimingDAQ/blob/0bb5c289ce52b3b5f9db7d312595f2904053e268/src/DatAnalyzer.cc#L1191-L1201

### Steps to reconstruct the pulse:

#### method 1

``` 
cp -r /storage/af/user/nlu/work/MTD/TimingDAQ .
source TimingDAQ/setup_lxplus.sh
cd TimingDAQ
make clean
make

./NetScopeStandaloneDat2Root --input_file=/storage/af/user/nlu/MTD/FQNET-Agilent-Scope/datatest/module2021/run_scoperun2.root --config=config/KeySightScope_v1_test.config --N_evts=10 --verbose --output_file=outputpath

note: outputpath is the full directory where you would like to save the output

e.g. --output_file=/storage/af/user/nlu/run_scoperun2_converted.root the output will appear in /storage/af/user/nlu/run_scoperun2_converted.root

```

#### method 2

``` 
git clone https://github.com/CaltechPrecisionTiming/TimingDAQ

source TimingDAQ/setup_lxplus.sh

cd TimingDAQ

cp /storage/af/user/nlu/work/MTD/TimingDAQ/config/KeySightScope_v1_test.config .

make -j8

```

./NetScopeStandaloneDat2Root --input_file=xxx.root --config=config/KeySightScope_v1_test.config --N_evts=4000


# Talks on LO measurement with module/single channel

## CERN measurement

https://indico.cern.ch/event/1021736/contributions/4291361/attachments/2215107/3749856/BTL%20bars%20absolute%20light%20output%20measurements%20with%20SiPMs.pdf

## LO measurement with single LYSO tiles

Dawn Tang SURF 2018: https://indico.cern.ch/event/744397/

# Data

Taken by Lautaro in June:

/storage/af/user/nlu/MTD/FQNET-Agilent-Scope/datatest/module2021/*root

pulse->Draw("channel[0]:time[0]","i_evt==3")
