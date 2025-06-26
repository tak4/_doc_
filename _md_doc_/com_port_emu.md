# Null-modem emulator(com0com)
https://com0com.sourceforge.net/

# Minicom
https://help.ubuntu.com/community/Minicom

# ubuntu serial port check
ls -la /dev/ttyS*

# minicom
sudo minicom -D /dev/ttyS1

# cu
sudo apt update
sudo apt install cu

cu -l /dev/ttyS5 -s 9600
