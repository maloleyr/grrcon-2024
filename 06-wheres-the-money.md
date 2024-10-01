# Where’s the Money: Defeating ATM Disk Encryption

## Speakers

Matt Burch

## Notes and Observations

- Another excellent presentation. It was practical, had demonstrations, and was apt.
- Consumer ATMs: Think grocery stores and gas stations. Usually running Windows CE.
- Financial ATMs: Think Banks. Usually running Windows 7/10. Manufactured by Hyosung, NCR, or Diebold.
- This talk focused on Diebold Nixdorf’s Vynamic Security Suite (VSS) which is found in Diebold ATMs.
- Two parts to an ATM: Top Hat contains the PC, keypad, and connections. The Bottom is the VAULT which is pretty darn secure.
- The Top Hat is very vulnerable to simple physical attacks. For example you can quickly break in and pull a hard drive! 
- Uses a tubular lock.
- Physical access is really the only attack vector in play.
- At a high level: ATM powers on; a secure boot process begins; a Linux OS (barebones) will boot and validate some internal files (this is where we can breach) before unlocking the Windows partition (bitlocker) and then Windows will boot. Windows boots to an autologin (local admin) then launches the ATM software package. 
- Essentially this researcher found ways to: 
  - Get the Bitlocker key from the Linux OS;
  - Alter the Linux boot process to launch a reverse shell during boot up;
  - This enables remote access to the Linux OS and likely the Windows OS as well.
- Caveat of course is: 
  - Requires physical access;
  - Have to pull the hard drive, image it, modify it, re-flash the hard drive, and reinstall.
    - Valid research but not a real world attack.
- Vulnerabilities identified in the talk have been remediated by Diebold. Vulnerable ATMs could be out there! Hard to get the end user organizations to update HOWEVER Diebold and others have remote ways of doing this. 
  - The remote update process could be an attack vector to keep an eye on.
