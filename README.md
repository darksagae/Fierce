# Fierce
Thinking...
> 
> Okay, the user is asking about Fierce, another DNS reconnaissance tool in Kali Linux. Let me recall what I know about Fierce.
> 
> First, Fierce is a DNS scanner used to locate non-contiguous IP space and hostnames. It's designed for situations where a user has a target domain but not much else. It helps in discovering both internal and external network information. Unlike Dnsrecon or Dnsenum, Fierce is more about finding as much information as possible about a domain's DNS infrastructure, including subdomains and IP ranges.
> 
> I need to start with installation. Kali might have it pre-installed, but if not, the user can install it using 'sudo apt install fierce' or via the GitHub repository. Also, mention that it's a Perl script, so Perl dependencies might be needed.
> 
> Basic syntax: The command typically starts with 'fierce' followed by the domain and options. Common options include --dns-server to specify a DNS server, --wordlist for brute-forcing subdomains, and --range to scan IP ranges.
> 
> Examples are crucial. Let's structure them as follows:
> 
> 1. Basic scan: fierce --domain example.com
> 2. Specify a DNS server: fierce --domain example.com --dns-server 8.8.8.8
> 3. Brute-force subdomains with a custom wordlist: fierce --domain example.com --wordlist /path/to/wordlist.txt
> 4. Scan an IP range: fierce --domain example.com --range 192.168.0.0/24
> 5. Connect to found hosts via HTTP: fierce --domain example.com --connect
> 
> For each example, provide a sample output. For instance, the basic scan would list found subdomains and their IPs. The brute-force example would show discovered subdomains from the wordlist.
> 
> Potential mistakes: Users might forget to specify the domain or use incorrect options. Also, not having the right permissions or network access could lead to incomplete results.
> 
> Ethical considerations: Emphasize that Fierce should only be used on domains the user owns or has explicit permission to scan. Unauthorized use could be illegal.
> 
> Differentiating Fierce from other tools: Fierce is more aggressive in scanning and attempts to find linked networks and subdomains. It also tries to connect to discovered web servers to verify their existence.
> 
> Sample outputs should reflect typical results, like discovered subdomains, IP addresses, and possibly HTTP banners if --connect is used.
> 
> Troubleshooting tips: If Fierce isn't working, check Perl dependencies, network connectivity, DNS server accessibility, and wordlist paths. Also, running with --verbose might help diagnose issues.
> 
> Finally, wrap everything into a structured format with installation instructions, syntax, options, examples, outputs, and ethical notes.
> 


**Fierce** is a semi-lightweight DNS reconnaissance tool in Kali Linux designed to discover non-contiguous IP spaces and subdomains associated with a target domain. It combines zone transfers, brute-forcing, and reverse lookups. Below is a guide on its usage, examples, and sample outputs.

---

### **Installation**
Fierce is pre-installed in Kali Linux. If missing:
```bash
sudo apt update && sudo apt install fierce
```

---

### **Basic Syntax**
```bash
fierce --domain <target-domain> [options]
```

---

### **Common Options**
| Option               | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `--dns-server <IP>`  | Use a custom DNS server (e.g., `8.8.8.8`).                                |
| `--wordlist <file>`  | Brute-force subdomains using a custom wordlist.                           |
| `--range <IP/CIDR>`  | Scan a specific IP range (e.g., `192.168.1.0/24`).                        |
| `--connect`          | Attempt HTTP connections to discovered hosts.                            |
| `--wide`             | Scan all IPs in the subnet of discovered hosts (aggressive).              |
| `--delay <ms>`       | Add delays between requests to avoid detection.                           |

---

### **Examples**

#### **1. Basic Domain Scan**
```bash
fierce --domain example.com
```
**Output**:
```
DNS Servers for example.com:
  a.iana-servers.net
  b.iana-servers.net

Trying zone transfer first:
  Testing a.iana-servers.net
  Request timed out or transfer not allowed.
  Testing b.iana-servers.net
  Request timed out or transfer not allowed.

Unsuccessful zone transfer. Switching to brute force.

Now performing 2280 test(s)...
Subdomain found: www.example.com      93.184.216.34
Subdomain found: mail.example.com     93.184.216.35
Subdomain found: ftp.example.com      93.184.216.36
Done.
```

