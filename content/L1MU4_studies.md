 ## L1MU4 trigger efficency studies

### Introduction
For the 2017 LHC run a high trigger rate is expected. Therefore the trigger lookup-tables have to be updated to decrease the trigger rate by making the triggers more selective.

The L1MU4 muon trigger should be improved by updating the TGC lookup tables in the end-caps.

For this study, the tag and probe method is used, which is explained below.

The code used to produce these plots can be accessed here: https://gitlab.cern.ch/pgadow/L1MU4Optimization

### Tag and Probe method for efficiency measurements
In order to test the trigger without bias, the tag and probe method is used.
A well-known resonance, such as the $J/\psi$ resonance ($3.0969\,\text{GeV}$) can be used, which decays into $\mu^{+}\mu^{-}$ with branching ratio of ca. $6 \%$. By triggering on one muon of the two-pronged decay, which is called the tag muon, the other muon, which is called the probe muon, can be used to measure the trigger efficiency. This is achieved by trying to match trigger objects to the probe muon.

A L1 trigger object is said to match the probe muon if $\Delta R(\text{probe}, \text{L1 trigger object}) < 0.3$.

In this study, only L1 RoIs originating from TGC chambers are considered. Therefore the probe muon is required to satisfy the condition $1.05 < |\eta^{\text{probe}}| < 2.4$.

The efficiency is defined as 
$$ \text{efficiency} = \frac{\text{number of probes that match the trigger}}{\text{total number of selected probes}}$$

### Event selection
Events have been selected for the tag and probe method, which meet the following requirements:

* Positive single muon trigger decision (using the triggers listed below)
* Event contains exactly 2 muons
* Tag muon is either combined or segment-tagged muon with $p_{\text{T}} > 4\,\text{GeV}$ and $|\eta| < 2.4$, which could be matched to the HLT trigger object.
* Tag and probe muon have opposite charge
* Probe muon is either combined or segment tagged muon with $1.05 < |\eta| < 2.4$
* Invariant mass of dimuon system is $2.8 < m_{\mu\mu} < 3.34$
* For improving the separation between tag and probe muon it is required that the distance between those satisfies 0.1 < $\Delta R$ (tag, probe) < 2.5


##### Trigger list
For selecting events for the tag and probe study, the following set of triggers was used:

* HLT_mu4
* HLT_mu6
* HLT_mu8
* HLT_mu10
* HLT_mu18
* HLT_mu6_idperf
* HLT_mu14
* HLT_mu20_iloose_L1MU15
* HLT_mu20_ivarloose_L1MU15
* HLT_mu24_iloose_L1MU15
* HLT_mu24_imedium
* HLT_mu24_ivarloose_L1MU15
* HLT_mu24_iloose
* HLT_mu24_ivarloose
* HLT_mu24_ivarmedium
* HLT_mu26_imedium
* HLT_mu26_ivarmedium
* HLT_mu28_imedium
* HLT_mu28_ivarmedium
* HLT_mu18_mu8noL1
* HLT_mu20_mu8noL1
* HLT_mu22_mu8noL1
* HLT_mu24_mu8noL1
* HLT_mu26_mu8noL1
* HLT_mu4_bJpsi_Trkloose
* HLT_mu6_bJpsi_Trkloose
* HLT_mu10_bJpsi_Trkloose
* HLT_mu18_bJpsi_Trkloose
* HLT_mu20_2mu0noL1_JpsimumuFS
* HLT_mu18_2mu0noL1_JpsimumuFS

### Distribution of dimuon invariant mass after event selection

![Dimuon invariant mass J/psi peak](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_m_mumu_jpsi.png)

### Distributions of tag muon after event selection

#### $p_{\text{T}}^{\text{tag}}$ distribution

![Tag muon pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_tag_pt.png)

#### $\eta^{\text{tag}}$ distribution

![Tag muon eta](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_tag_eta.png)

#### $\phi^{\text{tag}}$ distribution

![Tag muon phi](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_tag_phi.png)

#### Muon type distribution

![Tag muon type](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_tag_type_Log.png)

#### $\Delta R(\text{tag}, \text{HLT object})$ distribution

![Tag muon type](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_tag_dR.png)


### Distributions of probe muon after event selection

#### $p_{\text{T}}^{\text{probe}}$ distribution

![Probe muon pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_probe_pt.png)

#### $\eta^{\text{probe}}$ distribution

![Probe muon eta](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_probe_eta.png)

#### $\phi^{\text{probe}}$ distribution

![Probe muon phi](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_probe_phi.png)

#### Muon type distribution

![Probe muon type](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_probe_type_Log.png)

#### $\text{min}\, \Delta R(\text{probe}, \text{L1 RoI})$ distribution

![Probe muon type](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_probe_dR.png)

### Efficiency measurement

These distributions show the turn-on curves of the L1MU4 trigger without any optimisation on the look-up tables.

![Efficiency measurement vs pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/efficiency_pt.png)

#### Efficiency measurement for $\mu^{+}$

![Efficiency measurement vs pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/efficiency_pt_charge_positive.png)

#### Efficiency measurement for $\mu^{-}$

![Efficiency measurement vs pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/efficiency_pt_charge_negative.png)

### Rate measurement
The rate of L1 Regions of Interest (trigger objects), which originate from a TGC trigger chamber is shown in dependency of $\eta$. No optimisation on the TGC look-up-tables is yet performed.

Three distributions are overlayed:

* all L1 RoIs (white) 
* L1 RoIs, which could be matched to a probe muon within $\Delta R < 0.3$ (blue)
* L1 RoIs, which could be matched to a probe muon within $\Delta R < 0.3$ with $p_{\text{T}} > 4 \, \text{GeV}$ (green)

![Rate measurement vs eta](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/rate_eta.png)


### Study for $p_{\text{T}}^{\text{probe}}$-dependent $\Delta R$-matching

Because of the deflection in the magnetic field between the Big Wheel and the Outer Wheel the $\Delta R$-matching with a fixed value might not be sufficient.
For developing an intuition about possible cuts, the correlation between $p_{\text{T}}^{\text{probe}}$ and $\Delta R (\text{L1 RoI}, \text{probe})$ is shown below.

![dR(probe, L1 RoI) vs probe pt](http://pgadow.web.cern.ch/pgadow/notes/content/L1MU4_studies-plots/h_dR_vs_pt.png)

A possible way to set the cut could be to define thresholds for $\Delta R$ based on $p_{\text{T}}^{\text{probe}}$ regions, e.g. like this:

* $p_{\text{T}}^{\text{probe}} < 6 \, \text{GeV}$: $\Delta R < 0.3$
* $p_{\text{T}}^{\text{probe}} < 8 \, \text{GeV}$: $\Delta R < 0.2$
* $p_{\text{T}}^{\text{probe}} < 10 \, \text{GeV}$: $\Delta R < 0.15$
* $p_{\text{T}}^{\text{probe}} > 10 \, \text{GeV}$: $\Delta R < 0.1$

Of course this definition is only proposed by estimating the distribution by eye and not by quantitative means. A more quantitative estimation is possible by fitting a function in the distribution shown above.


### Next steps

1. Implement the hardware emulation of the TGC coincidence (already present in Junpei Maeda's code?)
2. Implement an interface to read and write look-up tables (already present in Junpei Maeda's code?)
3. Test different look-up table definitions and evaluate efficiency and rate.
4. Provide efficiency plots also for eta and phi