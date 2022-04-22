# forti-vpn-azure
FortiGate BaseLine Configuration to create VPN Tunnel up to Azure!

```
config vpn ipsec phase1-interface 
    edit "SiteName2Azure" 
        set interface "wan1" 
        set ike-version 2 
        set peertype any 
        set net-device enable 
        set proposal aes256-sha1 aes256-sha256 aes128-sha256 
        set dpd on-idle 
        set dhgrp 2 
        set nattraversal disable 
        set remote-gw 172.0.0.1
        #set psksecret "set_randomly generated key here"
        set dpd-retryinterval 5 
    next 
 
 
config vpn ipsec phase2-interface 
    edit "SiteName2Azure" 
        set phase1name "SiteName2Azure" 
        set proposal aes128-sha1 aes256-sha1 3des-sha1 aes128-sha256 aes256-sha256 3des-sha256 
        set keylifeseconds 3600 
    next    
end 
```
