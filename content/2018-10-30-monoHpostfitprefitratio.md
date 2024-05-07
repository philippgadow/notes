## ATLAS-CONF-2018-039 postfit prefit yields

```
ttbar + single top: Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.01  (postfit: 11796.86 / prefit: 11665.61)
ttbar + single top: Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.96  (postfit: 6450.18 / prefit: 6736.43)
ttbar + single top: Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.97  (postfit: 307.60 / prefit: 315.92)
ttbar + single top: Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR -> 0.77  (postfit: 10.80 / prefit: 14.09)
ttbar + single top: 0.99  (postfit in \sum_all regions: 18565.44 / prefit in \sum_SR: 18732.05)
diboson: Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.97  (postfit: 438.35 / prefit: 450.89)
diboson: Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.92  (postfit: 399.62 / prefit: 435.32)
diboson: Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.94  (postfit: 48.98 / prefit: 52.34)
diboson: Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR -> 0.90  (postfit: 9.37 / prefit: 10.40)
diboson: 0.94  (postfit in \sum_all regions: 896.33 / prefit in \sum_SR: 948.95)
W + jets: Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.54  (postfit: 3023.56 / prefit: 1957.12)
W + jets: Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.39  (postfit: 2237.96 / prefit: 1610.87)
W + jets: Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.27  (postfit: 183.63 / prefit: 144.68)
W + jets: Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR -> 1.18  (postfit: 26.38 / prefit: 22.27)
W + jets: 1.46  (postfit in \sum_all regions: 5471.52 / prefit in \sum_SR: 3734.95)
Z + jets: Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.40  (postfit: 6333.38 / prefit: 4513.93)
Z + jets: Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.35  (postfit: 5176.41 / prefit: 3844.07)
Z + jets: Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 1.35  (postfit: 564.95 / prefit: 418.53)
Z + jets: Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR -> 1.34  (postfit: 80.51 / prefit: 60.15)
Z + jets: 1.38  (postfit in \sum_all regions: 12155.25 / prefit in \sum_SR: 8836.68)
VHbb: Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.96  (postfit: 136.33 / prefit: 141.99)
VHbb: Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.92  (postfit: 129.30 / prefit: 140.92)
VHbb: Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR -> 0.93  (postfit: 17.26 / prefit: 18.60)
VHbb: Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR -> 0.93  (postfit: 3.86 / prefit: 4.14)
VHbb: 0.94  (postfit in \sum_all regions: 286.75 / prefit in \sum_SR: 305.65)
```

### Code used to produce these numbers

```
#!/bin/env python
import csv
import math
from argparse import ArgumentParser


def getArgs():
    """Get arguments from command line."""
    parser = ArgumentParser()
    parser.add_argument("inputFilePostFit")
    parser.add_argument("inputFilePreFit")

    return parser.parse_args()


def readData(inputFile):
    """Read data from csv file."""
    data = {}
    with open(inputFile, 'rb') as csvfile:
        reader = csv.reader(csvfile, delimiter=',')
        # structure of row: region,sample,yield,uncertainty
        for row in reader:
            if row[1] not in data:
                data[row[1]] = {}
            try:
                data[row[1]][row[0]] = [float(row[2]), float(row[3])]
            except Exception:
                data[row[1]][row[0]] = [float(0.), float(0.)]
    return data


def getSumForBackgrounds(data, backgrounds, regions):
    """Sum different flavours for V+jets processes."""
    evt_yield = 0.
    for bg in backgrounds:
        for r in regions:
            evt_yield += data[bg][r][0]
    return evt_yield


def main():
    """For a group of background physics processes iterate over specified histograms in ROOT input file and print out LaTeX table with yield and statistical uncertainty."""

    args = getArgs()
    data_postfit = readData(args.inputFilePostFit)
    data_prefit = readData(args.inputFilePreFit)

    r = ""

    regions = [
        "Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR",
        "Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR",
        "Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR",
        "Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR"
        # "Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1",
        # "Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1",
        # "Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1",
        # "Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1",
        # "Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2",
        # "Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2",
        # "Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2",
        # "Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2"
    ]

    backgrounds = [
        ['ttbar + single top', ['ttbar', 'stop']],
        ['diboson', ['diboson']],
        ['W + jets', ['Wl', 'Wcl', 'Whf']],
        ['Z + jets', ['Zl', 'Zcl', 'Zhf']],
        ['VHbb', ['VHbb']]
    ]

    for name, background in backgrounds:
        ratio = 0.
        summedyield_prefit = 0.
        summedyield_postfit = 0.
        for region in regions:
            y_prefit = getSumForBackgrounds(data_prefit, background, [region])
            summedyield_prefit += y_prefit

            y_postfit = getSumForBackgrounds(data_postfit, background, [region])
            summedyield_postfit += y_postfit
            ratio_in_region = -1.
            try:
                ratio_in_region = y_postfit / y_prefit
            except Exception:
                print("no prefit")
            print("{name}: {region} -> {ratio:.2f}  (postfit: {postfit:.2f} / prefit: {prefit:.2f})".format(name=name, region=region, ratio=ratio_in_region, postfit=y_postfit, prefit=y_prefit))

        if summedyield_prefit == 0:
            continue

        ratio = summedyield_postfit / summedyield_prefit
        print("{name}: {ratio:.2f}  (postfit in \sum_all regions: {postfit:.2f} / prefit in \sum_SR: {prefit:.2f})".format(name=name, ratio=ratio, postfit=summedyield_postfit, prefit=summedyield_prefit))
        # print("{name}: {ratio:.2f}  (postfit in \sum_CR: {postfit:.2f} / prefit in \sum_CR: {prefit:.2f})".format(name=name, ratio=ratio, postfit=summedyield_postfit, prefit=summedyield_prefit))


if __name__ == '__main__':
    main()
```