---

#### **2. Use a Custom DNS Server**
```bash
fierce --domain example.com --dns-server 8.8.8.8
```
**Explanation**: Uses Google’s DNS (`8.8.8.8`) for queries.

---

#### **3. Brute-Force Subdomains with a Wordlist**
```bash
fierce --domain example.com --wordlist /usr/share/wordlists/subdomains-top1mil.txt
```
**Output**:
```
Brute-forcing subdomains with 100000 entries...
Found: admin.example.com     203.0.113.45
Found: dev.example.com       198.51.100.22
Found: api.example.com       192.0.2.10
```

---

#### **4. Scan an IP Range**
```bash
fierce --domain example.com --range 192.168.1.0/24
```
**Output**:
```
Scanning 192.168.1.0/24 for PTR records...
192.168.1.10   →   server1.example.com
192.168.1.20   →   printer.example.com
```

---

#### **5. Connect to HTTP Services**
```bash
fierce --domain example.com --connect
```
**Output**:
```
Found: www.example.com (93.184.216.34)
Connecting to http://93.184.216.34...
  HTTP/1.1 200 OK
  Server: nginx
Found: mail.example.com (93.184.216.35)
Connecting to http://93.184.216.35...
  HTTP/1.1 403 Forbidden
```

---

### **Key Features**
- **Zone Transfer Checks**: Tests DNS servers for misconfigured zone transfers.
- **Subdomain Brute-Forcing**: Uses wordlists to discover hidden subdomains.
- **Reverse Lookups**: Maps IP ranges to hostnames.
- **Aggressive Scanning**: The `--wide` flag expands scans to entire subnets.

---

### **Ethical Note**
- Use **only on authorized targets**. Unauthorized scanning violates laws and ethics.

---

### **Troubleshooting**
- **No Results?** Try a larger wordlist or the `--wide` flag.
- **Connection Issues?** Ensure network access and DNS server responsiveness.
- **Slow Performance?** Add delays with `--delay 1000`.

---

### **Comparison with Dnsrecon/Dnsmap**
- **Fierce**: Focuses on aggressive IP range scanning and HTTP verification.
- **Dnsrecon**: More comprehensive DNS record enumeration.
- **Dnsmap**: Simpler subdomain brute-forcing without IP range checks.

---

Combine Fierce with tools like **Nmap** or **Nikto** for deeper vulnerability analysis of discovered hosts.
                            ALTERNATIVE
The Fierce tool is a reconnaissance tool used in Kali Linux for DNS enumeration and discovering non-contiguous IP space and hostnames. It helps identify potential targets by using DNS queries to find subdomains and misconfigured networks.

### How to Use Fierce

1. **Accessing Fierce**
   - **Terminal**: Open a terminal and type `fierce -h` to see the help options.
   - **GUI Method**: Navigate to Applications -> Kali Linux -> Information Gathering -> DNS Analysis -> Fierce.

### Basic Syntax
```bash
fierce [options]
```

### Common Options and Examples

1. **Basic Domain Scan**
   ```bash
   fierce --domain example.com
   ```
   - Performs a default scan against the target domain `example.com`.

2. **Subdomain Enumeration**
   ```bash
   fierce -dns example.com -threads 10
   ```
   - Scans for subdomains of `example.com` using 10 threads.

3. **Brute-Forcing Subdomains**
   ```bash
   fierce -dns example.com -wordlist /path/to/wordlist.txt
   ```
   - Uses a specified wordlist to brute-force subdomains of `example.com`.

4. **Performing DNS Reconnaissance**
   ```bash
   fierce -dns example.com --connect
   ```
   - Attempts to make HTTP connections to non-RFC1918 addresses and outputs the return headers.

5. **Outputting Results to a File**
   ```bash
   fierce -dns example.com -file results.txt
   ```
   - Saves the results of the scan to `results.txt`.

### Important Considerations
- **Ethical Use**: Only use Fierce against domains you have permission to test to avoid legal issues.
- **Zone Transfers**: Fierce tries to perform zone transfers, but many domains do not allow this.
- **Wildcards**: It checks for wildcard DNS records to avoid false positives during brute-forcing.

Using Fierce effectively can help gather valuable information during the reconnaissance phase of penetration testing.


                                        
