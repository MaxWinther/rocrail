
## Trackplan

### Sensors

**Setup**
Sensors are mapped to mXion in the interface tab setting the follwing
- `Interface ID` to md
- `Node ID` aka `Bus` for Z21 protocol to 1 which actually stands for responses comming from LocoNet
- `Address` is set to the programmed address in mXion plus 1

**Usage**

From tables below in phase 1, isolators 31 and 21
- Main station 6 and 4
- Lake station 6 and 4
- Driweway station 6 and 4
- Main line 13 and 9

From tables below in phase 2, isolators 20 and 14
- Main station 16 and 11
- Main line 4 and 3

Feedback modules
1. Main station; block track 1 and track 2. Main line block to Terrase switch, and one sensor in block Lake to Terrase switch. One free sensor
2. Lake station; block track 1 and track 2. Main Line switch to Lake, and two sensors in block Lake to Terrase switch.  No free sensors.
3. Driveway; blocks and sideways on station plus single main line block. No free sensors


| Station | Track | Block | Isolartor | Sensor | Phase | FB       |
|---------|-------|-------|-----------|--------|-------|----------|
| Main    | 1     |       | 3         | 2      | 1     | 1A 1B    |
|         | 2     |       | 3         | 2      | 1     | 1C 2D    |
|         | 3     |       | 4         | 3      | 2     |          |
|         | 4N    |       | 3         | 2      | 2     |          |
|         | 4S    |       | 3         | 2      | 2     |          |
|         | 5N    |       | 3         | 2      | 2     |          |
|         | 5N    |       | 3         | 2      | 2     |          |
| Total   |       |       | 6         | 4      | 1     |          |
|         |       |       | 16        | 11     | 2     |          |


| Station | Track | Block | Isolartor | Sensor | Phase | FB       |
|---------|-------|-------|-----------|--------|-------|----------|
| Lake    | 1     |       | 3         | 2      | 1     | 2A 2B    |
|         | 2     |       | 3         | 2      | 1     | 2C 2D    |
| Total   |       |       | 6         | 4      | 1     |          |


| Station | Track | Block | Isolartor | Sensor | Phase |FB        |
|---------|-------|-------|-----------|--------|-------|----------|
| Driveway| 1     |       | 3         | 2      | 1     | 3A 3B    |
|         | 2     |       | 1         | 1      | 3     | 3G       |
|         | 3     |       | 3         | 2      | 1     | 3C 3D    |
|         | 4     |       | 1         | 1      | 3     | 3H       |
| Total   |       |       | 6         | 4      | 1     |          |


| From    | To      | Block   | Isolartor | Sensor | Phase |FB        |
|---------|--------|----------|-----------|--------|-------|----------|
| Main    | Ter.sw | bkHspHe  | 3         | 2      | 1     | 1E 1F    |
| Ter.sw  | Lake   | bkspHLn  | 4         | 3      | 1     | 2G 2H 1G |
| Driveway| Switch | bkIspHn  | 3         | 2      | 1     | 3E 3F    |
| Switch  | Lake   | bkspHInw | 3         | 2      | 1     | 2E 2F    |
| Main    | Ter.sw | bkHspHs  | 4         | 3      | 2     |          |
| Total   |        |          | 13        | 9      | 1     |          |


## rocrail.ini


### Set up mXion

The property
- `xnetgbm` enables feedback via Loconet
- `host` ip-address of CS mXion; Upladsgade 10.76.215.157, Sommerhus 192.168.8.197
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

```
<webclient 
    port="8081" 
    webpath="web" 
    imgpath="images" 
    svgpath1=svg/themes/SpDrS60" 
    svgpath2="." 
    svgpath3="." 
    svgpath4="." 
    svgpath5=".">
    <rocweb/>
</webclient>
```

**Raspberry Pi**

Symbolic links in working directory
- web ln -s /home/pi/Rocrail/web web
- svg ln -s /home/pi/Rocrail/svg svg

**MacOS**

Symbolic links created by installation
