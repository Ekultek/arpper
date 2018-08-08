# arpper

`arpper` is a simple solution to an annoying problem of gathering live IP addresses from a local network.

# Scenario

On a local network you need to determine which connections are alive and which are not. You can use `arp -a` to do this, but `arp -a` will display everything on the local network, alive or not:

```bash
arp -a
...
? (10.9.1.121) at 68:5c:25:b3:99:7b on eth0 ifscope [ethernet]
? (10.9.1.122) at (incomplete) on en0 [ethernet]
? (10.9.1.202) at 0e:4e:34:2c:7b:8c on eth0 ifscope [ethernet]
...
```

`arrper` will utilize `arp` and `ping` to determine which hosts are alive and which are not and save the living hosts into a file:

```bash
./arpper
[!] cannot determine if required tools are on the system or not (to fix: `pip install whichcraft`), skipping determination..
[+] running 'arp -a' through current connected network..
[+] determining live hosts..
[+] LIVING HOSTS:
------------------------------
|   IP:                 MAC: |
------------------------------
[+] 10.9.1.200          6e:5b:35:b3:79:7
[+] 10.9.1.201          28:57:be:ae:51:7b
[+] 10.9.1.202          0:4e:84:21:4b:8a
[+] 10.9.1.60           78:7e:8a:c4:66:98
[+] 10.9.1.5            58:2e:b1:df:53:da
...
------------------------------
[+] data written to 20180808-results.txt
```

# Installation

Git clone:
```
git clone https://github.com/ekultek/arpper.git && cd arpper && chmod a+x arpper && ./arpper
```

cURL:
```
curl -o arpper https://gist.githubusercontent.com/Ekultek/7c28e48da71092c8f45a56d390e803b1/raw/933d99bea5a10323f9fa901525fd52400eeeda6a/arpper && chmod a+x arpper && ./arpper
```

wGET:
```
wget -O arpper https://gist.githubusercontent.com/Ekultek/7c28e48da71092c8f45a56d390e803b1/raw/933d99bea5a10323f9fa901525fd52400eeeda6a/arpper && chmod a+x arpper && ./arpper
```

# Requirements

 - `arp` (absolute)
 - `ping` (default*)
 - `whichcraft` (optional)

If you want `arpper` to check if you have `arp` and `ping` on the system, you will need to install `whichcraft` with `pip install whichcraft`. `arpper` will attempt to run regardless if this is installed or not.

# License

No license, do as you will.