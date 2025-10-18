- No program has direct access to the keyboard, mouse, display device, speaker, disk, memory, or any system hardware.
- Programs rely on the services provided by the operating system (OS) to utilize hardware.
- We can think of the OS as a layer of software imposed between the hardware and whatever program is currently running.
	- **ALL** attempts made by an application to manipulate hardware **MUST** go through the system.
![[Layered View of a Computer System.png]]
- The OS has 2 main purposes:
	1. To protect the hardware from misuse by runaway applications.
	2. To provide applications with simple and uniform (standard) mechanisms for manipulating complicated and different low-level hardware devices.
		- Think about it: every PC running windows can run a .exe file however each one of those PCs have different hardware specifications, the Windows OS allows for standardization which lets the programs actually run on the OS.
			- This is also why Windows programs cannot run on MacOS and vice versa, they are applications targeting the different specifications of different OSes.
	- The OS achieves these goals via [[Processes|processes]], [[Virtual Memory|virtual memory]], [[Threads|threads]], and [[Files|files]].
	![[Abstractions provided by an OS.png]]