## Checks of cutflows with different versions of the XAMPPmonoS code

I checked the resolved signal region cutflow using 1000 events of the `mc16_13TeV.310774.MadGraphPy8EG_A14NNP23LO_monoSww_all_zp2500_dm200_dh160.deriv.DAOD_EXOT27.e7040_s3126_r9364_p3758` sample.


### Master branch
The resolved cutflow is checked for the `master` branch, commit hash `9ede50c4cee017bd8a936c7a5a0fea3770398bda`.

The master branch uses a veto on baseline leptons and signal leptons.

The lepton veton in MonoSAnalysisConfig is implemented as
```
// lepton veto
        Cut* BaselineElectronVeto = NewCut("0 baseline electrons", Cut::CutType::CutInt, m_skimEvents);
        if (!BaselineElectronVeto->initialize("N_BaselineElectrons", "==0")) return StatusCode::FAILURE;
        Cut* SignalElectronVeto = NewCut("0 signal electrons", Cut::CutType::CutInt, m_skimEvents);
        if (!SignalElectronVeto->initialize("N_SignalElectrons", "==0")) return StatusCode::FAILURE;
        SRResolvedCutFlow.push_back(SignalElectronVeto->combine(BaselineElectronVeto, Cut::Combine::AND));

        Cut* BaselineMuonVeto = NewCut("0 baseline muons", Cut::CutType::CutInt, m_skimEvents);
        if (!BaselineMuonVeto->initialize("N_BaselineMuons", "==0")) return StatusCode::FAILURE;
        Cut* SignalMuonVeto = NewCut("0 signal muons", Cut::CutType::CutInt, m_skimEvents);
        if (!SignalMuonVeto->initialize("N_SignalMuons", "==0")) return StatusCode::FAILURE;
        SRResolvedCutFlow.push_back(SignalMuonVeto->combine(BaselineMuonVeto, Cut::Combine::AND));
```


The SUSYTools config file is
```
##################################################
# SUSYTools configuration file
##################################################
#
#EleBaseline.Pt: defined in job option
#EleBaseline.Eta: defined in job option
#EleBaseline.Id: defined in job option
#EleBaseline.CrackVeto: defined in job option
#EleBaseline.z0: defined in job option
#
#Ele.Pt: defined in job option
#Ele.Eta: defined in job option
#Ele.Id: defined in job option
#Ele.CrackVeto: defined in job option
#Ele.Iso: defined in job option
#Ele.z0: defined in job option
#Ele.d0sig: defined in job option
Ele.IsoHighPt: FCHighPtCaloOnly # tight iso required for electrons pt > 200 GeV
Ele.CFT: None # ChargeIDSelector WP
# 
#MuonBaseline.Pt: defined in job option
#MuonBaseline.Eta: defined in job option
#MuonBaseline.Id: defined in job option
#MuonBaseline.z0: defined in job option
#
#Muon.Pt: defined in job option
#Muon.Eta: defined in job option
#Muon.Id: defined in job option
#Muon.z0: defined in job option
#Muon.d0sig: defined in job option
#Muon.Iso: defined in job option
#
MuonCosmic.z0: 1.
MuonCosmic.d0: 0.2
#
BadMuon.qoverp: 0.4
```


The settings in the run option are 

```
######################
# Electron Selection #
######################
# we have 3 stages, preselection, baseline and signal.
# PreSelectionDecorator = "signal", we apply already the signal decorators to the preselection object
SetupSUSYElectronSelector().PreSelectionDecorator = "signal"
SetupSUSYElectronSelector().ApplyTriggerSF = False
SetupSUSYElectronSelector().RequireIsoPreSelection = True
SetupSUSYElectronSelector().RequireIsoBaseline = True

SetupSUSYTools().EleBaselinePt = 7000.
SetupSUSYTools().EleBaselineEta = 2.47
SetupSUSYTools().EleBaselineId = "LooseAndBLayerLLH"
SetupSUSYTools().EleBaselineCrackVeto = False
SetupSUSYTools().EleBaselineD0sig = 5.
SetupSUSYTools().EleBaselineZ0 = 0.5

SetupSUSYTools().ElePt = 7000.
SetupSUSYTools().EleEta = 2.47
SetupSUSYTools().EleId = "LooseAndBLayerLLH"
SetupSUSYTools().EleIso = "FCLoose"
SetupSUSYTools().EleCrackVeto = False
SetupSUSYTools().EleD0sig = 5.
SetupSUSYTools().EleZ0 = 0.5

##################
# Muon Selection #
##################
# we have 3 stages, preselection, baseline and signal.
# PreSelectionDecorator = "signal", we apply already the signal decorators to the preselection object
SetupSUSYMuonSelector().PreSelectionDecorator = "signal"
SetupSUSYMuonSelector().ApplyTriggerSF = False
SetupSUSYMuonSelector().RequireIsoPreSelection = True
SetupSUSYMuonSelector().RequireIsoBaseline = True

SetupSUSYTools().MuonBaselinePt = 7000.
SetupSUSYTools().MuonBaselineEta = 2.7
SetupSUSYTools().MuonBaselineId = 2  # Loose
SetupSUSYTools().MuonBaselineD0sig = 3.
SetupSUSYTools().MuonBaselineZ0 = 0.5

SetupSUSYTools().MuonPt = 7000.
SetupSUSYTools().MuonEta = 2.7
SetupSUSYTools().MuonId = 2  # Loose
SetupSUSYTools().MuonD0sig = 3.
SetupSUSYTools().MuonZ0 = 0.5
SetupSUSYTools().MuonIso = "FCLoose"
```



