
## Acceptance study for mono-V samples
In this document the acceptance ratio for DmSimp NLO samples vs dmV LO samples is studied for a vector mediator model with gQ = 0.25, gL = 0.0 and gDM = 1.0.

The acceptance is studied on truth level.

In the plots the acceptance ratio is shown, which is defined as 

$$\frac{\text{acceptance of NLO samples}}{\text{acceptance of LO samples}}$$


<pre><code class="python">
import numpy as np
import seaborn as sns
import pandas as pd
import matplotlib.pyplot as plt
</code></pre>


<pre><code class="python">
%matplotlib inline
</code></pre>


<pre><code class="python">
sns.set(style="ticks")
sns.set_palette("husl")

acceptance_full = pd.read_csv('acceptance.csv')

acceptance_monoZ = acceptance_full.query('Model == "Zhad"')
acceptance_monoW = acceptance_full.query('Model == "Whad"')

acceptance = acceptance_monoZ.pivot("Dark Matter mass [GeV]", "Mediator mass [GeV]", "Acceptance (NLO) / Acceptance (LO)")

# Draw a heatmap with the numeric values in each cell
sns.heatmap(acceptance, annot=True, linewidths=.5, fmt='.3g').invert_yaxis()
</code></pre>


![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/output_3_0.png)


<pre><code class="python">

acceptance = acceptance_monoW.pivot("Dark Matter mass [GeV]", "Mediator mass [GeV]", "Acceptance (NLO) / Acceptance (LO)")

# Draw a heatmap with the numeric values in each cell
sns.heatmap(acceptance, annot=True, linewidths=.5, fmt='.3g').invert_yaxis()
</code></pre>


![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/output_4_0.png)

### MET and pT(W,Z) distributions

Why is the acceptance higher for the NLO samples? The most stringent cut in the event selection is the MET cut. Since the NLO MET distributions are consistently harder than the LO distributions, we expect more signal events passing the event selection.

#### Distributions for Whad DM 1 MM 300
![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/TRUTH_met_Whad_DM_1_MM_300.png)
![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/TRUTH_ptv_Whad_DM_1_MM_300.png)

