## Mono-V Run 2 signal yield and acceptance studies
#### 11.04.2017
This document shows pre-fit signal yields and acceptance x efficiency for Mono-W(had.) and Mono-Z(had.) samples (full simulation), which have been evaluated after the full analysis chain, including b-tagging and other event weights. 
The post-fit signal yields and acceptances will of course differ from the quantities shown here. The post-fit yields are shown here:
http://pgadow.web.cern.ch/pgadow/notes/index.php?file=MonoV_postfityieldstudy2017-04-19.md

The signal samples are already normalised to their cross-sections.

More detail on the signal samples is given here:
https://twiki.cern.ch/twiki/bin/viewauth/AtlasProtected/MonoWZHad

### Input
The signal sample histograms using the event selection implemented following the event selection implemented in [commit 235fd630c50a1df391a0869d44ec46f02d212966](https://gitlab.cern.ch/CxAODFramework/CxAODReader_monoVH/commit/235fd630c50a1df391a0869d44ec46f02d212966) of the CxAODReader_monoVH code.

The study was performed with the input file, which can be accessed here:
https://cernbox.cern.ch/index.php/s/MR5VqFIhJupCLbQ

The password to obtain the file can be obtained from the author (Paul.Philipp.Gadow@spamnotCERN.ch)

### List of samples with less than 0.001 yield in one or more analysis categories
* WWxxDM1 : 3.95596280214e-05
* WWxxDM10 : 2.23560473387e-05
* WWxxDM1000 : 0.000129864203085
* WWxxDM150 : 4.93489437758e-05
* WWxxDM50 : 7.29609578229e-05
* WWxxDM500 : 0.000909367848575
* ZZxxDM1 : 0.000339654935477
* ZZxxDM10 : 0.000355943000838
* ZZxxDM1000 : 0.000606499201542
* ZZxxDM150 : 0.000294001754355
* ZZxxDM50 : 0.000400763183961
* ZZxxDM500 : 0.000688910338848
* dmVWhadDM1000MM10 : 0.000269536307314
* dmVWhadDM1000MM1000 : 0.000271456156042
* dmVWhadDM10MM10 : 0
* dmVWhadDM10MM100 : 0
* dmVWhadDM10MM10000 : 0.000100795343883
* dmVWhadDM150MM10 : 0
* dmVWhadDM150MM1000 : 0
* dmVWhadDM150MM295 : 0
* dmVWhadDM1MM10 : 0.0
* dmVWhadDM1MM100 : 0
* dmVWhadDM1MM300 : 0
* dmVWhadDM500MM10 : 0
* dmVWhadDM500MM10000 : 0
* dmVWhadDM50MM10 : 0
* dmVWhadDM50MM300 : 0
* dmVWhadDM50MM95 : 0
* dmVZhadDM10MM10 : 0
* dmVZhadDM10MM10000 : 0.000451019912724
* dmVZhadDM1MM10 : 0
* dmVZhadDM500MM10000 : 0.000333106633925

### List of samples with no entries in one or more analysis categories

* WWxxDM1 : 0
* WWxxDM500 : 0
* dmVWhadDM10MM10 : 0
* dmVWhadDM10MM100 : 0
* dmVWhadDM150MM10 : 0
* dmVWhadDM150MM1000 : 0
* dmVWhadDM150MM295 : 0
* dmVWhadDM1MM10 : 0.0
* dmVWhadDM1MM100 : 0
* dmVWhadDM1MM300 : 0
* dmVWhadDM500MM10 : 0
* dmVWhadDM500MM10000 : 0
* dmVWhadDM50MM10 : 0
* dmVWhadDM50MM300 : 0
* dmVWhadDM50MM95 : 0
* dmVZhadDM10MM10 : 0
* dmVZhadDM1MM10 : 0

### Definitions

**Signal yield** is defined as the weighted entries in the pre-fit $E_{\text{T}}^{\text{miss}}$ distributions. The **uncertainty on the signal yield** is the associated error which is stored in the weighted pre-fit histograms. The **entries** are the integer number of the histogram entries and correspond to unweighted events.

The acceptance*efficiency is defined as the number entries in the pre-fit histogram as defined before divided by the number of generated events.

The number of generated events, according to the [production request](https://its.cern.ch/jira/browse/ATLMCPROD-1875) is 20.000 events.

The uncertainty on the acceptance*efficiency is defined as $\sigma_{\text{acceptance} \times \text{efficiency}} = \frac{\sqrt{\text{entries}}}{\text{number of generated events}}$ (assuming a Poissonian distribution).

### Detailed list of yields and histogram entries for signal models
```
dmVWhadDM1000MM1995
         0 tag merged   signal yield:   2.6214 +/-   0.0702 ( 1668.0 entries)    acceptance*efficiency: 0.0834 +/- 0.0020
         1 tag merged   signal yield:   0.2623 +/-   0.0236 (  142.0 entries)    acceptance*efficiency: 0.0071 +/- 0.0006
         2 tag merged   signal yield:   0.0029 +/-   0.0020 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
         0 tag resolved signal yield:   4.5586 +/-   0.0976 ( 2838.0 entries)    acceptance*efficiency: 0.1419 +/- 0.0027
         1 tag resolved signal yield:   0.1640 +/-   0.0172 (   98.0 entries)    acceptance*efficiency: 0.0049 +/- 0.0005
         2 tag resolved signal yield:   0.0114 +/-   0.0041 (    8.0 entries)    acceptance*efficiency: 0.0004 +/- 0.0001
dmVWhadDM1000MM1000
         0 tag merged   signal yield:   0.0919 +/-   0.0026 ( 1876.0 entries)    acceptance*efficiency: 0.0938 +/- 0.0022
         1 tag merged   signal yield:   0.0063 +/-   0.0006 (  126.0 entries)    acceptance*efficiency: 0.0063 +/- 0.0006
         2 tag merged   signal yield:   0.0003 +/-   0.0001 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield:   0.1375 +/-   0.0029 ( 3030.0 entries)    acceptance*efficiency: 0.1515 +/- 0.0028
         1 tag resolved signal yield:   0.0056 +/-   0.0005 (  122.0 entries)    acceptance*efficiency: 0.0061 +/- 0.0006
         2 tag resolved signal yield:   0.0001 +/-   0.0001 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
dmVWhadDM1000MM10
         0 tag merged   signal yield:   0.0585 +/-   0.0015 ( 1920.0 entries)    acceptance*efficiency: 0.0960 +/- 0.0022
         1 tag merged   signal yield:   0.0056 +/-   0.0005 (  156.0 entries)    acceptance*efficiency: 0.0078 +/- 0.0006
         2 tag merged   signal yield:   0.0003 +/-   0.0001 (   10.0 entries)    acceptance*efficiency: 0.0005 +/- 0.0002
         0 tag resolved signal yield:   0.0842 +/-   0.0018 ( 2776.0 entries)    acceptance*efficiency: 0.1388 +/- 0.0026
         1 tag resolved signal yield:   0.0050 +/-   0.0005 (  140.0 entries)    acceptance*efficiency: 0.0070 +/- 0.0006
         2 tag resolved signal yield:   0.0001 +/-   0.0001 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
dmVWhadDM500MM10000
         0 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         1 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         1 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM500MM2000
         0 tag merged   signal yield:  12.8567 +/-   0.3531 ( 1710.0 entries)    acceptance*efficiency: 0.0855 +/- 0.0021
         1 tag merged   signal yield:   1.2555 +/-   0.1233 (  144.0 entries)    acceptance*efficiency: 0.0072 +/- 0.0006
         2 tag merged   signal yield:   0.0398 +/-   0.0163 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
         0 tag resolved signal yield:  22.0763 +/-   0.4690 ( 2942.0 entries)    acceptance*efficiency: 0.1471 +/- 0.0027
         1 tag resolved signal yield:   0.8802 +/-   0.0890 (  108.0 entries)    acceptance*efficiency: 0.0054 +/- 0.0005
         2 tag resolved signal yield:   0.0392 +/-   0.0160 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
dmVWhadDM500MM995
         0 tag merged   signal yield:  29.3022 +/-   0.9838 ( 1150.0 entries)    acceptance*efficiency: 0.0575 +/- 0.0017
         1 tag merged   signal yield:   3.0955 +/-   0.3249 (  104.0 entries)    acceptance*efficiency: 0.0052 +/- 0.0005
         2 tag merged   signal yield:   0.0762 +/-   0.0381 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield:  68.7079 +/-   1.4953 ( 2764.0 entries)    acceptance*efficiency: 0.1382 +/- 0.0026
         1 tag resolved signal yield:   4.1605 +/-   0.4630 (  134.0 entries)    acceptance*efficiency: 0.0067 +/- 0.0006
         2 tag resolved signal yield:   0.1880 +/-   0.0825 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
dmVWhadDM500MM10
         0 tag merged   signal yield:   1.2111 +/-   0.0349 ( 1508.0 entries)    acceptance*efficiency: 0.0754 +/- 0.0019
         1 tag merged   signal yield:   0.1097 +/-   0.0125 (  110.0 entries)    acceptance*efficiency: 0.0055 +/- 0.0005
         2 tag merged   signal yield:   0.0021 +/-   0.0015 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
         0 tag resolved signal yield:   2.2559 +/-   0.0488 ( 2852.0 entries)    acceptance*efficiency: 0.1426 +/- 0.0027
         1 tag resolved signal yield:   0.1292 +/-   0.0147 (  116.0 entries)    acceptance*efficiency: 0.0058 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM150MM1000
         0 tag merged   signal yield: 134.0460 +/-   4.5641 ( 1118.0 entries)    acceptance*efficiency: 0.0559 +/- 0.0017
         1 tag merged   signal yield:  14.5850 +/-   1.6652 (   98.0 entries)    acceptance*efficiency: 0.0049 +/- 0.0005
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 326.2126 +/-   7.2901 ( 2726.0 entries)    acceptance*efficiency: 0.1363 +/- 0.0026
         1 tag resolved signal yield:  13.3693 +/-   1.5263 (   94.0 entries)    acceptance*efficiency: 0.0047 +/- 0.0005
         2 tag resolved signal yield:   0.1766 +/-   0.1249 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
dmVWhadDM150MM295
         0 tag merged   signal yield: 191.1867 +/-  11.3120 (  402.0 entries)    acceptance*efficiency: 0.0201 +/- 0.0010
         1 tag merged   signal yield:  12.6018 +/-   2.8552 (   22.0 entries)    acceptance*efficiency: 0.0011 +/- 0.0002
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 811.3672 +/-  23.0267 ( 1750.0 entries)    acceptance*efficiency: 0.0875 +/- 0.0021
         1 tag resolved signal yield:  43.6362 +/-   4.9291 (   86.0 entries)    acceptance*efficiency: 0.0043 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM150MM10
         0 tag merged   signal yield:  19.1306 +/-   0.8842 (  582.0 entries)    acceptance*efficiency: 0.0291 +/- 0.0012
         1 tag merged   signal yield:   1.3109 +/-   0.2187 (   38.0 entries)    acceptance*efficiency: 0.0019 +/- 0.0003
         2 tag merged   signal yield:   0.1258 +/-   0.0632 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield:  65.7264 +/-   1.6370 ( 2018.0 entries)    acceptance*efficiency: 0.1009 +/- 0.0022
         1 tag resolved signal yield:   4.2919 +/-   0.4793 (  102.0 entries)    acceptance*efficiency: 0.0051 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM50MM300
         0 tag merged   signal yield: 985.6684 +/-  68.3623 (  302.0 entries)    acceptance*efficiency: 0.0151 +/- 0.0009
         1 tag merged   signal yield: 124.2654 +/-  20.7189 (   38.0 entries)    acceptance*efficiency: 0.0019 +/- 0.0003
         2 tag merged   signal yield:   5.6101 +/-   3.9670 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
         0 tag resolved signal yield: 5101.8906 +/- 147.5312 ( 1634.0 entries)   acceptance*efficiency: 0.0817 +/- 0.0020
         1 tag resolved signal yield: 211.1802 +/-  29.2780 (   58.0 entries)    acceptance*efficiency: 0.0029 +/- 0.0004
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM50MM95
         0 tag merged   signal yield: 241.6803 +/-  24.2517 (  118.0 entries)    acceptance*efficiency: 0.0059 +/- 0.0005
         1 tag merged   signal yield:  11.7327 +/-   4.7928 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 1262.9615 +/-  50.3754 (  692.0 entries)   acceptance*efficiency: 0.0346 +/- 0.0013
         1 tag resolved signal yield:  49.0323 +/-  10.7582 (   22.0 entries)    acceptance*efficiency: 0.0011 +/- 0.0002
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM50MM10
         0 tag merged   signal yield:  56.6930 +/-   5.1789 (  164.0 entries)    acceptance*efficiency: 0.0082 +/- 0.0006
         1 tag merged   signal yield:   3.2128 +/-   1.0170 (   10.0 entries)    acceptance*efficiency: 0.0005 +/- 0.0002
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 367.1333 +/-  13.8910 ( 1034.0 entries)    acceptance*efficiency: 0.0517 +/- 0.0016
         1 tag resolved signal yield:  13.4168 +/-   2.9746 (   30.0 entries)    acceptance*efficiency: 0.0015 +/- 0.0003
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM10MM10000
         0 tag merged   signal yield:   0.0012 +/-   0.0000 ( 1302.0 entries)    acceptance*efficiency: 0.0651 +/- 0.0018
         1 tag merged   signal yield:   0.0001 +/-   0.0000 (   96.0 entries)    acceptance*efficiency: 0.0048 +/- 0.0005
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield:   0.0023 +/-   0.0001 ( 2536.0 entries)    acceptance*efficiency: 0.1268 +/- 0.0025
         1 tag resolved signal yield:   0.0001 +/-   0.0000 (  110.0 entries)    acceptance*efficiency: 0.0055 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
dmVWhadDM10MM100
         0 tag merged   signal yield: 1380.3097 +/- 172.8563 (   68.0 entries)   acceptance*efficiency: 0.0034 +/- 0.0004
         1 tag merged   signal yield: 502.8262 +/- 209.2019 (   12.0 entries)    acceptance*efficiency: 0.0006 +/- 0.0002
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 12705.1307 +/- 628.3758 (  536.0 entries)  acceptance*efficiency: 0.0268 +/- 0.0012
         1 tag resolved signal yield: 465.1157 +/- 116.1163 (   18.0 entries)    acceptance*efficiency: 0.0009 +/- 0.0002
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM10MM10
         0 tag merged   signal yield:  79.0034 +/-  24.6881 (   12.0 entries)    acceptance*efficiency: 0.0006 +/- 0.0002
         1 tag merged   signal yield:  22.0726 +/-  11.0628 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 1437.4272 +/- 146.1665 (  208.0 entries)   acceptance*efficiency: 0.0104 +/- 0.0007
         1 tag resolved signal yield:  55.3329 +/-  23.4452 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM1MM2000
         0 tag merged   signal yield:  12.9605 +/-   0.3608 ( 1616.0 entries)    acceptance*efficiency: 0.0808 +/- 0.0020
         1 tag merged   signal yield:   1.1399 +/-   0.1104 (  130.0 entries)    acceptance*efficiency: 0.0065 +/- 0.0006
         2 tag merged   signal yield:   0.1106 +/-   0.0428 (    8.0 entries)    acceptance*efficiency: 0.0004 +/- 0.0001
         0 tag resolved signal yield:  24.2911 +/-   0.5243 ( 3002.0 entries)    acceptance*efficiency: 0.1501 +/- 0.0027
         1 tag resolved signal yield:   1.0814 +/-   0.1110 (  110.0 entries)    acceptance*efficiency: 0.0055 +/- 0.0005
         2 tag resolved signal yield:   0.0416 +/-   0.0170 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
dmVWhadDM1MM300
         0 tag merged   signal yield: 1077.6270 +/-  70.0934 (  320.0 entries)   acceptance*efficiency: 0.0160 +/- 0.0009
         1 tag merged   signal yield:  77.1698 +/-  18.6201 (   22.0 entries)    acceptance*efficiency: 0.0011 +/- 0.0002
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 5244.3953 +/- 147.9938 ( 1680.0 entries)   acceptance*efficiency: 0.0840 +/- 0.0020
         1 tag resolved signal yield: 226.7654 +/-  53.2989 (   46.0 entries)    acceptance*efficiency: 0.0023 +/- 0.0003
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
dmVWhadDM1MM100
         0 tag merged   signal yield: 1327.6145 +/- 178.1134 (   62.0 entries)   acceptance*efficiency: 0.0031 +/- 0.0004
         1 tag merged   signal yield:  93.9484 +/-  47.0164 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         0 tag resolved signal yield: 10783.9655 +/- 518.9313 (  492.0 entries)  acceptance*efficiency: 0.0246 +/- 0.0011
         1 tag resolved signal yield: 836.2046 +/- 145.1579 (   36.0 entries)    acceptance*efficiency: 0.0018 +/- 0.0003
         2 tag resolved signal yield:  54.9395 +/-  38.8481 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
dmVWhadDM1MM10
         0 tag merged   signal yield: 2054.2741 +/- 1027.2171 (    6.0 entries)  acceptance*efficiency: 0.0003 +/- 0.0001
         1 tag merged   signal yield:   0.0000 +/-   0.0000 ( 1488.0 entries)    acceptance*efficiency: 0.0744 +/- 0.0019
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (  404.0 entries)    acceptance*efficiency: 0.0202 +/- 0.0010
         0 tag resolved signal yield: 11460.2665 +/- 2462.1259 (   22.0 entries) acceptance*efficiency: 0.0011 +/- 0.0002
         1 tag resolved signal yield:   0.0000 +/-   0.0000 (27296.0 entries)    acceptance*efficiency: 1.3648 +/- 0.0083
         2 tag resolved signal yield:   0.0000 +/-   0.0000 ( 4524.0 entries)    acceptance*efficiency: 0.2262 +/- 0.0034
dmVZhadDM1000MM1995
         0 tag merged   signal yield:   1.0312 +/-   0.0284 ( 1760.0 entries)    acceptance*efficiency: 0.0880 +/- 0.0021
         1 tag merged   signal yield:   0.1631 +/-   0.0112 (  250.0 entries)    acceptance*efficiency: 0.0125 +/- 0.0008
         2 tag merged   signal yield:   0.2068 +/-   0.0122 (  346.0 entries)    acceptance*efficiency: 0.0173 +/- 0.0009
         0 tag resolved signal yield:   1.3352 +/-   0.0327 ( 2300.0 entries)    acceptance*efficiency: 0.1150 +/- 0.0024
         1 tag resolved signal yield:   0.1407 +/-   0.0092 (  258.0 entries)    acceptance*efficiency: 0.0129 +/- 0.0008
         2 tag resolved signal yield:   0.1997 +/-   0.0125 (  322.0 entries)    acceptance*efficiency: 0.0161 +/- 0.0009
dmVZhadDM1000MM1000
         0 tag merged   signal yield:   0.0311 +/-   0.0008 ( 1882.0 entries)    acceptance*efficiency: 0.0941 +/- 0.0022
         1 tag merged   signal yield:   0.0047 +/-   0.0004 (  252.0 entries)    acceptance*efficiency: 0.0126 +/- 0.0008
         2 tag merged   signal yield:   0.0052 +/-   0.0003 (  322.0 entries)    acceptance*efficiency: 0.0161 +/- 0.0009
         0 tag resolved signal yield:   0.0386 +/-   0.0009 ( 2334.0 entries)    acceptance*efficiency: 0.1167 +/- 0.0024
         1 tag resolved signal yield:   0.0045 +/-   0.0003 (  280.0 entries)    acceptance*efficiency: 0.0140 +/- 0.0008
         2 tag resolved signal yield:   0.0074 +/-   0.0004 (  404.0 entries)    acceptance*efficiency: 0.0202 +/- 0.0010
dmVZhadDM1000MM10
         0 tag merged   signal yield:   0.0199 +/-   0.0005 ( 1772.0 entries)    acceptance*efficiency: 0.0886 +/- 0.0021
         1 tag merged   signal yield:   0.0030 +/-   0.0002 (  262.0 entries)    acceptance*efficiency: 0.0131 +/- 0.0008
         2 tag merged   signal yield:   0.0036 +/-   0.0002 (  324.0 entries)    acceptance*efficiency: 0.0162 +/- 0.0009
         0 tag resolved signal yield:   0.0270 +/-   0.0007 ( 2302.0 entries)    acceptance*efficiency: 0.1151 +/- 0.0024
         1 tag resolved signal yield:   0.0028 +/-   0.0002 (  246.0 entries)    acceptance*efficiency: 0.0123 +/- 0.0008
         2 tag resolved signal yield:   0.0046 +/-   0.0003 (  380.0 entries)    acceptance*efficiency: 0.0190 +/- 0.0010
dmVZhadDM500MM10000
         0 tag merged   signal yield:   0.0003 +/-   0.0000 ( 1718.0 entries)    acceptance*efficiency: 0.0859 +/- 0.0021
         1 tag merged   signal yield:   0.0001 +/-   0.0000 (  278.0 entries)    acceptance*efficiency: 0.0139 +/- 0.0008
         2 tag merged   signal yield:   0.0001 +/-   0.0000 (  280.0 entries)    acceptance*efficiency: 0.0140 +/- 0.0008
         0 tag resolved signal yield:   0.0005 +/-   0.0000 ( 2476.0 entries)    acceptance*efficiency: 0.1238 +/- 0.0025
         1 tag resolved signal yield:   0.0001 +/-   0.0000 (  268.0 entries)    acceptance*efficiency: 0.0134 +/- 0.0008
         2 tag resolved signal yield:   0.0001 +/-   0.0000 (  348.0 entries)    acceptance*efficiency: 0.0174 +/- 0.0009
dmVZhadDM500MM2000
         0 tag merged   signal yield:   4.6738 +/-   0.1357 ( 1660.0 entries)    acceptance*efficiency: 0.0830 +/- 0.0020
         1 tag merged   signal yield:   0.6691 +/-   0.0482 (  230.0 entries)    acceptance*efficiency: 0.0115 +/- 0.0008
         2 tag merged   signal yield:   0.7988 +/-   0.0539 (  288.0 entries)    acceptance*efficiency: 0.0144 +/- 0.0008
         0 tag resolved signal yield:   6.3103 +/-   0.1447 ( 2308.0 entries)    acceptance*efficiency: 0.1154 +/- 0.0024
         1 tag resolved signal yield:   0.7877 +/-   0.0568 (  252.0 entries)    acceptance*efficiency: 0.0126 +/- 0.0008
         2 tag resolved signal yield:   0.9888 +/-   0.0582 (  360.0 entries)    acceptance*efficiency: 0.0180 +/- 0.0009
dmVZhadDM500MM995
         0 tag merged   signal yield:  10.4414 +/-   0.3378 ( 1172.0 entries)    acceptance*efficiency: 0.0586 +/- 0.0017
         1 tag merged   signal yield:   1.5890 +/-   0.1407 (  160.0 entries)    acceptance*efficiency: 0.0080 +/- 0.0006
         2 tag merged   signal yield:   1.9590 +/-   0.1764 (  206.0 entries)    acceptance*efficiency: 0.0103 +/- 0.0007
         0 tag resolved signal yield:  20.0106 +/-   0.4780 ( 2242.0 entries)    acceptance*efficiency: 0.1121 +/- 0.0024
         1 tag resolved signal yield:   2.4593 +/-   0.1604 (  266.0 entries)    acceptance*efficiency: 0.0133 +/- 0.0008
         2 tag resolved signal yield:   3.2495 +/-   0.1955 (  350.0 entries)    acceptance*efficiency: 0.0175 +/- 0.0009
dmVZhadDM500MM10
         0 tag merged   signal yield:   0.4181 +/-   0.0128 ( 1414.0 entries)    acceptance*efficiency: 0.0707 +/- 0.0019
         1 tag merged   signal yield:   0.0498 +/-   0.0042 (  162.0 entries)    acceptance*efficiency: 0.0081 +/- 0.0006
         2 tag merged   signal yield:   0.0893 +/-   0.0068 (  282.0 entries)    acceptance*efficiency: 0.0141 +/- 0.0008
         0 tag resolved signal yield:   0.6792 +/-   0.0163 ( 2336.0 entries)    acceptance*efficiency: 0.1168 +/- 0.0024
         1 tag resolved signal yield:   0.0691 +/-   0.0046 (  248.0 entries)    acceptance*efficiency: 0.0124 +/- 0.0008
         2 tag resolved signal yield:   0.0863 +/-   0.0051 (  312.0 entries)    acceptance*efficiency: 0.0156 +/- 0.0009
dmVZhadDM150MM1000
         0 tag merged   signal yield:  45.2727 +/-   1.7850 (  910.0 entries)    acceptance*efficiency: 0.0455 +/- 0.0015
         1 tag merged   signal yield:   7.0666 +/-   0.6386 (  142.0 entries)    acceptance*efficiency: 0.0071 +/- 0.0006
         2 tag merged   signal yield:   9.8716 +/-   0.7221 (  208.0 entries)    acceptance*efficiency: 0.0104 +/- 0.0007
         0 tag resolved signal yield:  96.2984 +/-   2.4069 ( 2012.0 entries)    acceptance*efficiency: 0.1006 +/- 0.0022
         1 tag resolved signal yield:  13.1288 +/-   0.9451 (  252.0 entries)    acceptance*efficiency: 0.0126 +/- 0.0008
         2 tag resolved signal yield:  13.7886 +/-   0.9815 (  268.0 entries)    acceptance*efficiency: 0.0134 +/- 0.0008
dmVZhadDM150MM295
         0 tag merged   signal yield:  55.0841 +/-   3.3026 (  346.0 entries)    acceptance*efficiency: 0.0173 +/- 0.0009
         1 tag merged   signal yield:   7.1709 +/-   1.7229 (   32.0 entries)    acceptance*efficiency: 0.0016 +/- 0.0003
         2 tag merged   signal yield:  11.0854 +/-   1.3681 (   70.0 entries)    acceptance*efficiency: 0.0035 +/- 0.0004
         0 tag resolved signal yield: 251.4672 +/-   7.4525 ( 1524.0 entries)    acceptance*efficiency: 0.0762 +/- 0.0020
         1 tag resolved signal yield:  23.2095 +/-   2.2401 (  136.0 entries)    acceptance*efficiency: 0.0068 +/- 0.0006
         2 tag resolved signal yield:  35.5242 +/-   3.1536 (  188.0 entries)    acceptance*efficiency: 0.0094 +/- 0.0007
dmVZhadDM150MM10
         0 tag merged   signal yield:   7.3892 +/-   0.3526 (  582.0 entries)    acceptance*efficiency: 0.0291 +/- 0.0012
         1 tag merged   signal yield:   1.0052 +/-   0.1613 (   62.0 entries)    acceptance*efficiency: 0.0031 +/- 0.0004
         2 tag merged   signal yield:   1.2227 +/-   0.1314 (  104.0 entries)    acceptance*efficiency: 0.0052 +/- 0.0005
         0 tag resolved signal yield:  23.0101 +/-   0.6093 ( 1910.0 entries)    acceptance*efficiency: 0.0955 +/- 0.0022
         1 tag resolved signal yield:   2.1249 +/-   0.1587 (  190.0 entries)    acceptance*efficiency: 0.0095 +/- 0.0007
         2 tag resolved signal yield:   3.0828 +/-   0.2296 (  238.0 entries)    acceptance*efficiency: 0.0119 +/- 0.0008
dmVZhadDM50MM300
         0 tag merged   signal yield: 369.0643 +/-  22.8821 (  300.0 entries)    acceptance*efficiency: 0.0150 +/- 0.0009
         1 tag merged   signal yield:  70.2238 +/-  10.0705 (   54.0 entries)    acceptance*efficiency: 0.0027 +/- 0.0004
         2 tag merged   signal yield:  50.0940 +/-   8.6741 (   40.0 entries)    acceptance*efficiency: 0.0020 +/- 0.0003
         0 tag resolved signal yield: 1529.4542 +/-  47.2785 ( 1258.0 entries)   acceptance*efficiency: 0.0629 +/- 0.0018
         1 tag resolved signal yield: 145.2311 +/-  13.8301 (  122.0 entries)    acceptance*efficiency: 0.0061 +/- 0.0006
         2 tag resolved signal yield: 188.8705 +/-  16.7181 (  160.0 entries)    acceptance*efficiency: 0.0080 +/- 0.0006
dmVZhadDM50MM95
         0 tag merged   signal yield:  79.4561 +/-   8.2510 (  108.0 entries)    acceptance*efficiency: 0.0054 +/- 0.0005
         1 tag merged   signal yield:   5.2380 +/-   1.8597 (    8.0 entries)    acceptance*efficiency: 0.0004 +/- 0.0001
         2 tag merged   signal yield:  12.3914 +/-   2.7753 (   20.0 entries)    acceptance*efficiency: 0.0010 +/- 0.0002
         0 tag resolved signal yield: 413.3342 +/-  19.6215 (  598.0 entries)    acceptance*efficiency: 0.0299 +/- 0.0012
         1 tag resolved signal yield:  46.1803 +/-   6.2882 (   64.0 entries)    acceptance*efficiency: 0.0032 +/- 0.0004
         2 tag resolved signal yield:  30.4914 +/-   4.6501 (   48.0 entries)    acceptance*efficiency: 0.0024 +/- 0.0003
dmVZhadDM50MM10
         0 tag merged   signal yield:  29.6383 +/-   2.4252 (  216.0 entries)    acceptance*efficiency: 0.0108 +/- 0.0007
         1 tag merged   signal yield:   2.9327 +/-   0.7025 (   22.0 entries)    acceptance*efficiency: 0.0011 +/- 0.0002
         2 tag merged   signal yield:   3.4325 +/-   0.6639 (   30.0 entries)    acceptance*efficiency: 0.0015 +/- 0.0003
         0 tag resolved signal yield: 113.8008 +/-   4.4938 (  894.0 entries)    acceptance*efficiency: 0.0447 +/- 0.0015
         1 tag resolved signal yield:  15.5469 +/-   1.4315 (  126.0 entries)    acceptance*efficiency: 0.0063 +/- 0.0006
         2 tag resolved signal yield:  13.9013 +/-   1.4099 (  114.0 entries)    acceptance*efficiency: 0.0057 +/- 0.0005
dmVZhadDM10MM10000
         0 tag merged   signal yield:   0.0005 +/-   0.0000 ( 1338.0 entries)    acceptance*efficiency: 0.0669 +/- 0.0018
         1 tag merged   signal yield:   0.0001 +/-   0.0000 (  158.0 entries)    acceptance*efficiency: 0.0079 +/- 0.0006
         2 tag merged   signal yield:   0.0001 +/-   0.0000 (  262.0 entries)    acceptance*efficiency: 0.0131 +/- 0.0008
         0 tag resolved signal yield:   0.0007 +/-   0.0000 ( 2162.0 entries)    acceptance*efficiency: 0.1081 +/- 0.0023
         1 tag resolved signal yield:   0.0001 +/-   0.0000 (  238.0 entries)    acceptance*efficiency: 0.0119 +/- 0.0008
         2 tag resolved signal yield:   0.0001 +/-   0.0000 (  312.0 entries)    acceptance*efficiency: 0.0156 +/- 0.0009
dmVZhadDM10MM100
         0 tag merged   signal yield: 327.3644 +/-  51.7689 (   42.0 entries)    acceptance*efficiency: 0.0021 +/- 0.0003
         1 tag merged   signal yield:  19.8592 +/-  14.0426 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
         2 tag merged   signal yield:  46.9909 +/-  19.3603 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
         0 tag resolved signal yield: 3640.7071 +/- 197.6745 (  438.0 entries)   acceptance*efficiency: 0.0219 +/- 0.0010
         1 tag resolved signal yield: 397.2739 +/-  57.6360 (   52.0 entries)    acceptance*efficiency: 0.0026 +/- 0.0004
         2 tag resolved signal yield: 464.0799 +/-  64.1920 (   56.0 entries)    acceptance*efficiency: 0.0028 +/- 0.0004
dmVZhadDM10MM10
         0 tag merged   signal yield:  76.1952 +/-  20.5542 (   24.0 entries)    acceptance*efficiency: 0.0012 +/- 0.0002
         1 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         2 tag merged   signal yield:  14.2103 +/-   6.0571 (    6.0 entries)    acceptance*efficiency: 0.0003 +/- 0.0001
         0 tag resolved signal yield: 353.3349 +/-  35.7840 (  160.0 entries)    acceptance*efficiency: 0.0080 +/- 0.0006
         1 tag resolved signal yield:  23.2521 +/-   7.5939 (   10.0 entries)    acceptance*efficiency: 0.0005 +/- 0.0002
         2 tag resolved signal yield:  23.9356 +/-   6.9945 (   12.0 entries)    acceptance*efficiency: 0.0006 +/- 0.0002
dmVZhadDM1MM2000
         0 tag merged   signal yield:   4.7821 +/-   0.1343 ( 1656.0 entries)    acceptance*efficiency: 0.0828 +/- 0.0020
         1 tag merged   signal yield:   0.6879 +/-   0.0594 (  216.0 entries)    acceptance*efficiency: 0.0108 +/- 0.0007
         2 tag merged   signal yield:   0.7464 +/-   0.0507 (  268.0 entries)    acceptance*efficiency: 0.0134 +/- 0.0008
         0 tag resolved signal yield:   7.0321 +/-   0.1635 ( 2444.0 entries)    acceptance*efficiency: 0.1222 +/- 0.0025
         1 tag resolved signal yield:   0.8259 +/-   0.0572 (  266.0 entries)    acceptance*efficiency: 0.0133 +/- 0.0008
         2 tag resolved signal yield:   1.1083 +/-   0.0702 (  378.0 entries)    acceptance*efficiency: 0.0189 +/- 0.0010
dmVZhadDM1MM300
         0 tag merged   signal yield: 315.2203 +/-  19.7799 (  282.0 entries)    acceptance*efficiency: 0.0141 +/- 0.0008
         1 tag merged   signal yield:  22.4490 +/-   5.5642 (   18.0 entries)    acceptance*efficiency: 0.0009 +/- 0.0002
         2 tag merged   signal yield:  42.2127 +/-   7.1284 (   38.0 entries)    acceptance*efficiency: 0.0019 +/- 0.0003
         0 tag resolved signal yield: 1458.2739 +/-  43.0523 ( 1338.0 entries)   acceptance*efficiency: 0.0669 +/- 0.0018
         1 tag resolved signal yield: 179.5289 +/-  14.5304 (  164.0 entries)    acceptance*efficiency: 0.0082 +/- 0.0006
         2 tag resolved signal yield: 196.4095 +/-  15.4521 (  176.0 entries)    acceptance*efficiency: 0.0088 +/- 0.0007
dmVZhadDM1MM100
         0 tag merged   signal yield: 590.7631 +/-  72.6189 (   76.0 entries)    acceptance*efficiency: 0.0038 +/- 0.0004
         1 tag merged   signal yield: 165.0202 +/-  49.0856 (   14.0 entries)    acceptance*efficiency: 0.0007 +/- 0.0002
         2 tag merged   signal yield: 126.1181 +/-  36.2088 (   14.0 entries)    acceptance*efficiency: 0.0007 +/- 0.0002
         0 tag resolved signal yield: 3949.0118 +/- 218.3640 (  466.0 entries)   acceptance*efficiency: 0.0233 +/- 0.0011
         1 tag resolved signal yield: 265.7266 +/-  49.1034 (   34.0 entries)    acceptance*efficiency: 0.0017 +/- 0.0003
         2 tag resolved signal yield: 488.6271 +/-  65.6297 (   60.0 entries)    acceptance*efficiency: 0.0030 +/- 0.0004
dmVZhadDM1MM10
         0 tag merged   signal yield: 332.4796 +/- 235.0986 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
         1 tag merged   signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         2 tag merged   signal yield: 691.5038 +/- 346.3014 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield: 4303.8352 +/- 1037.8786 (   20.0 entries)  acceptance*efficiency: 0.0010 +/- 0.0002
         1 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
WWxxDM1000
         0 tag merged   signal yield:   0.0015 +/-   0.0000 ( 9036.0 entries)    acceptance*efficiency: 0.4518 +/- 0.0048
         1 tag merged   signal yield:   0.0001 +/-   0.0000 (  618.0 entries)    acceptance*efficiency: 0.0309 +/- 0.0012
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (   12.0 entries)    acceptance*efficiency: 0.0006 +/- 0.0002
         0 tag resolved signal yield:   0.0002 +/-   0.0000 (  916.0 entries)    acceptance*efficiency: 0.0458 +/- 0.0015
         1 tag resolved signal yield:   0.0000 +/-   0.0000 (   30.0 entries)    acceptance*efficiency: 0.0015 +/- 0.0003
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
WWxxDM500
         0 tag merged   signal yield:   0.0090 +/-   0.0001 ( 8154.0 entries)    acceptance*efficiency: 0.4077 +/- 0.0045
         1 tag merged   signal yield:   0.0009 +/-   0.0000 (  726.0 entries)    acceptance*efficiency: 0.0363 +/- 0.0013
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (   12.0 entries)    acceptance*efficiency: 0.0006 +/- 0.0002
         0 tag resolved signal yield:   0.0018 +/-   0.0001 ( 1408.0 entries)    acceptance*efficiency: 0.0704 +/- 0.0019
         1 tag resolved signal yield:   0.0001 +/-   0.0000 (   64.0 entries)    acceptance*efficiency: 0.0032 +/- 0.0004
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (      0 entries)    acceptance*efficiency: 0.0000 +/- 0.0000
WWxxDM150
         0 tag merged   signal yield:   0.0268 +/-   0.0004 ( 7910.0 entries)    acceptance*efficiency: 0.3955 +/- 0.0044
         1 tag merged   signal yield:   0.0026 +/-   0.0001 (  672.0 entries)    acceptance*efficiency: 0.0336 +/- 0.0013
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (   10.0 entries)    acceptance*efficiency: 0.0005 +/- 0.0002
         0 tag resolved signal yield:   0.0073 +/-   0.0002 ( 1980.0 entries)    acceptance*efficiency: 0.0990 +/- 0.0022
         1 tag resolved signal yield:   0.0002 +/-   0.0000 (   62.0 entries)    acceptance*efficiency: 0.0031 +/- 0.0004
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
WWxxDM50
         0 tag merged   signal yield:   0.0304 +/-   0.0004 ( 7464.0 entries)    acceptance*efficiency: 0.3732 +/- 0.0043
         1 tag merged   signal yield:   0.0029 +/-   0.0001 (  592.0 entries)    acceptance*efficiency: 0.0296 +/- 0.0012
         2 tag merged   signal yield:   0.0001 +/-   0.0000 (   16.0 entries)    acceptance*efficiency: 0.0008 +/- 0.0002
         0 tag resolved signal yield:   0.0102 +/-   0.0003 ( 2282.0 entries)    acceptance*efficiency: 0.1141 +/- 0.0024
         1 tag resolved signal yield:   0.0005 +/-   0.0001 (   82.0 entries)    acceptance*efficiency: 0.0041 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    8.0 entries)    acceptance*efficiency: 0.0004 +/- 0.0001
WWxxDM10
         0 tag merged   signal yield:   0.0311 +/-   0.0004 ( 7290.0 entries)    acceptance*efficiency: 0.3645 +/- 0.0043
         1 tag merged   signal yield:   0.0027 +/-   0.0001 (  570.0 entries)    acceptance*efficiency: 0.0285 +/- 0.0012
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
         0 tag resolved signal yield:   0.0108 +/-   0.0003 ( 2314.0 entries)    acceptance*efficiency: 0.1157 +/- 0.0024
         1 tag resolved signal yield:   0.0005 +/-   0.0001 (   92.0 entries)    acceptance*efficiency: 0.0046 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    4.0 entries)    acceptance*efficiency: 0.0002 +/- 0.0001
WWxxDM1
         0 tag merged   signal yield:   0.0302 +/-   0.0004 ( 7002.0 entries)    acceptance*efficiency: 0.3501 +/- 0.0042
         1 tag merged   signal yield:   0.0028 +/-   0.0002 (  530.0 entries)    acceptance*efficiency: 0.0265 +/- 0.0012
         2 tag merged   signal yield:   0.0000 +/-   0.0000 (    8.0 entries)    acceptance*efficiency: 0.0004 +/- 0.0001
         0 tag resolved signal yield:   0.0103 +/-   0.0002 ( 2318.0 entries)    acceptance*efficiency: 0.1159 +/- 0.0024
         1 tag resolved signal yield:   0.0005 +/-   0.0001 (  100.0 entries)    acceptance*efficiency: 0.0050 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (    2.0 entries)    acceptance*efficiency: 0.0001 +/- 0.0001
ZZxxDM1000
         0 tag merged   signal yield:   0.0006 +/-   0.0000 ( 8036.0 entries)    acceptance*efficiency: 0.4018 +/- 0.0045
         1 tag merged   signal yield:   0.0001 +/-   0.0000 ( 1422.0 entries)    acceptance*efficiency: 0.0711 +/- 0.0019
         2 tag merged   signal yield:   0.0001 +/-   0.0000 (  814.0 entries)    acceptance*efficiency: 0.0407 +/- 0.0014
         0 tag resolved signal yield:   0.0001 +/-   0.0000 (  802.0 entries)    acceptance*efficiency: 0.0401 +/- 0.0014
         1 tag resolved signal yield:   0.0000 +/-   0.0000 (   94.0 entries)    acceptance*efficiency: 0.0047 +/- 0.0005
         2 tag resolved signal yield:   0.0000 +/-   0.0000 (  120.0 entries)    acceptance*efficiency: 0.0060 +/- 0.0005
ZZxxDM500
         0 tag merged   signal yield:   0.0035 +/-   0.0000 ( 7434.0 entries)    acceptance*efficiency: 0.3717 +/- 0.0043
         1 tag merged   signal yield:   0.0007 +/-   0.0000 ( 1396.0 entries)    acceptance*efficiency: 0.0698 +/- 0.0019
         2 tag merged   signal yield:   0.0005 +/-   0.0000 (  910.0 entries)    acceptance*efficiency: 0.0455 +/- 0.0015
         0 tag resolved signal yield:   0.0006 +/-   0.0000 ( 1182.0 entries)    acceptance*efficiency: 0.0591 +/- 0.0017
         1 tag resolved signal yield:   0.0001 +/-   0.0000 (  122.0 entries)    acceptance*efficiency: 0.0061 +/- 0.0006
         2 tag resolved signal yield:   0.0001 +/-   0.0000 (  176.0 entries)    acceptance*efficiency: 0.0088 +/- 0.0007
ZZxxDM150
         0 tag merged   signal yield:   0.0099 +/-   0.0001 ( 6982.0 entries)    acceptance*efficiency: 0.3491 +/- 0.0042
         1 tag merged   signal yield:   0.0016 +/-   0.0001 ( 1096.0 entries)    acceptance*efficiency: 0.0548 +/- 0.0017
         2 tag merged   signal yield:   0.0013 +/-   0.0001 (  922.0 entries)    acceptance*efficiency: 0.0461 +/- 0.0015
         0 tag resolved signal yield:   0.0022 +/-   0.0001 ( 1510.0 entries)    acceptance*efficiency: 0.0755 +/- 0.0019
         1 tag resolved signal yield:   0.0003 +/-   0.0000 (  170.0 entries)    acceptance*efficiency: 0.0085 +/- 0.0007
         2 tag resolved signal yield:   0.0004 +/-   0.0000 (  266.0 entries)    acceptance*efficiency: 0.0133 +/- 0.0008
ZZxxDM50
         0 tag merged   signal yield:   0.0114 +/-   0.0002 ( 6764.0 entries)    acceptance*efficiency: 0.3382 +/- 0.0041
         1 tag merged   signal yield:   0.0020 +/-   0.0001 ( 1058.0 entries)    acceptance*efficiency: 0.0529 +/- 0.0016
         2 tag merged   signal yield:   0.0018 +/-   0.0001 (  990.0 entries)    acceptance*efficiency: 0.0495 +/- 0.0016
         0 tag resolved signal yield:   0.0032 +/-   0.0001 ( 1744.0 entries)    acceptance*efficiency: 0.0872 +/- 0.0021
         1 tag resolved signal yield:   0.0004 +/-   0.0000 (  222.0 entries)    acceptance*efficiency: 0.0111 +/- 0.0007
         2 tag resolved signal yield:   0.0005 +/-   0.0000 (  262.0 entries)    acceptance*efficiency: 0.0131 +/- 0.0008
ZZxxDM10
         0 tag merged   signal yield:   0.0111 +/-   0.0002 ( 6316.0 entries)    acceptance*efficiency: 0.3158 +/- 0.0040
         1 tag merged   signal yield:   0.0020 +/-   0.0001 ( 1036.0 entries)    acceptance*efficiency: 0.0518 +/- 0.0016
         2 tag merged   signal yield:   0.0016 +/-   0.0001 (  870.0 entries)    acceptance*efficiency: 0.0435 +/- 0.0015
         0 tag resolved signal yield:   0.0034 +/-   0.0001 ( 1812.0 entries)    acceptance*efficiency: 0.0906 +/- 0.0021
         1 tag resolved signal yield:   0.0004 +/-   0.0000 (  192.0 entries)    acceptance*efficiency: 0.0096 +/- 0.0007
         2 tag resolved signal yield:   0.0006 +/-   0.0000 (  312.0 entries)    acceptance*efficiency: 0.0156 +/- 0.0009
ZZxxDM1
         0 tag merged   signal yield:   0.0112 +/-   0.0002 ( 6390.0 entries)    acceptance*efficiency: 0.3195 +/- 0.0040
         1 tag merged   signal yield:   0.0021 +/-   0.0001 ( 1082.0 entries)    acceptance*efficiency: 0.0541 +/- 0.0016
         2 tag merged   signal yield:   0.0018 +/-   0.0001 (  940.0 entries)    acceptance*efficiency: 0.0470 +/- 0.0015
         0 tag resolved signal yield:   0.0032 +/-   0.0001 ( 1742.0 entries)    acceptance*efficiency: 0.0871 +/- 0.0021
         1 tag resolved signal yield:   0.0003 +/-   0.0000 (  176.0 entries)    acceptance*efficiency: 0.0088 +/- 0.0007
         2 tag resolved signal yield:   0.0006 +/-   0.0000 (  306.0 entries)    acceptance*efficiency: 0.0153 +/- 0.0009
```


### Code for reproducing the results


<pre><code class="python">
"""
Script to print out the signal yields in different b-tagging categories for the mono-V run-2 2016/17 analysis

author: Philipp Gadow (pgadow@mpp.mpg.de)
"""

import ROOT
import math

# define input file here:
#input_file_name = "root://eosatlas.cern.ch//eos/atlas/atlascerngroupdisk/phys-exotics/jdm/monoV/Run2/hist_0lep.root"
input_file_name = "/ptmp/mpp/pgadow/monoV/Data_Output/sys0lep_v72_unblinded.root"

generated_events = 20000

# define helper functions:

def getHisto(file, name):
    return file.Get(name)

def getYield(file, name):
    if(file.GetListOfKeys().Contains(name)):
        h = getHisto(file, name)
        highcut = 1500
        lowcut = 150
        if 'merged' in name:
            lowcut = 250
        error  = ROOT.Double(0.)
        result = h.IntegralAndError(lowcut, highcut, error)
        raw    = h.GetEntries()
        acceptanceTimesEfficiency = raw / float(generated_events)
        acceptanceTimesEfficiencyError = math.sqrt(raw) / float(generated_events)

    else:
        error = 0
        result = 0
        raw = 0
        acceptanceTimesEfficiency = 0
        acceptanceTimesEfficiencyError = 0
    return result, error, raw, acceptanceTimesEfficiency, acceptanceTimesEfficiencyError

# define list of DM signals:

signalsWhad = [
    "dmVWhadDM1000MM1995",
    "dmVWhadDM1000MM1000",
    "dmVWhadDM1000MM10",

    "dmVWhadDM500MM10000",
    "dmVWhadDM500MM2000",
    "dmVWhadDM500MM995",
    "dmVWhadDM500MM10",

    "dmVWhadDM150MM1000",
    "dmVWhadDM150MM295",
    "dmVWhadDM150MM10",

    "dmVWhadDM50MM300",
    "dmVWhadDM50MM95",
    "dmVWhadDM50MM10",

    "dmVWhadDM10MM10000",
    "dmVWhadDM10MM100",
    "dmVWhadDM10MM10",

    "dmVWhadDM1MM2000",
    "dmVWhadDM1MM300",
    "dmVWhadDM1MM100",
    "dmVWhadDM1MM10"
]


signalsZhad = [
    "dmVZhadDM1000MM1995",
    "dmVZhadDM1000MM1000",
    "dmVZhadDM1000MM10",

    "dmVZhadDM500MM10000",
    "dmVZhadDM500MM2000",
    "dmVZhadDM500MM995",
    "dmVZhadDM500MM10",

    "dmVZhadDM150MM1000",
    "dmVZhadDM150MM295",
    "dmVZhadDM150MM10",

    "dmVZhadDM50MM300",
    "dmVZhadDM50MM95",
    "dmVZhadDM50MM10",

    "dmVZhadDM10MM10000",
    "dmVZhadDM10MM100",
    "dmVZhadDM10MM10",

    "dmVZhadDM1MM2000",
    "dmVZhadDM1MM300",
    "dmVZhadDM1MM100",
    "dmVZhadDM1MM10"
]

signalsEFT = [
    "WWxxDM1000",
    "WWxxDM500",
    "WWxxDM150",
    "WWxxDM50",
    "WWxxDM10",
    "WWxxDM1",
    "ZZxxDM1000",
    "ZZxxDM500",
    "ZZxxDM150",
    "ZZxxDM50",
    "ZZxxDM10",
    "ZZxxDM1"
]
signals = signalsWhad + signalsZhad + signalsEFT

# define analysis regions (signal regions):

regions = [
    ["_0tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isWZTagSubstrPassMassPass_merged_MET", "merged", 0],
    ["_1tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isWZTagSubstrPassMassPass_merged_MET", "merged", 1],
    ["_2tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isWZTagMassPass_merged_MET", "merged", 2],
    ["_0tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isMassPass_resolved_MET", "resolved", 0],
    ["_1tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isMassPass_resolved_MET", "resolved", 1],
    ["_2tag1pfat0pjet_0ptv_monoWZ_ZeroLepton_recycle_isMassPass_resolved_MET", "resolved", 2]
]

# process input file

input_file = ROOT.TFile.Open(input_file_name)
print "loaded input file: {}".format(input_file_name)

low_yield_signals = {}
no_yield_signals = {}
for signal in signals:
    for region, topology, tag in regions:
        histname = signal + region

        yield_number, yield_error, yield_raw, acceff, acceffError = getYield(input_file, histname)
        # output information
        if tag == 0 and topology == "merged":
            print "checking", signal
        print "\t {0} tag {1:8} signal yield: {2:8.4f} +/- {3:8.4f} ({4:7} entries) \t acceptance*efficiency: {5:.4f} +/- {6:.4f}".format(tag, topology, yield_number, yield_error, yield_raw, acceff, acceffError)
        if yield_number < 0.001 and signal not in low_yield_signals.keys():
            low_yield_signals[signal] = yield_number
        if (yield_number == 0 or yield_raw == 0) and signal not in no_yield_signals.keys():
            no_yield_signals[signal] = yield_number

print "list of samples with less than 0.001 yield in one or more analysis categories"
for signal in sorted(low_yield_signals):
    print '*', signal, ':', low_yield_signals[signal]

print "list of samples with no entries in one or more analysis categories"
for signal in sorted(no_yield_signals):
    print '*', signal, ':', no_yield_signals[signal]
</code class="python"></pre>
