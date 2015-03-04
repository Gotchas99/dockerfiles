vnc
===
Ubuntu Core 14.04 + CUDA 6.5.19 + LXDE desktop + Firefox browser with a TightVNC server. Requires the host has the corresponding CUDA drivers installed for the kernel module. Runs as a daemon by default by using tail. 

Build
-----
Include password.txt with the password for TightVNC (by default this is "password"). This must be at least 8 characters.

Usage
-----
The container must have all NVIDIA devices attached to it for CUDA to work properly.
Therefore the command will be as such: `docker run -dP --device /dev/nvidiactl:/dev/nvidiactl --device /dev/nvidia-uvm:/dev/nvidia-uvm --device /dev/nvidia0:/dev/nvidia0 kaixhin/cuda-vnc`.
With 4 GPUs this would also have to include `--device /dev/nvidia1:/dev/nvidia1 --device /dev/nvidia2:/dev/nvidia2 --device /dev/nvidia3:/dev/nvidia3`.

For automatically mapping a VNC port use `docker run -dP kaixhin/cuda-vnc` and `docker port <id>` to retrieve the port.
For specifying the port manually use `docker run -d -p <port>:5901 kaixhin/cuda-vnc`.
The shell can be entered as usual using `docker run -it kaixhin/cuda-vnc bash`.