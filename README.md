1. Download the newest NVIDIA driver (without installing it)
2. Right click on it and Extract all to some dir using any archive manager (7zip for example). Let's call this dir YOUR_EXTRACTED_DRIVER_DIR
3. Open _nv\_disp.inf_ from YOUR_EXTRACTED_DRIVER_DIR/Display.Driver
4. Search for your Video Card name (for example _p106-100_) at the end of the file. Something like _NVIDIA\_DEV.1C07 = "NVIDIA P106-100"_
5. Remember your device code -> _1C07_
6. Now search for analogous card -> any _GTX 1060_ is for _p106-100_, and _GTX 1070_ is for _p104-100_. You will find something like _NVIDIA\_DEV.1C06 = "NVIDIA GeForce GTX 1060 6GB"_
7. Remember analogous device code -> _1C06_
8. Now search for the section name for analogous device code: something like _%NVIDIA\_DEV.1C06%           = Section108, PCI\VEN\_10DE&DEV\_1C06_
9. Remember section name _Section108_
10. Search and replace section name for your device: you will find something like _%NVIDIA\_DEV.1C07%           = Section110, PCI\VEN\_10DE&DEV\_1C07_. Change _Section110_ to _Section108_
11. There will two different section names. For example, for _p106-100_: _Section110_, _Section109_ and for _GTX 1060_: _Section108_, _Section107_. You must change them respectively: _110_ -> _108_, _109_ -> _107_. Just change section name for your device to section for analogus device for every block.

Additional required steps:

12. Disable automatic driver updates: regedit -> Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching -> SearchOrderConfig = 0
13. Also check Your computer -> Properties -> Advanced system settings -> Hardware -> Device Installation settings -> _No (your device might not work as expected)_ should be set
14. Uninstall existing NVIDIA drivers using DDU
15. Enable testsinging -> run cmd or powershell (by admin) -> type in the commend _bcdedit /set testsigning on_
16. Reboot
17. Run the driver installer from YOUR_EXTRACTED_DRIVER_DIR -> setup.exe, click Next, Yes or whatever, wait for a prompt and confirm you want install it anyway. Wait until it finishes.
18. Disable testsigning -> run cmd or powershell (by admin) -> type in the commend _bcdedit /set testsigning off_
19. Reboot
20. Display settings -> Graphics settings -> Choose your DirectX game -> Set High performance _NVIDIA P106-100_
21. Enjoy your DirectX games
