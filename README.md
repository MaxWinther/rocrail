
## Trackplan

### Sensors

**Setup**
Sensors are mapped to mXion in the interface tab setting the follwing
- `Interface ID` to md
- `Node ID` aka `Bus` for Z21 protocol to 1 which actually stands for responses comming from LocoNet
- `Address` is set to the programmed address in mXion plus 1

## rocrail.ini

### Set up mXion

The property
- `xnetgbm` enables feedback via Loconet
- `host` ip-address of CS mXion
- `libpath` actual path to drivers in the rocrail install

**MacOS**
```
<digint lib="z21" iid="md" port="21105" uid="0" 
    host="10.76.215.157" locolist="false" absent="false" xnetgbm="true" swtime="250" protver="0" desc="mXion" 
    ignorepowercmds="true" 
    ignorepoweroffonghost="false" 
    show="true" swapgates="false" stress="false" guid="0000ACDE480020210303160626126000" 
    libpath="/Applications/Rocrail.app/Contents/MacOS"/>
```


### Set up webclient

**Raspberry Pi**

```
<webclient 
    port="8081" 
    webpath="/opt/rocrail/web" 
    imgpath="/opt/rocrail/web" 
    svgpath1="/opt/rocrail/svg/themes/SpDrS60" 
    svgpath2="." 
    svgpath3="." 
    svgpath4="." 
    svgpath5=".">
    <rocweb/>
</webclient>
```

**MacOS**
```
<webclient 
    port="8081" 
    webpath="/Applications/Rocrail.app/Contents/rocdata/web" 
    imgpath="/Applications/Rocrail.app/Contents/rocdata/images" 
    svgpath1="/Applications/Rocrail.app/Contents/rocdata/svg/themes/SpDrS60" 
    svgpath2="." 
    svgpath3="." 
    svgpath4="." 
    svgpath5="."
    <rocweb/>
</webclient>
```
