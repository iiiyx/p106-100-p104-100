__REMEMBER__: to make it work you must have at least 4-th generation Intel Core CPU with integrated video. Also you must certainly enable iGPU at BIOS (32-64 MB will be enough). And I don't know the way how to start OpenGL games on these mining cards.

_Some BIOS require additional configurating._


Now follow these steps:

1. Download 417.22 NVIDIA driver (without installing it): https://www.guru3d.com/files-get/geforce-417-22-whql-driver-download,1.html
I guess this one is the latest, where NVIDIA didn't disable the FEATURE.
2. Right click on it and Extract all to some dir using any archive manager (7zip for example). Let's call this dir YOUR_EXTRACTED_DRIVER_DIR
3. Open ___nv\_dispi.inf___ from YOUR_EXTRACTED_DRIVER_DIR/Display.Driver
4. Find and "replace all" strings exactly "___= Section110,___" with exactly "___= Section108,___"
4.1. Also replace "___= Section109,___" with "___= Section107,___"
_Yes, these strings start with equals sign followed by space (= ) and end with comma (,)_

Additional required steps:

5. Disable automatic driver updates: regedit -> Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching -> ___SearchOrderConfig = 0___
6. Also check Your computer -> Properties -> Advanced system settings -> Hardware -> Device Installation settings -> ___No (your device might not work as expected)___ must be set
7. Enable testsinging -> run ___cmd___ or ___powershell___ (___by admin___) -> enter the command ___bcdedit /set testsigning on___. You will see something like _The operation completed successfully._
8. Uninstall existing NVIDIA drivers using ___DDU___ (google: display driver uninstaller) with reboot
9. After reboot complete - Run the driver installer from YOUR_EXTRACTED_DRIVER_DIR -> ___setup.exe___
10. Disable Geforce experience, click Next, Yes or whatever, choose _Custom install_ and _Make clean installation_, wait for the prompt and ___confirm___ you want install this driver anyway. Wait until it finishes.
11. Disable testsigning -> run ___cmd___ or ___powershell___ (___by admin___) -> enter the command ___bcdedit /set testsigning off___. You will see something like _The operation completed successfully._
12. Reboot
13. Go to Display settings -> Graphics settings -> Choose your ___DirectX___ game -> Set ___High performance NVIDIA P106-100___
14. Enjoy your ___DirectX___ games
