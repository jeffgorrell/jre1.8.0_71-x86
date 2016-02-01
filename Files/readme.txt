any content in this path can be referenced with the $dirFiles variable

the exe does not work as of 8u60.
The path given to MsiInstallProduct starts with C:\Windows\system32\ but for 32 bit process on 64 bit OS the real path would be C:\Windows\SysWOW64\ because of file system redirection. That's why Windows Installer Engine can't find the MSI package.

Best workaround is to launch the exe installer to extract the msi to %USERPROFILE%\AppData\LocalLow\Oracle\Java\

Option 1) If you want to use the exe installer (substitute correct version)
Copy the msi to C:\Windows\System32\Config\SystemProfile\AppData\LocalLow\Oracle\Java\jre1.8.0_71\jre1.8.0_71.msi
run the exe with /s parameter.

Option 2) Simply just use the MSI from whatever path you want, however you will need to pass the MSI the desired parameters on the command line (can't use the C:\ProgramData\Oracle\Java\java.settings.cfg like with the exe). 
It is suggested that the MSI is copied to a known local path before execution rather than from ccmcache to avoid any possible msi source issues later on.