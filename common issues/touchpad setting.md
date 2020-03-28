# change touchpad speed through command.

#### 1.list all device id
```
xinput --list
```

#### 2.list particular device setting options
```
xinput --list-props 14

Device 'Elan Touchpad':
	Device Enabled (169):	1
	Coordinate Transformation Matrix (171):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	libinput Tapping Enabled (323):	1
	libinput Tapping Enabled Default (324):	0
	libinput Tapping Drag Enabled (325):	1

```

##### 3.increase the trackpad tracking speed ( increase it by 4 times )
```
xinput --set-prop 14 171 4.000000, 0.000000, 0.000000, 0.000000, 4.000000, 0.000000, 0.000000, 0.000000, 1.000000
```

#### 4.decrease scrolling speed
```
    Synaptics Scrolling Distance (301):	-75, 75
xinput --set-prop 10 301 -75, 75
```