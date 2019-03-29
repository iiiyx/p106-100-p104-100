__REMEMBER__: to make it work you must have 4-th generation Intel Core CPU with integrated video. Also you must certainly enable iGPU at BIOS (32-64 MB will be enough).

_Some BIOS require additional configurating._


Now follow these steps:

1. Download the newest NVIDIA driver (without installing it)
2. Right click on it and Extract all to some dir using any archive manager (7zip for example). Let's call this dir YOUR_EXTRACTED_DRIVER_DIR
3. Open ___nv\_disp.inf___ from YOUR_EXTRACTED_DRIVER_DIR/Display.Driver
4. Search for your Video Card name (for example _p106-100_) at the end of the file. Something like _NVIDIA\_DEV.___1C07___ = "NVIDIA P106-100"_
5. Remember your device code -> ___1C07___
6. Now search for analogous card -> any _GTX 1060_ is for _p106-100_, and _GTX 1070_ is for _p104-100_. You will find something like _NVIDIA\_DEV.___1C06___ = "NVIDIA GeForce GTX 1060 6GB"_
7. Remember analogous device code -> ___1C06___
8. Now search for the section name for analogous device code: something like _%NVIDIA\_DEV.___1C06___%           = ___Section108___, PCI\VEN\_10DE&DEV\_1C06_
9. Remember section name ___Section108___
10. Search and replace section name for your device: you will find something like _%NVIDIA\_DEV.___1C07___%           = ___Section110___, PCI\VEN\_10DE&DEV\_1C07_. Change ___Section110___ to ___Section108___
11. There will two different section names. For example, for _p106-100_: _Section110_, _Section109_ and for _GTX 1060_: _Section108_, _Section107_. You must change them respectively: _110_ -> _108_, _109_ -> _107_. Just change section name for your device to section for analogus device for every block. Take a look how I changed it at my commit: https://github.com/iiiyx/p106-100-p104-100/commit/b7d774a159a3b19e828e1fdac74a82128898ec17#diff-7393cec44a96cba9ae1207071c71e341

Additional required steps:

12. Disable automatic driver updates: regedit -> Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching -> ___SearchOrderConfig = 0___
13. Also check Your computer -> Properties -> Advanced system settings -> Hardware -> Device Installation settings -> ___No (your device might not work as expected)___ must be set
14. Uninstall existing NVIDIA drivers using ___DDU___ (google: display driver uninstaller)
15. Enable testsinging -> run ___cmd___ or ___powershell___ (___by admin___) -> enter the command ___bcdedit /set testsigning on___. You will see something like _The operation completed successfully._
16. Reboot
17. Run the driver installer from YOUR_EXTRACTED_DRIVER_DIR -> ___setup.exe___, click Next, Yes or whatever, choose _Custom install_ and _Make clean installation_, wait for the prompt and ___confirm___ you want install this driver anyway. Wait until it finishes.
18. Disable testsigning -> run ___cmd___ or ___powershell___ (___by admin___) -> enet the command ___bcdedit /set testsigning off___. You will see something like _The operation completed successfully._
19. Reboot
20. Go to Display settings -> Graphics settings -> Choose your ___DirectX___ game -> Set ___High performance NVIDIA P106-100___
21. Enjoy your ___DirectX___ games
