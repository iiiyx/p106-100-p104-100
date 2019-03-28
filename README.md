Find the changes at my commit.

1. Download the newest NVIDIA driver (without installing it)
2. Extract all to some dir using any archive manager (7zip as an example). Let's call this dir as YOUR_EXTRACTED_DRIVER_DIR.
3. Modify files at YOUR_EXTRACTED_DRIVER_DIR/Display.Driver: _nv\_disp.inf_ and _nvaci.inf_
4. Disable automatic driver updates: regedit -> Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching -> SearchOrderConfig = 0
5. Also check Your computer -> Properties -> Advanced system settings -> Hardware -> Device Installation settings -> _No (your device might not work as expected)_ should be set
6. Uninstall existing NVIDIA drivers using DDU
7. Enable testsinging -> run cmd or powershell (by admin) -> type in the commend _bcdedit /set testsigning on_
8. Reboot
9. Run the driver installer from YOUR_EXTRACTED_DRIVER_DIR -> setup.exe, click Next, Yes or whatever, wait for a prompt and confirm you want install it anyway. Wait until it finishes.
10. Disable testsigning -> run cmd or powershell (by admin) -> type in the commend _bcdedit /set testsigning off_
11. Reboot
12. Display settings -> Graphics settings -> Choose your DirectX game -> Set High performance
13. Enjoy your game