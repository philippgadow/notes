
## Z tagger


```python
import numpy as np
import matplotlib.pyplot as plt
```


```python
%matplotlib inline
```


```python
pt = np.arange(200.0, 2700.0)
```


```python
def lowercut_z_mass(pt):
    #if pt > 2500:
    #    return 69.4240299485
    return np.sqrt(np.power((-8911.32152025)/pt-(-72.3863305346),2)+np.power((0.0232216747865)*pt+(-67.1786329156),2))
def uppercut_z_mass(pt):
    #if pt > 2500:
    #    return 109.831901054
    return np.sqrt(np.power((428.215902774)/pt-(-105.538285882),2)+np.power((0.0192931557406)*pt+(-18.4246216168),2))

def uppercut_z_d2(pt):
    # if pt > 2500:
    #    return 1.90713763304
    return (0.86245030986)+(0.0010301169875)*pt+(-6.37151804335e-07)*np.power(pt,2.0)+(2.95602462111e-10)*np.power(pt,3.0)+(-5.54801878773e-14)*np.power(pt,4.0)
```


```python
plt.figure(1)
plt.subplot(311)
plt.title('$Z$ tagger mass + substructure window')
plt.xlabel('pt [GeV]')
plt.ylabel('upper masscut  [GeV]')
plt.plot(pt, uppercut_z_mass(pt), 'r--')

plt.subplot(312)
plt.xlabel('pt [GeV]')
plt.ylabel('lower mass cut [GeV]')
plt.plot(pt, lowercut_z_mass(pt), 'b--')

plt.subplot(313)
plt.xlabel('pt [GeV]')
plt.ylabel('upper D2 cut')
plt.plot(pt, uppercut_z_d2(pt), 'g--')
plt.show()
```


![png](http://pgadow.web.cern.ch/pgadow/notes/content/2017-07-25-taggermasswindows/output_5_0.png)


## W tagger


```python
def lowercut_w_mass(pt):
    #if pt > 2500:
    #    return  60.0593267161
    return np.sqrt(np.power((-8680.2717943)/pt-(-54.2916959506),2)+np.power((0.0142530985867)*pt+(-67.640437403),2))
def uppercut_w_mass(pt):
    #if pt > 2500:
    #    return 99.824544933
    return np.sqrt(np.power((79.4993903251)/pt-(-94.0432300643),2)+np.power((0.0201350277197)*pt+(-16.9485211641),2))
def uppercut_w_d2(pt):
    # if pt > 2500:
    #    return 2.01439576478
    return (0.827098899953)+(0.00117390855197)*pt+(-7.27657125295e-07)*np.power(pt,2.0)+(3.46942900597e-10)*np.power(pt,3.0)+(-6.7087367778e-14)*np.power(pt,4.0)
```


```python
plt.figure(1)
plt.subplot(311)
plt.title('$W$ tagger mass + substructure window')
plt.xlabel('pt [GeV]')
plt.ylabel('upper masscut  [GeV]')
plt.plot(pt, uppercut_w_mass(pt), 'r--')

plt.subplot(312)
plt.xlabel('pt [GeV]')
plt.ylabel('lower mass cut [GeV]')
plt.plot(pt, lowercut_w_mass(pt), 'b--')

plt.subplot(313)
plt.xlabel('pt [GeV]')
plt.ylabel('upper D2 cut')
plt.plot(pt, uppercut_w_d2(pt), 'g--')
plt.show()
```


![png](http://pgadow.web.cern.ch/pgadow/notes/content/2017-07-25-taggermasswindows/output_8_0.png)



```python

```
