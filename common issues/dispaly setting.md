dispaly setting
======================

xrandr 
---
* xrandr : to show all display device and info
* xrandr --output VGA --same-as LVDS --auto        	    打开外接显示器(--auto:最高分辨率)，与笔记本液晶屏幕显示同样内容（克隆）
* xrandr --output VGA --same-as LVDS --mode 1280x1024   打开外接显示器(分辨率为1280x1024)，与笔记本液晶屏幕显示同样内容（克隆）
* xrandr --output VGA --right-of LVDS --auto       	    打开外接显示器(--auto:最高分辨率)，设置为右侧扩展屏幕
* xrandr --output VGA --off         					关闭外接显示器
* xrandr --output VGA --auto --output LVDS --off        打开外接显示器，同时关闭笔记本液晶屏幕（只用外接显示器工作）
* xrandr --output VGA --off --output LVDS --auto        关闭外接显示器，同时打开笔记本液晶屏幕 （只用笔记本液晶屏）
