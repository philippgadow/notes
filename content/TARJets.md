## Service work for TAR jet calibration

Expert contact: Jason Veatch (jveatch@cern.ch)
TWiki: https://twiki.cern.ch/twiki/bin/view/AtlasProtected/JetSubstructureAndTagging

egroup: atlas-cp-jet-track-assisted-jss

Running document: https://docs.google.com/document/d/1pwgHTAjMLLUG_IdQqbmCnyURP-wFJoUZSqgUuQJJNsY/edit#heading=h.9wtejacb1hjd
### General info

3 algorithms:

- TAS
- TAR
- SAT

TAS is not too well performing, so it is not followed any longer.
TAR jet ingredients can be added easily to the derivations, SAT ingredients are not so trivial.
Therefore focus on TAR for the moment.

Uncertainties for tracks and LCTopo jets are avaliable and can be piped through as bottom-up uncertainties
Two uncertainties for LCTopo jets are not ready yet, Lars Henkelmann is checking those.

In the end maybe the uncertainties can be parameterised, right now analysis should use bottom-up uncertainties.
Vary the uncertainties on the basic objects and re-build TAR jets to get the uncertainties on TAR jets.


Typical guinea pig: W' samples (boosted W decays), check impact on modeling uncertainties and bottom-up uncertainties
perhaps also for top jets.
Check impact of uncertainties on key observables, such as TAR jet pt and others.

Slides with release 20.7: https://indico.cern.ch/event/719977/contributions/2972488/attachments/1639349/2617046/tas_2018_04_25.pdf

End goal: as a function of jet pt and eta fractional uncertainty on JES, JMS, substructure shape moments comparing conventional large-R jets and TAR jets


How to check the modeling uncertainty?
Check with different samples (with the nominal) and check the differences between e.g. Herwig and Pythia and check envelope between different generators and theory settings

Bottom up uncertainties are evaluated with a nominal sample, then the modeling uncertainty is added to that in quadrature.

Are there uncertainties for LCTopo02 jets? Jason will check with Jona, until then a proxy (EMTopo04) is used.
Uncertainties are evaluated by using the RScan method (use 0.4 to get 0.2 uncertainties)

I will get the sample list from Jason and will get his release 20.7 code.

Suggested derivation JETM8, not to have any bias from triggers. Check if the AntiKt02LCTopo jets are in the JETM8 derivation.
This derivation has no trigger requirement and is just used for MC.
Also no thinning will be applied (in contrast to EXOT27).

### TAR jet bottom-up uncertainties

Task description:

Code: https://gitlab.cern.ch/jveatch/HWWTagAnalysis/


W' samples:
```
user.jveatch.301255.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m600.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301256.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m800.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301257.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m1000.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301259.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m1200.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301262.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m1500.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301264.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m1700.DAOD_JETM8.R2.FullSim.2017.06.02.v03_EXT0
user.jveatch.301267.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m2000.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301272.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m2500.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301277.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m3000.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301280.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m3600.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301282.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m4000.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301285.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m4600.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
user.jveatch.301287.Pythia8EvtGen_A14NNPDF23LO_Wprime_WZqqqq_m5000.DAOD_JETM8.R2.FullSim.2017.06.02.v02_EXT0
```

New DxAOD request: https://its.cern.ch/jira/browse/ATLJETMET-1103
New DxAOD production task: https://prodtask-dev.cern.ch/prodtask/inputlist_with_request/23011/
