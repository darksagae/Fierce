# Fierce
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


                                        
