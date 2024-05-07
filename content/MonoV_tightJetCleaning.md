## Mono-V Tight Jet Cleaning

03.05.2017 - Paul.Philipp.Gadow@cern.ch

#### Introduction

To test the tight jet cleaning, all CxAOD files have to be reproduced with the CxAOD Maker, where the tight jet cleaning flag is passed to each jet.


#### Disclaimer

UPDATE: It seems that the jet cleaning is not as easy to implement as suggested in first place.

For details visit: https://its.cern.ch/jira/browse/CXAOD-339

The jet cleaning documented here follows the suggestion in the initial ticket written by Sam Meehan. The discussion below suggests that jet cleaning should be written out as an event based flag and not as an additional decorator for jets as it is done in this implementation at the moment.

The way suggested by Nicholas Morange is not implemented yet and following the procedure below will only give the tight jet cleaning which follows the initial suggestion reported by Sam Meehan.

#### How-To

In a new lxplus session enter:

```mkdir CxAODFramework-00-26-01```

```cd CxAODFramework-00-26-01```

```git clone https://:@gitlab.cern.ch:8443/CxAODFramework/FrameworkSub.git```

```git checkout r26-01```

```cd ..```

```source FrameworkSub/bootstrap/setup-tag.sh```

Then follow all steps and prompt your password as the script requests. You should then have a working environment for production of v26-01 CxAODs.

Now check that everything compiles and that you can submit a test job locally by

```hsg5framework```

To implement tight jet cleaning, you should enter the following commands to the terminal:

```rm -rf CxAODMaker```

```git clone https://:@gitlab.cern.ch:8443/pgadow/CxAODMaker.git```

```cd CxAODMaker```

```git checkout tightJetCleaning```

```cd ..```

```rm -rf CxAODTools```

```git clone https://:@gitlab.cern.ch:8443/pgadow/CxAODTools.git```

```cd CxAODTools```

```git checkout tightJetCleaning```

```cd ..```

```rc clean```

```rc find_packages```

```rc compile```


Now you have a working setup to produce v26 CxAODs with tight jet cleaning enabled.