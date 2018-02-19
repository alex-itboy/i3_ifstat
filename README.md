### Why do I need this
I modified this program used to show the network speed on my i3wm status bar.
All it does is showing the current network speed and exit. So you need to use other
programs to constantly call it and show it to the status bar. For me I use i3pystatus.

### Usage
`i3_ifstat -i enp0s31f6`
which is 
`i3_ifstat -i <interface>`

To check out interfaces, use

On my i3pystatus setup
```python
#Network speed
wlan_interface = r"wlp4s0"
eth_interface = r"enp0s31f6"
wlan_str = r"/home/alex/.config/i3/i3_ifstat -i " + wlan_interface
eth_str = r"/home/alex/.config/i3/i3_ifstat -i " + eth_interface
show_wlan = True

if show_wlan:
	status.register("shell",
		command=wlan_str,
		format="[W|{output}]",
		interval=1,
	)
else:
	status.register("shell",
		command=eth_str,
		format="[E|{output}]",
		interval=1,
	)
```

and you can just `./configure`, `make` then put the `ifstat` execute file to `/home/yours/.config/i3/i3_ifstat`

### Something else
Actually， all I do is slightly change the way it output its data. Default delay is 990ms.(because I run it every second)

There is a shell script to achieve the same goal from Archlinux Wiki.[Link](https://wiki.archlinux.org/index.php/i3#Network_Download.2FUpload_speed_in_statusbar)
But I am good with ifstat.