### Postfit yields

```
$ cat data/yields_postfit_conditional_mu0.csv 
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,98.1186864292,58.1212291226
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,122.187881353,48.7407947798
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,6113.07485181,446.861866898
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,76.5943237832,35.9629529714
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,131.263713059,49.2695978937
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,2815.69873432,526.067452814
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,928.850572669,83.3899319548
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,10868.0083462,339.523737705
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,438.352045547,67.1489817571
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,136.327412684,38.8325641151
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,21728.4765678,137.510693428
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,235.78315147,41.6981800429
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,0.0108513429708,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),1.59094249755,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,21818.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,235.78315147,41.6981800429
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,8.93839536771,5.23794216582
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,6.33328154071,2.59978189461
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,240.374012975,13.4881210604
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,78.3956647269,45.9999280694
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,214.881404853,83.9955183921
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,3608.30353507,542.076480398
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,2924.81056072,272.022592764
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,26344.8027157,656.941367423
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,225.74674197,49.9777104731
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,78.8718847954,22.467616609
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,33731.4581977,179.612062629
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,33706.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,18.8539166526,10.7381473954
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,32.6433684713,12.6999935815
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,1637.31292207,47.5248876759
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,2.59313934056,0.427379690936
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,15.2269939844,1.73292883043
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,155.694764118,9.22717904201
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,86.1772177763,14.5081753208
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,33.6321677245,9.56984130048
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,1982.13449014,38.3788937821
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,1897.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,70.5210208099,41.8999379396
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,102.967879273,40.5660855143
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,5002.91903063,338.317650321
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,48.3334073994,27.3480632435
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,73.8583462732,28.3065624405
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,2115.76387835,356.888762729
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,587.489591777,51.632818703
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,5862.68759489,190.329582644
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,399.618868677,59.1662757896
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,129.299423539,36.9118026638
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,14393.4590416,110.226425814
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,4025.83758212,327.155090058
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,0.279699102939,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),29.6633180903,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,14350.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,4025.83758212,327.155090058
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,3.12058903684,1.92235474704
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,4.93803804285,1.93446007342
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,148.852979157,9.75601320834
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,96.5064152818,56.4297122796
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,164.423015931,62.7894603364
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,3134.96596494,403.718012009
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,2305.21611861,188.63903282
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,14581.1090751,433.197044614
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,216.59959609,47.6525930837
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,81.7317301952,23.3401167016
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,20737.4635224,136.650687882
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,20728.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,16.0546168492,9.36582497216
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,21.4975174029,8.31993263133
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,1250.87774139,37.2518225976
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,1.24296783427,0.244735596165
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,6.98882911432,0.942105878874
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,46.1895864618,4.41263710468
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,75.965938526,12.4113751149
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,31.1773228506,8.87255953768
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,1449.99452043,28.6093912953
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,1533.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,9.36005715657,5.35215156437
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,18.5584095373,7.21339804561
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,537.035725123,36.1058155805
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,4.14199389394,2.27004052987
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,7.35170581578,2.97228346144
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,172.135883678,31.631245056
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,43.3204961735,12.5880390676
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,264.284418781,21.4906424255
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,48.9846957757,11.2014794791
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,17.2632194865,4.94969046957
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,1122.43660542,25.271964013
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,13078.6563887,904.61052227
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,11.6520223285,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),109.749422627,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,1128.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,13078.6563887,904.61052227
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,0.159471636397,0.0912407629266
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,0.829248859972,0.416577095965
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,12.2310214513,0.858588423157
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,8.1148715965,4.51535630032
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,25.3682404878,9.78165245343
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,422.052113248,64.9339127071
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,273.934629104,85.6874374589
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,858.778237018,69.5725934256
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,28.7290688342,6.68543811051
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,13.6574347659,3.9236326595
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,1643.854337,35.5037126164
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,1641.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,2.20296322371,1.30463557862
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,5.11764730304,2.05847211683
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,153.89511619,7.24175440252
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0292289043249,0.0157957997427
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,0.0176816293683,0.00581726223153
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,0.381669937611,0.193211000403
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,0.910557073218,0.298225436597
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,9.75989036653,1.61463180334
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,4.47059853254,1.27906101625
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,176.785353161,6.9469458302
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,173.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zl,4.36717250544,0.700535826835
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zcl,3.17519232724,1.62043341467
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zhf,72.9668807196,6.07324608892
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Wl,0.569602091053,0.264593647423
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Wcl,2.07230255522,1.41435230814
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Whf,23.7366855478,5.47946655326
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,stop,2.92970335206,1.98379048298
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,ttbar,7.87165768918,1.55880206596
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,diboson,9.36977095572,1.72402693532
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,VHbb,3.85782514697,1.117578396
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Bkg,130.91679289,7.15837248801
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Signal,10226.5530729,710.112777943
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,S/B,78.1149067825,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),100.485277766,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,data,119.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,zp2hdm,10226.5530729,710.112777943
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zl,0.251747489581,0.0490925185756
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zcl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zhf,0.833641743133,0.100474954537
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Wl,3.65887309023,0.945976436968
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Wcl,5.02383861807,2.56014283067
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Whf,71.0974709497,13.7771629784
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,stop,17.3785085597,12.378129402
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,ttbar,38.3427830002,6.34679371394
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,diboson,5.96477719758,1.45519954143
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,VHbb,3.65035610178,1.06150807304
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Bkg,146.20199675,9.27303434215
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,data,152.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zl,1.95176993865,0.273271981396
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zcl,1.13551644993,0.581365178946
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zhf,22.1901971364,1.75954037196
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Whf,0.0214425630666,0.00759324502924
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,stop,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,ttbar,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,diboson,3.20408049481,0.575629296302
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,VHbb,1.20876537365,0.350713906118
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Bkg,29.7117719565,2.1651610052
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,data,26.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
```