Resulting cutflow:
```
Printing raw events
CutFlowHisto                                                        DSID_310774_CutFlow
Systematic variation                                                Nominal
#######################################################################################
Cut                                                                 Yields
#######################################################################################
Initial                                                             30000 ± 173.21
PassGRL                                                             30000 ± 173.21
passLArTile                                                         30000 ± 173.21
Trigger                                                             23801 ± 154.28
HasVtx                                                              23801 ± 154.28
BadJet                                                              23799 ± 154.27
CosmicMuon                                                          23794 ± 154.25
BadMuon                                                             23790 ± 154.24
IsMETTrigPassed                                                     22628 ± 150.43
(0 signal electrons && 0 baseline electrons)                        19015 ± 137.89
(0 signal muons && 0 baseline muons)                                16405 ± 128.08
MetTST>150                                                          14524 ± 120.52
>=2 jets                                                            14112 ± 118.79
MetTST<=500                                                         10620 ± 103.05
#######################################################################################
```

### Combined ntuple branch

The cutflow for the combined ntuple branch `theonentuple` is checked using commit hash `8722f132e608f25a08dd85d0ed7595e62621b91c`. Note that this still has the wrong jet definition that is lacking the JVT requirement (as has the master branch). For cutflow comparison this is kept the same.

The lepton veto is implemented in MonoSAnalysisConfig as
```
 // lepton veto
        Cut* BaselineElectronVeto = NewCut("0 baseline electrons", Cut::CutType::CutInt, m_skimEvents);
        if (!BaselineElectronVeto->initialize("N_BaselineElectrons", "==0")) return StatusCode::FAILURE;
        SRResolvedCutFlow.push_back(BaselineElectronVeto);

        Cut* BaselineMuonVeto = NewCut("0 baseline muons", Cut::CutType::CutInt, m_skimEvents);
        if (!BaselineMuonVeto->initialize("N_BaselineMuons", "==0")) return StatusCode::FAILURE;
        SRResolvedCutFlow.push_back(BaselineMuonVeto);
```

The job option lepton settings are:


```
######################
# Electron Selection #
######################
SetupSUSYElectronSelector().ApplyTriggerSF = True
# signal electrons with pt > 200 GeV have a different high pt isolation working
# point which baseline electrons don't have. "PreSelectionDecorator = signal"
# forces already pre-electrons and consecutively also baseline-electrons to
# satisfy the signal electron definition. This allows to make the cutflow
# coherent to the master branch which is based on the mono-h(bb) code. On the
# other hand we maybe don't want for the electrons used for the veto to require
# a very tight working point for high pt electrons. In the SUSYTools config file
# the signal electron Et requirement is lowered for 27 GeV to 7 GeV and a manual
# cut for the 2 lepton region is added in the mono-s analysis helper. Since the
# PreSelectionDecorator forces all electrons to satisfy the signal definition,
# it is futile to write additional SF for baseline electrons.
SetupSUSYElectronSelector().PreSelectionDecorator = "signal"
# SetupSUSYElectronSelector().WriteBaselineSF = True

# the isolation requirements for pre-electrons and baseline-electrons are
# already taken into account by SUSYTools because we defined the isolation
# working points for baseline electrons in the susytools config file
SetupSUSYElectronSelector().RequireIsoPreSelection = False
SetupSUSYElectronSelector().RequireIsoBaseline = False

##################
# Muon Selection #
##################
SetupSUSYMuonSelector().ApplyTriggerSF = True
SetupSUSYMuonSelector().WriteBaselineSF = True

# the isolation requirements for pre-electrons and baseline-electrons are
# already taken into account by SUSYTools because we defined the isolation
# working points for baseline electrons in the susytools config file
SetupSUSYMuonSelector().RequireIsoPreSelection = False
SetupSUSYMuonSelector().RequireIsoBaseline = False
```


