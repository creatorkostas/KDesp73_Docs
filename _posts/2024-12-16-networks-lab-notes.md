---
title: Networks Lab Notes 
date: 2024-12-16 14:33:00 +0200
categories: [notes] 
tags: [networks, school]
---

## Links

- [Σελίδα Μαθήματος](https://people.iee.ihu.gr/~dima/?page_id=13#)
- [DNS Watch](https://dnswatch.info)
- [Google Dig](https://toolbox.googleapps.com/apps/dig/)
- [Dig](https://www.digwebinterface.com/)
- [Hex Packet Decoder](https://hpd.gasmi.net/)
- [BIND Download](https://downloads.isc.org/isc/bind9/9.16.7/BIND9.16.7.x64.zip)
- [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)
- [Υποδικτύωση](https://www.davidc.net/sites/default/subnets/subnets.html)


## Ενότητα 1

### Εντολή `ipconfig /all`

Η εντολή `ipconfig /all` εμφανίζει αναλυτικές πληροφορίες για τη διαμόρφωση του δικτύου.

```powershell
ipconfig /all
```

#### Host 
- Physical Address
- IPv4

#### Δίκτυο
- Subnet Mask
- Defauly Gateway (Διεύθυνση Router)

### Εντολή `tracert`

```powershell
tracert <domain | IPv4>
```

Η εντολή tracert εμφανίζει τη διαδρομή που ακολουθούν τα πακέτα μέχρι έναν συγκεκριμένο προορισμό, παρέχοντας τη λίστα των ενδιάμεσων σταθμών (jumps).

Σημειώσεις:
- Γραμμές με αστερίσκους (*) υποδεικνύουν χρονικά όρια (timeouts) και δεν τις λαμβάνουμε υπόψη.


### TCP Protocol Stack

![tcp-protocol-stack](/assets/tcp-protocol-stack.png "TCP Protocol Stack")

### DNS

- Θύρα 53 (Με πάντα UDP πρωτόκολλο)

Για καθαρισμό του DNS cache:
- Windows: `ipconfig /flushdns`
- Linux: `sudo system-resolve –flush-caches` 

#### Records

- NS: Name Server (Διακομιστής Ονομάτων)
- A: Address Record (συσχέτιση ενός domain με μία IPv4 διεύθυνση)
- MX: Mail Exchange Record (Διακομιστής Ηλεκτρονικού Ταχυδρομείου)
- CNAME: Canonical Name (συσχέτιση ενός εικονικού domain με ένα πραγματικό)

### Εντολή `arp -a <host>`

```powershell
arp -a <host>
```

## Ενότητα 2

### Wireshark

#### Φίλτρα

| Φίλτρο | Περιγραφή |
|--------|-----------|
| `dns` | Πακέτα που αφορούν το προτόκολλο DNS |
| `ip.addr == 192.168.1.1` | Πακέτα από ή πρός τη διεύθυνση IP 192.168.1.1 |
| `tcp.port == 443` | Πακέτα μέσω της θύρας 443 |
| `udp` | Μόνο UDP πακέτα |
| `eth.addr == 00:11:22:33:44:55` | Πακέτα από ή προς συγκεκριμένη MAC Address |
| `http.request.method == "GET"` | Αιτήματα HTTP GET |
| `frame.len > 1000` | Πακέτα με μέγεθος μεγαλύτερο απο 1000 bytes |
| `ip.src == 192.168.1.1 && tcp.flags.syn == 1` | SYN πακέτα από συγκεκριμένη IP |

Για περισσότερα στην [εδώ](https://wiki.wireshark.org/DisplayFilters)

#### Follow TCP packet

![wireshark_follow_tcp](/assets/wireshark_follow_tcp.png "Follow TCP packet")

### Σύγκριση χαρακτηριστικών των προτοκόλλων

![protocol-comparison](/assets/protocol-comparison.png "Protocol Comparison")

## Ενότητα 3

![network-masks](/assets/network-masks.png "Network Masks")

### Static Routing

![static-routing](/assets/static_routing.png "Static Routing in CPT")