### Prefit yields

```
$ cat data/yields_prefit.csv 
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,108.495991131,82.2509580996
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,140.694660377,67.3208755373
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,4264.74413657,792.803955312
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,105.692075193,64.895600852
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,142.440050285,66.4883913257
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,1708.99153846,323.655841671
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,979.393122692,124.158481084
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,10686.2198535,832.019596411
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,450.892921187,82.3075957116
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,141.987716548,43.5671121414
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,18729.552066,1716.48681687
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,223.902055044,43.4229847404
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,0.0119544799713,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),1.62634955624,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,21818.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,223.902055044,43.4229847404
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,11.7285220272,8.97148005822
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,7.01632533907,3.56890598317
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,184.806429269,17.9387035324
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,100.799165043,75.7118414295
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,252.768277869,121.524865951
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,2557.36738666,295.366826532
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,2872.12337695,440.54244786
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,25954.8423416,1964.47971053
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,235.414783916,55.8791121579
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,81.1902691523,24.9146223277
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,32258.0568778,2498.03537768
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,33706.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,23.1861627946,16.9749151382
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,39.0034299642,18.5033315995
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,1279.50884789,98.6370205526
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,2.1141631435,0.315966709219
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,15.4698296754,2.39222801474
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,151.858174735,10.8652883645
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,91.1044471931,17.9613793778
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,34.8645599431,10.6941816335
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,1637.10961534,131.677254879
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,1897.0,0
Region_BMax200_BMin150_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,98.8944851707,74.9162933359
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,133.606807322,65.2020308006
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,3611.57298198,678.425773761
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,72.8158586818,53.6258090187
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,102.172808687,49.311979761
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,1435.8854523,272.720370786
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,681.306133761,82.167987689
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,6055.12341711,630.834883808
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,435.324399442,77.6977130707
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,140.920525518,43.5406286941
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,12767.62287,1439.97321443
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,4015.40826799,388.466408394
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,0.314499285332,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),30.9952046891,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,14350.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,4015.40826799,388.466408394
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,4.41369238433,3.45867364166
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,4.95772495237,2.40997990044
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,121.75439892,13.6847975193
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,113.499423511,85.6811188025
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,209.705625165,101.154794396
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,2397.17978329,235.082551146
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,2610.25543241,272.638159246
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,15082.4739337,1461.80158421
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,228.986571885,54.3371726282
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,88.2768672225,27.1869586042
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,20861.5034535,1950.92708332
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,20728.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,19.6307640648,14.5770163834
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,25.9003946888,12.2959154412
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,932.414355556,66.5906612639
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,0.867195935584,0.154820422196
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,8.58612172048,2.26316198376
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,41.8285278742,3.74960883206
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,76.7213915994,14.6651979335
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,32.2227690669,9.85235778259
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,1138.17152051,87.7958083988
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,1533.0,0
Region_BMax350_BMin200_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zl,11.9767157522,8.85511803616
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zcl,21.9417333612,10.5547860533
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Zhf,384.60908008,74.8175389175
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wl,5.71048487263,4.31379476918
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Wcl,12.0324477597,6.79471096423
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Whf,126.941454444,40.7799446757
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,stop,62.0513556384,31.396198168
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,ttbar,253.865611813,33.9608997431
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,diboson,52.336747276,13.9803763112
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,VHbb,18.5998537319,5.76792140409
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Bkg,950.065484729,130.311195144
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,Signal,13171.2467845,1062.42777166
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/B,13.8635146695,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),110.838173036,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,data,1128.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L0_Y2015_distmBB_DSR,zp2hdm,13171.2467845,1062.42777166
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zl,0.244087318901,0.213543724958
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zcl,0.670785155576,0.435660184817
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Zhf,9.16153382131,1.12568246452
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wl,12.625471492,9.72802415541
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Wcl,35.9347313377,19.4345893337
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Whf,347.951864974,87.703333896
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,stop,418.533956438,212.489846626
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,ttbar,854.583739191,124.242435165
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,diboson,30.6353059623,7.76082160482
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,VHbb,14.6891661034,4.54908642317
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Bkg,1725.03064179,291.865330944
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,data,1641.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zl,2.26831209751,1.74753297446
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zcl,5.91809246368,2.88493899434
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Zhf,112.938193433,10.391177484
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wl,0.0349349331012,0.0243343847815
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Whf,0.0152639434021,0.00857147297986
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,stop,0.684926143656,0.516033276981
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,ttbar,0.931912391269,0.379231219626
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,diboson,9.81154325016,1.87752915719
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,VHbb,4.5864029231,1.40740583301
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Bkg,137.189581578,13.4333181727
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,data,173.0,0
Region_BMax500_BMin350_incFat1_Fat0_incJet1_J2_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zl,4.2426423585,0.820815049895
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zcl,3.97088763998,2.66106920055
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Zhf,51.9339886323,11.0537647685
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Wl,0.92278829961,0.518251200181
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Wcl,3.33012967658,3.38305606892
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Whf,18.0168843435,7.27297154505
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,stop,6.84181876909,5.60144327631
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,ttbar,7.2513158516,1.96890848042
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,diboson,10.4005703697,2.34417859034
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,VHbb,4.14356985831,1.28532968479
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Bkg,111.054595799,20.1066926934
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,Signal,11152.0808973,919.916754833
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,S/B,100.419805386,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,S/sqrt(S+B),105.081498375,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,data,119.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L0_Y2015_distmBB_DSR,zp2hdm,11152.0808973,919.916754833
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zl,0.229011682213,0.050709363103
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zcl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Zhf,0.564811715665,0.093532318025
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Wl,4.58560383347,1.79661536171
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Wcl,6.5016407781,4.8701498397
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Whf,59.3845442854,21.6813160127
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,stop,36.4867314703,29.1166323689
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,ttbar,38.5667929237,11.2333255066
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,diboson,6.03316344096,1.81197005135
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,VHbb,3.84641124509,1.1957424017
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Bkg,156.198711375,44.5368036278
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,Signal,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,S/B,0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,S/sqrt(S+B),0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,data,152.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L1_Y2015_distCharge_DCR1,zp2hdm,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zl,1.7864063253,0.278736212393
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zcl,1.37883606499,0.925033766128
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Zhf,15.6261939991,2.12739625188
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Wl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Wcl,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Whf,0.0164188578438,0.00701166841741
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,stop,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,ttbar,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,diboson,3.279896765,0.679659978932
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,VHbb,1.22493193735,0.378626099865
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Bkg,23.3126839495,3.17151102596
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,Signal,0.0,0.0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,S/B,0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,S/sqrt(S+B),0.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,data,26.0,0
Region_BMin500_incFat1_Fat1_incJet1_J0_T2_L2_Y2015_distmBB_DCR2,zp2hdm,0.0,0.0
```
