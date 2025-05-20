# Bash Grundlagen VM scripts

## Übung 5 - Advanced regex

## Erklärung dmesg mit Regex
Regex mit der Verwendung von dmesg sorgt dafür, dass es die Kerlen Nachrichten seit Systemstart ausgibt, mit erweitertem regular expression und dabei nur die Zeilen anzeigt in welchen eine PCI-Adresse wie folgt vorkommt.

### Beispiel:

## Command dmesg ohne Regex
```bash
sudo dmesg'
```

### Ausgabe
```bash
mert@m122:~$ sudo dmesg
[    0.000000] Linux version 6.8.0-59-generic (buildd@lcy02-amd64-035) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0, GNU ld (GNU Binutils for Ubuntu) 2.42) #61-Ubuntu SMP PREEMPT_DYNAMIC Fri Apr 11 23:16:11 UTC 2025 (Ubuntu 6.8.0-59.61-generic 6.8.12)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-6.8.0-59-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Hygon HygonGenuine
[    0.000000]   Centaur CentaurHauls
[    0.000000]   zhaoxin   Shanghai
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000f7feffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f7ff0000-0x00000000f7ffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000f7fff000-0x00000000f7ffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001873fffff] usable
```

## Command dmesg mit Regex
```bash
sudo dmesg | egrep '[0-9]{4}:[0-9]{2}:[0-9a-f]{2}.[0-9]'
```

### Ausgabe
```bash
mert@m122:~$ sudo dmesg | egrep '[0-9]{4}:[0-9]{2}:[0-9a-f]{2}.[0-9]'
[    0.108913] pci 0000:00:00.0: [8086:7192] type 00 class 0x060000 conventional PCI endpoint
[    0.110313] pci 0000:00:07.0: [8086:7110] type 00 class 0x060100 conventional PCI endpoint
[    0.111191] pci 0000:00:07.1: [8086:7111] type 00 class 0x010180 conventional PCI endpoint
[    0.111955] pci 0000:00:07.1: BAR 4 [io  0xffa0-0xffaf]
[    0.112033] pci 0000:00:07.1: BAR 0 [io  0x01f0-0x01f7]: legacy IDE quirk
[    0.112035] pci 0000:00:07.1: BAR 1 [io  0x03f6]: legacy IDE quirk
[    0.112036] pci 0000:00:07.1: BAR 2 [io  0x0170-0x0177]: legacy IDE quirk
[    0.112037] pci 0000:00:07.1: BAR 3 [io  0x0376]: legacy IDE quirk
[    0.112296] pci 0000:00:07.3: [8086:7113] type 00 class 0x068000 conventional PCI endpoint
[    0.112987] pci 0000:00:07.3: quirk: [io  0x0400-0x043f] claimed by PIIX4 ACPI
[    0.113340] pci 0000:00:08.0: [1414:5353] type 00 class 0x030000 conventional PCI endpoint
[    0.114362] pci 0000:00:08.0: BAR 0 [mem 0xf8000000-0xfbffffff]
[    0.114558] pci 0000:00:08.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.131573] pci 0000:00:08.0: vgaarb: setting as boot VGA device
[    0.131573] pci 0000:00:08.0: vgaarb: bridge control possible
[    0.131573] pci 0000:00:08.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.151695] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.218968] ata_piix 0000:00:07.1: version 2.13
[    0.219104] ata_piix 0000:00:07.1: Hyper-V Virtual Machine detected, ATA device ignore set
[    1.915002] piix4_smbus 0000:00:07.3: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr
[ 4563.361800] audit: type=1400 audit(1747141537.968:226): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="lsb_release" pid=4295 comm="apparmor_parser"
[ 4563.382125] audit: type=1400 audit(1747141537.988:227): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="nvidia_modprobe" pid=4298 comm="apparmor_parser"
[ 4563.382734] audit: type=1400 audit(1747141537.989:228): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="nvidia_modprobe//kmod" pid=4298 comm="apparmor_parser"
[ 4563.832640] audit: type=1400 audit(1747141538.440:229): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="1password" pid=4622 comm="apparmor_parser"
[ 4563.832651] audit: type=1400 audit(1747141538.440:230): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name=4D6F6E676F444220436F6D70617373 pid=4624 comm="apparmor_parser"
[ 4563.832666] audit: type=1400 audit(1747141538.440:231): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="QtWebEngineProcess" pid=4625 comm="apparmor_parser"
[ 4563.832771] audit: type=1400 audit(1747141538.440:232): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="Discord" pid=4623 comm="apparmor_parser"
[ 4563.835849] audit: type=1400 audit(1747141538.443:233): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="balena-etcher" pid=4626 comm="apparmor_parser"
[ 4566.474298] kauditd_printk_skb: 114 callbacks suppressed
[ 4566.474301] audit: type=1400 audit(1747141541.081:348): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="ubuntu_pro_apt_news" pid=5015 comm="apparmor_parser"
[ 4566.690720] audit: type=1400 audit(1747141541.298:349): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="ubuntu_pro_esm_cache" pid=5018 comm="apparmor_parser"
[ 4566.691423] audit: type=1400 audit(1747141541.299:350): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="ubuntu_pro_esm_cache//apt_methods" pid=5018 comm="apparmor_parser"
[ 4566.692076] audit: type=1400 audit(1747141541.299:351): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="ubuntu_pro_esm_cache//apt_methods_gpgv" pid=5018 comm="apparmor_parser"
[ 4566.693012] audit: type=1400 audit(1747141541.300:352): apparmor="STATUS" oper
```

### Regex aufbau
```bash
[0-9]{4}    # genau vier Ziffern 0–9
  :           # gefolgt von einem Doppelpunkt
  [0-9]{2}    # genau zwei Ziffern 0–9
  :           # noch ein Doppelpunkt
  [0-9a-f]{2} # genau zwei Hex-Zeichen (0–9, a–f)
  \.          # ein Literal-Punkt
  [0-9]       # eine Ziffer 0–9
```

## Erklärung ifconfig mit Regex
Regex mit der Verwendung von ifconfig sorgt dafür, dass er exakt die IPv4 Adresse ausgibt und von all den Daten uns nur zeigt, was wir effektiv sehen wollen

### Beispiel:

### Command ifconfig ohne Regex
```bash
ifconfig
```

### Ausgabe
```bash
mert@m122:~$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.50.254  netmask 255.255.240.0  broadcast 172.20.63.255
        inet6 fe80::215:5dff:fe10:2407  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:10:24:07  txqueuelen 1000  (Ethernet)
        RX packets 240691  bytes 295468403 (295.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 41635  bytes 3286717 (3.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 454  bytes 46158 (46.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 454  bytes 46158 (46.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

### Command ifconfig mit Regex
```bash
ifconfig | grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])
```

### Ausgabe
```bash
mert@m122:~$ ifconfig | grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])'
172.20.50.254
255.255.240.0
172.20.63.255
127.0.0.1
255.0.0.0
```

### Regex aufbau
```bash
(                     # dreimal wiederholt:
  (1?[0-9][0-9]?      #   Zahlen 0–199
   |2[0-4][0-9]        #   Zahlen 200–249
   |25[0-5]            #   Zahlen 250–255
  )\.                 #   gefolgt von einem Literal-Punkt
){3}                  # genau drei solcher Oktette
(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])
                      # viertes Oktett 0–255
```