#### Distributions for Zhad DM 1 MM 300
![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/TRUTH_met_Zhad_DM_1_MM_300.png)
![png](http://pgadow.web.cern.ch/pgadow/notes/content/monoVacceptance-plots/TRUTH_ptv_Zhad_DM_1_MM_300.png)

### Raw values for the acceptance

| Model | Dark Matter mass [GeV] | Mediator mass [GeV] | Acceptance (LO) | errorAcceptanceLO | Acceptance (NLO) | errorAcceptanceNLO | Acceptance (NLO) / Acceptance (LO) | errorRatio      | 
|-------|------------------------|---------------------|-----------------|-------------------|------------------|--------------------|------------------------------------|-----------------| 
| Zhad  | 1                      | 100                 | 0.0043          | 0.000220962207472 | 0.00479          | 0.00010465155739   | 1.11395348837                      | 0.0784974825325 | 
| Zhad  | 1                      | 300                 | 0.02002         | 0.000510745945181 | 0.022564         | 0.000244343833834  | 1.12707292707                      | 0.039267695564  | 
| Zhad  | 1                      | 2000                | 0.105154206168  | 0.00135800120692  | 0.11219185343    | 0.000632376947846  | 1.06692692112                      | 0.0193306694134 | 
| Zhad  | 10                     | 10                  | 0.00156         | 0.000129833113118 | 0.00184          | 6.32651565072e-05  | 1.17948717949                      | 0.131059970594  | 
| Zhad  | 10                     | 100                 | 0.00412         | 0.000216006415262 | 0.00489400978802 | 0.000105855701455  | 1.1878664534                       | 0.0829487504664 | 
| Zhad  | 10                     | 10000               | 0.0821673950656 | 0.001166350932    | 0.0899346551645  | 0.000551317229667  | 1.09452971088                      | 0.0215387626512 | 
| Zhad  | 50                     | 10                  | 0.0112          | 0.000370081520408 | 0.0131900263801  | 0.000181073068374  | 1.17768092679                      | 0.0520828410167 | 
| Zhad  | 50                     | 95                  | 0.00617         | 0.000267906100131 | 0.00727          | 0.000130863254958  | 1.17828200972                      | 0.0684116562694 | 
| Zhad  | 50                     | 300                 | 0.0197          | 0.000506143690329 | 0.022814         | 0.000245870984198  | 1.15807106599                      | 0.0401461808678 | 
| Zhad  | 150                    | 10                  | 0.03635         | 0.000717858404746 | 0.0401983215866  | 0.000340393391354  | 1.10586854433                      | 0.0301042296821 | 
| Zhad  | 150                    | 295                 | 0.02323         | 0.000555434813137 | 0.0271720543441  | 0.000271545588308  | 1.16969670013                      | 0.0375833315419 | 
| Zhad  | 150                    | 1000                | 0.07196         | 0.00152148152368  | 0.076684920219   | 0.000500076471413  | 1.06566036991                      | 0.0285490995163 | 
| Zhad  | 500                    | 10                  | 0.087765265916  | 0.00171742908486  | 0.0957930653781  | 0.000573186553027  | 1.09146898125                      | 0.0266967165598 | 
| Zhad  | 500                    | 995                 | 0.07534         | 0.00156444854349  | 0.0831748317483  | 0.000525489460228  | 1.10399298843                      | 0.0284654263748 | 
| Zhad  | 500                    | 2000                | 0.106888551084  | 0.00194020957866  | 0.115234371093   | 0.000643066550202  | 1.07807964393                      | 0.0246376857897 | 
| Zhad  | 500                    | 10000               | 0.106219119441  | 0.0019327264158   | 0.115810412847   | 0.000679999776607  | 1.09029724079                      | 0.0251755833605 | 
| Zhad  | 1000                   | 10                  | 0.116351635164  | 0.00204590410103  | 0.126621777386   | 0.000762888864123  | 1.08826813828                      | 0.0247193066163 | 
| Zhad  | 1000                   | 1000                | 0.119809584767  | 0.00208385183299  | 0.12596240591    | 0.000680113955362  | 1.05135499931                      | 0.0233611780352 | 
| Zhad  | 1000                   | 1995                | 0.110788863109  | 0.00198409093339  | 0.119481470221   | 0.000657842251019  | 1.07846101917                      | 0.0243124451528 | 
| Whad  | 1                      | 100                 | 0.00318         | 0.000266411796595 | 0.00479          | 0.00010465155739   | 1.50628930818                      | 0.133348213388  | 
| Whad  | 1                      | 300                 | 0.0163403268065 | 0.000644752564432 | 0.022564         | 0.000244343833834  | 1.38087813464                      | 0.060106608242  | 
| Whad  | 1                      | 2000                | 0.0903490349035 | 0.00174838041033  | 0.11219185343    | 0.000632376947846  | 1.24176039677                      | 0.0280428126621 | 
| Whad  | 10                     | 10                  | 0.0012          | 0.000160285896994 | 0.00184          | 6.32651565072e-05  | 1.53333333333                      | 0.214410391921  | 
| Whad  | 10                     | 100                 | 0.00308         | 0.000261967651661 | 0.00489400978802 | 0.000105855701455  | 1.58896421689                      | 0.139665121243  | 
| Whad  | 10                     | 10000               | 0.0713028521141 | 0.00151308261344  | 0.0899346551645  | 0.000551317229667  | 1.26130515818                      | 0.0309729809331 | 
| Whad  | 50                     | 10                  | 0.00892         | 0.000462265694357 | 0.0131900263801  | 0.000181073068374  | 1.47870250897                      | 0.0818406832813 | 
| Whad  | 50                     | 95                  | 0.00472         | 0.000328354311622 | 0.00727          | 0.000130863254958  | 1.54025423729                      | 0.112270549699  | 
| Whad  | 50                     | 300                 | 0.01576         | 0.000631907616556 | 0.022814         | 0.000245870984198  | 1.44758883249                      | 0.0626794230656 | 
| Whad  | 150                    | 10                  | 0.03138         | 0.000932547719081 | 0.0401983215866  | 0.000340393391354  | 1.28101725897                      | 0.043613687962  | 
| Whad  | 150                    | 295                 | 0.02046         | 0.000731187325308 | 0.0271720543441  | 0.000271545588308  | 1.32805739707                      | 0.0533634141009 | 
| Whad  | 150                    | 1000                | 0.06114         | 0.00137922926803  | 0.076684920219   | 0.000500076471413  | 1.25425123028                      | 0.0328173175913 | 
| Whad  | 500                    | 10                  | 0.0769215384308 | 0.00158435436346  | 0.0957930653781  | 0.000573186553027  | 1.24533475711                      | 0.0298767230497 | 
| Whad  | 500                    | 995                 | 0.06256         | 0.00139834734167  | 0.0831748317483  | 0.000525489460228  | 1.32952096784                      | 0.0335197665829 | 
| Whad  | 500                    | 2000                | 0.0929818596372 | 0.00177953046466  | 0.115234371093   | 0.000643066550202  | 1.23932099813                      | 0.0277096667411 | 
| Whad  | 500                    | 10000               | 0.0952590518104 | 0.0018064750423   | 0.115810412847   | 0.000679999776607  | 1.21574181819                      | 0.027642299152  | 
| Whad  | 1000                   | 10                  | 0.0991879350348 | 0.00185211570751  | 0.126621777386   | 0.000762888864123  | 1.27658446908                      | 0.0284914468891 | 
| Whad  | 1000                   | 1000                | 0.099597927627  | 0.00185695022401  | 0.12596240591    | 0.000680113955362  | 1.26470910501                      | 0.0272806533282 | 
| Whad  | 1000                   | 1995                | 0.0957914949794 | 0.00181263642307  | 0.119481470221   | 0.000657842251019  | 1.2473077098                       | 0.0274885378411 | 