The SUSYTools definitions are 

```
##################################################
# SUSYTools configuration file
##################################################
#
EleBaseline.Pt: 7000.
EleBaseline.Eta:  2.47
EleBaseline.Id: LooseAndBLayerLLH
EleBaseline.Iso: FCLoose
EleBaseline.CrackVeto: false
EleBaseline.d0sig: 5.0
EleBaseline.z0: 0.5
#
Ele.Et: 7000. # 27000. - the 27000. MeV requirement is enforced by hand in the monosanalysishelper  # yes, this is not a typo: it is Et, not Pt
Ele.Eta: 2.47
Ele.Id: LooseAndBLayerLLH
Ele.CrackVeto: false
Ele.Iso: FCLoose
Ele.d0sig: 5.0
Ele.z0: 0.5
Ele.IsoHighPt: FCHighPtCaloOnly # tight iso required for electrons pt > 200 GeV
Ele.CFT: None # ChargeIDSelector WP
# 
MuonBaseline.Pt: 7000.
MuonBaseline.Eta: 2.7
MuonBaseline.Id: 2  # Loose
MuonBaseline.Iso: FCLoose
MuonBaseline.d0sig: 3.
MuonBaseline.z0: 0.5
#
Muon.Pt: 25000.
Muon.Eta: 2.5
Muon.Id: 1  # Medium
Muon.Iso: FCTightTrackOnly
Muon.d0sig: 3.
Muon.z0: 0.5
#
MuonCosmic.z0: 1.
MuonCosmic.d0: 0.2
#
BadMuon.qoverp: 0.4
```

To make the 2 lepton control region behave as before, this is added to the XAMPPmonoS::MonSAnalysisHelper:
```
// manual enforcement of the signal electron pt cut of 27 GeV since we
        // had to set the electron signal pt to 7 GeV in order to use the signal
        // electrons also for the electron vetos (signal electrons have a
        // different high pt isolation working point)
        //
        // int NSignalElectrons = SignalElectrons->size();
        int NSignalElectrons = 0;
        for (const auto& ielec : *SignalElectrons) {
            if (ielec->pt() > 27000.) NSignalElectrons++;
        }
```

The resulting resolved signal region cutflow is
```
Printing raw events
CutFlowHisto          DSID_310774_CutFlow
Systematic variation  Nominal
#########################################
Cut                   Yields
#########################################
Initial               30000 ± 173.21
PassGRL               30000 ± 173.21
passLArTile           30000 ± 173.21
Trigger               25921 ± 161.00
HasVtx                25921 ± 161.00
BadJet                25919 ± 160.99
CosmicMuon            25914 ± 160.98
BadMuon               25909 ± 160.96
IsMETTrigPassed       22628 ± 150.43
0 baseline electrons  19015 ± 137.89
0 baseline muons      16405 ± 128.08
MetTST>150            14524 ± 120.52
>=2 jets              14112 ± 118.79
MetTST<=500           10620 ± 103.05
```

### Difference between the theonentuple and the master resolved signal region cutflow

The difference between the cutflows is none except in between trigger and inMetTrigPassed cuts :)
The difference in the trigger is expected since there are now also the single muon and single electron triggers in the combined ntuple, but the requirement of the lowest unprescaled MET trigger having fired makes the cutflows align again.


### Todo and thing to follow up

We should think about 

- if we want to rely on the different isolation WP for electrons as it was the case before or use just one loose isolation working point for the loose electron definition (effect on cutflow below % level)
- if we want to keep the bad jet cleaning as it is currently implemented or use the default tool settings in SUSYTools (effect on cutflow)



## Another check with a ttbar sample

This is another check with `mc16_13TeV.410470.PhPy8EG_A14_ttbar_hdamp258p75_nonallhad.deriv.DAOD_EXOT27.e6337_s3126_r10201_p3712/DAOD_EXOT27.16330605._000471.pool.root.1`


Master branch:

```
Printing raw events
CutFlowHisto                                                        DSID_410470_CutFlow
Systematic variation                                                Nominal
#######################################################################################
Cut                                                                 Yields
#######################################################################################
Initial                                                             45499 ± 213.30
PassGRL                                                             45499 ± 213.30
passLArTile                                                         45499 ± 213.30
Trigger                                                             25776 ± 160.55
HasVtx                                                              25776 ± 160.55
BadJet                                                              25773 ± 160.54
CosmicMuon                                                          25766 ± 160.52
BadMuon                                                             25756 ± 160.49
IsMETTrigPassed                                                     19549 ± 139.82
(0 signal electrons && 0 baseline electrons)                        14691 ± 121.21
(0 signal muons && 0 baseline muons)                                6693  ± 81.81
MetTST>150                                                          2950  ± 54.31
>=2 jets                                                            2950  ± 54.31
MetTST<=500                                                         2938  ± 54.20
```

Combined ntuple:

```
Printing raw events
CutFlowHisto          DSID_410470_CutFlow
Systematic variation  Nominal
#########################################
Cut                   Yields
#########################################
Initial               45499 ± 213.30
PassGRL               45499 ± 213.30
passLArTile           45499 ± 213.30
Trigger               41525 ± 203.78
HasVtx                41525 ± 203.78
BadJet                41519 ± 203.76
CosmicMuon            41506 ± 203.73
BadMuon               41492 ± 203.70
IsMETTrigPassed       19549 ± 139.82
0 baseline electrons  14691 ± 121.21
0 baseline muons      6693  ± 81.81
MetTST>150            2950  ± 54.31
>=2 jets              2950  ± 54.31
MetTST<=500           2938  ± 54.20
```





Perfect agreement!


## Check of 1 lepton CR cutflow with ttbar sample


Master branch:

I had to [modify some lines to make the master branch 1 lepton JO compliant with analysis release 21.2.59](https://gitlab.cern.ch/atlas-mpp-xampp/XAMPPmonoS/commit/6c9d016bf970c89cc24aacfc96e640809e3a92b1), since the names of the isolation working points changed in between releases.

```

- SetupSUSYTools().EleIso = "LooseTrackOnly"
+ SetupSUSYTools().EleIso = "FCLoose"

- SetupSUSYTools().MuonIso = "FixedCutTightTrackOnly"
+ SetupSUSYTools().MuonIso = "FCTightTrackOnly"
```

Master branch


resolved cutflow:
```
Initial                                       45499 ± 213.30
PassGRL                                       45499 ± 213.30
passLArTile                                   45499 ± 213.30
Trigger                                       36762 ± 191.73
HasVtx                                        36762 ± 191.73
BadJet                                        36757 ± 191.72
CosmicMuon                                    36743 ± 191.68
BadMuon                                       36729 ± 191.65
IsMETTrigPassed                               19548 ± 139.81
(0 signal electrons && 0 baseline electrons)  14690 ± 121.20
(1 signal muon && 1 loose muon)               6232  ± 78.94
MetTSTmuInvis>150                             3598  ± 59.98
MetTSTmuInvis<=500                            3576  ± 59.80
```

Combined ntuple branch:

resolved cutflow:
```
Initial                             45499 ± 213.30
PassGRL                             45499 ± 213.30
passLArTile                         45499 ± 213.30
Trigger                             41525 ± 203.78
HasVtx                              41525 ± 203.78
BadJet                              41519 ± 203.76
CosmicMuon                          41506 ± 203.73
BadMuon                             41492 ± 203.70
IsMETTrigPassed                     19549 ± 139.82
0 baseline electrons                14691 ± 121.21
(1 signal muon && 1 baseline muon)  6186  ± 78.65
MetTSTmuInvis>150                   3569  ± 59.74
MetTSTmuInvis<=500                  3548  ± 59.57
```


In the one lepton control region there is disagreement at the triggers but the cutflow almost converges again at the IsMETTrigPassed cut.

But then the cutflow diverges again after the muon requirement.

This is due to the different "baseline muon" definition in the 1 lepton control region implementation in the master branch and in the combined ntuple branch.
In the master branch fixed cut tight isolation is required for the signal lepton but (perhaps accidentally or due to mono-h(bb) mimicking the CxAOD framework) also for the baseline lepton.

This has effects both on the bad muon veto and the additional loose muon veto. The region requires 1 baseline muon and 1 signal muon: since the signal muon defintion is a subset of the baseline muon definion, this is the same as exactly 1 signal muon and no additional baseline muons.
Changing the isolation working point of the baseline muon definition has effects both on the bad muon / cosmic muon veto cuts and the muon requirement cut. Also this makes the object definition in the 1 lepton control region different to the signal region.


For diagnostic reasons I did this test: I changed the baseline muon isolation working point definition in the combined ntuple branch to also the tight isolation working point. After that the cutflows matched.