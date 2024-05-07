## Large-R jet systematics contained in the CxAODs (v28)

These systematics (as up/down variation histograms) are stored in the CxAODs of the Mono-V (2015+2016) analysis.

Please note that no `FATJET_Weak_JET_Rtrk_*` histograms are included.


```
// general large-R jet NP  
FATJET_JER__1up
FATJET_JMR__1up
FATJET_D2R__1up


// in addition choose one set of NP: either weak or medium

// weakly correlated scheme of large-R jet NP
FATJET_Weak_JET_Comb_Baseline_mass__1down
FATJET_Weak_JET_Comb_Baseline_mass__1up
FATJET_Weak_JET_Comb_Modelling_mass__1down
FATJET_Weak_JET_Comb_Modelling_mass__1up
FATJET_Weak_JET_Comb_TotalStat_mass__1down
FATJET_Weak_JET_Comb_TotalStat_mass__1up
FATJET_Weak_JET_Comb_Tracking_mass__1down
FATJET_Weak_JET_Comb_Tracking_mass__1up

FATJET_Weak_JET_Rtrk_Baseline_D2Beta1__1down
FATJET_Weak_JET_Rtrk_Baseline_D2Beta1__1up
FATJET_Weak_JET_Rtrk_Modelling_D2Beta1__1down
FATJET_Weak_JET_Rtrk_Modelling_D2Beta1__1up
FATJET_Weak_JET_Rtrk_TotalStat_D2Beta1__1down
FATJET_Weak_JET_Rtrk_TotalStat_D2Beta1__1up
FATJET_Weak_JET_Rtrk_Tracking_D2Beta1__1down
FATJET_Weak_JET_Rtrk_Tracking_D2Beta1__1up

FATJET_Weak_JET_Rtrk_Modelling_pT__1down 
FATJET_Weak_JET_Rtrk_Modelling_pT__1up
FATJET_Weak_JET_Rtrk_Baseline_pT__1down
FATJET_Weak_JET_Rtrk_Baseline_pT__1up
FATJET_Weak_JET_Rtrk_TotalStat_pT__1down
FATJET_Weak_JET_Rtrk_TotalStat_pT__1up
FATJET_Weak_JET_Rtrk_Tracking_pT__1down
FATJET_Weak_JET_Rtrk_Tracking_pT__1up


// medium correlated set of large-R jet NP
FATJET_Medium_JET_Comb_Baseline_Kin__1down
FATJET_Medium_JET_Comb_Baseline_Kin__1up
FATJET_Medium_JET_Comb_Modelling_Kin__1down
FATJET_Medium_JET_Comb_Modelling_Kin__1up
FATJET_Medium_JET_Comb_TotalStat_Kin__1down
FATJET_Medium_JET_Comb_TotalStat_Kin__1up
FATJET_Medium_JET_Comb_Tracking_Kin__1down
FATJET_Medium_JET_Comb_Tracking_Kin__1up
```


## Change in conditional background-only fit with all regions

Including the missing large-R jet combined mass uncertainties does not change the fit result much.

#### Without including large-R jet comb mass NP:
<a href="https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/pulls_nocombmassNP.png">
<img src="https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/pulls_nocombmassNP.png" width="500" alt="pull plot without comb mass NP">
</a>

[Text file fit result without large-R jet comb mass NP](https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/GlobalFit_fitres_conditionnal_mu0-nocombmassNP.txt)

#### With including large-R jet comb mass NP:
<a href="https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/pulls_withcombmassNP.png">
<img src="https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/pulls_withcombmassNP.png" width="500" alt="pull plot with comb mass NP">
</a>
[Text file fit result with large-R jet comb mass NP](https://pgadow.web.cern.ch/pgadow/notes/content/2017-11-14-largeRjetuncertainties/GlobalFit_fitres_conditionnal_mu0-withcombmassNP.txt)
