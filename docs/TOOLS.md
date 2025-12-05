# Interactive Tools Guide

**DDoS Tools Interactive Console**  
**Version**: 2.5  
**Last Updated**: December 2025  
**Maintained By**: Muhammad Thariq

---

## 📖 Overview

DDoS Tools includes a comprehensive set of interactive utilities for network analysis, diagnostics, and reconnaissance. All tools are accessible through the interactive console mode.

---

## 🚀 Accessing the Console

Launch the interactive console:

```bash
./ddos-tools
```

Then select option `8` or type `TOOLS` to enter the tools console.

Or directly from command line:

```bash
./ddos-tools --console
```

---

## 🛠️ Available Tools (7/7 - 100% Complete)

### 1. DSTAT - Network & System Statistics Monitor

**Purpose**: Real-time monitoring of network traffic and system resources.

**Usage**:
```
DDoSTools:~# DSTAT
```

**Features**:
- Live bytes sent/received per second
- Live packets sent/received per second
- Memory usage (allocated, total, percentage)
- Active goroutines count
- Updates every second
- Press Ctrl+C to stop

**Example Output**:
```
--- Network & System Statistics ---
Bytes Sent:        125.43 KB/s
Bytes Received:    892.17 KB/s
Packets Sent:      1.2K/s
Packets Received:  3.4K/s
Memory Usage:      45 MB / 512 MB (8.79%)
Goroutines:        12
-----------------------------------
```

**Platform Support**:
- ✅ Linux (reads `/proc/net/dev`)
- ✅ Windows (uses `GetIfTable2` API)
- ✅ macOS/Darwin (BSD sockets)

---

### 2. CHECK - Website Availability Checker

**Purpose**: Check if a website is online and get HTTP status codes.

**Usage**:
```
DDoSTools:~# CHECK
give-me-ipaddress# https://example.com
```

**Features**:
- HTTP/HTTPS support
- Status code display
- Online/Offline detection
- 20-second timeout
- Connection error reporting

**Example Output**:
```
Please wait...
Status Code: 200
Status: ONLINE
```

**Status Detection**:
- Status code < 500: **ONLINE**
- Status code >= 500: **OFFLINE**
- Connection error: **Error displayed**

**Commands**:
- `BACK` - Return to main console
- `CLEAR` - Clear screen
- `EXIT` - Exit program

---

### 3. INFO - IP Geolocation & ISP Lookup

**Purpose**: Get detailed information about an IP address or domain.

**Usage**:
```
DDoSTools:~# INFO
give-me-ipaddress# example.com
```

**Features**:
- Domain to IP resolution
- Country lookup
- City lookup
- Organization (ORG) lookup
- ISP identification
- Region information
- Uses ipwhois.app API

**Example Output**:
```
Country: United States
City: Los Angeles
Org: Example Organization
ISP: Example ISP LLC
Region: California
```

**Input Formats Supported**:
- Domain: `example.com`
- Full URL: `https://example.com/path`
- IP address: `93.184.216.34`

**Commands**:
- `BACK` - Return to main console
- `CLEAR` - Clear screen
- `EXIT` - Exit program

---

### 4. TSSRV - TeamSpeak SRV Record Resolver

**Purpose**: Resolve TeamSpeak 3 DNS SRV records to find server addresses.

**Usage**:
```
DDoSTools:~# TSSRV
give-me-domain# ts3server.example.com
```

**Features**:
- Resolves `_ts3._udp.` SRV records
- Resolves `_tsdns._tcp.` SRV records
- Shows target host and port
- Handles multiple records
- Useful for TeamSpeak server discovery

**Example Output**:
```
_ts3._udp.ts3server.example.com: voice.example.com:9987
_tsdns._tcp.ts3server.example.com: Not found
```

**SRV Record Types**:
- `_ts3._udp.` - TeamSpeak 3 voice server
- `_tsdns._tcp.` - TeamSpeak 3 DNS service

**Commands**:
- `BACK` - Return to main console
- `CLEAR` - Clear screen
- `EXIT` - Exit program

---

### 5. PING - Advanced TCP Ping Utility

**Purpose**: Perform TCP-based ping to measure latency and availability.

**Usage**:
```
DDoSTools:~# PING
give-me-ipaddress# example.com
```

**Features**:
- TCP connection-based ping (port 80)
- 5 ping attempts
- Round-trip time (RTT) measurement
- Packet loss calculation
- Average RTT calculation
- Online/Offline status detection
- 2-second timeout per ping

**Example Output**:
```
Address: 93.184.216.34
Reply from 93.184.216.34: time=45.23ms
Reply from 93.184.216.34: time=43.87ms
Reply from 93.184.216.34: time=44.12ms
Reply from 93.184.216.34: time=46.01ms
Reply from 93.184.216.34: time=44.56ms

Ping Statistics:
Packets: Sent = 5, Received = 5, Lost = 0
Average RTT: 44.76ms
Status: ONLINE
```

**Status Detection**:
- All packets lost: **OFFLINE**
- At least one reply: **ONLINE**

**Commands**:
- `BACK` - Return to main console
- `CLEAR` - Clear screen
- `EXIT` - Exit program

---

### 6. CFIP - CloudFlare IP Range Finder

**Purpose**: Fetch and display official CloudFlare IP address ranges.

**Usage**:
```
DDoSTools:~# CFIP
```

**Features**:
- Fetches official CloudFlare IPv4 ranges
- Fetches official CloudFlare IPv6 ranges
- Live data from cloudflare.com
- Shows total count of ranges
- Useful for firewall rules and CDN detection

**Example Output**:
```
Fetching CloudFlare IP ranges...

CloudFlare IPv4 Ranges:
  173.245.48.0/20
  103.21.244.0/22
  103.22.200.0/22
  103.31.4.0/22
  141.101.64.0/18
  108.162.192.0/18
  190.93.240.0/20
  188.114.96.0/20
  197.234.240.0/22
  198.41.128.0/17
  162.158.0.0/15
  104.16.0.0/13
  104.24.0.0/14
  172.64.0.0/13
  131.0.72.0/22

Total IPv4 ranges: 15

CloudFlare IPv6 Ranges:
  2400:cb00::/32
  2606:4700::/32
  2803:f800::/32
  2405:b500::/32
  2405:8100::/32
  2a06:98c0::/29
  2c0f:f248::/32

Total IPv6 ranges: 7

You can save these ranges to a file for firewall rules or analysis.
```

**Use Cases**:
- Firewall configuration
- CDN detection
- CloudFlare bypass analysis
- Network security rules
- Traffic routing decisions

**Data Source**:
- IPv4: `https://www.cloudflare.com/ips-v4`
- IPv6: `https://www.cloudflare.com/ips-v6`

**Notes**:
- Data is fetched live (requires internet)
- IP ranges may change over time
- Official CloudFlare documentation

---

### 7. DNS - Advanced DNS Lookup Tool

**Purpose**: Perform comprehensive DNS record lookups for any domain.

**Usage**:
```
DDoSTools:~# DNS
give-me-domain# example.com
```

**Features**:
- **A Records** (IPv4 addresses)
- **AAAA Records** (IPv6 addresses)
- **CNAME Records** (canonical names)
- **MX Records** (mail servers with priority)
- **NS Records** (name servers)
- **TXT Records** (text records, SPF, DKIM, etc.)
- Comprehensive error handling
- Clean, organized output

**Example Output**:
```
DNS Lookup Results for: example.com

A Records (IPv4):
  93.184.216.34

AAAA Records (IPv6):
  2606:2800:220:1:248:1893:25c8:1946

CNAME Record:
  No CNAME record found

MX Records (Mail Servers):
  Priority: 10, Host: mail1.example.com.
  Priority: 20, Host: mail2.example.com.

NS Records (Name Servers):
  a.iana-servers.net.
  b.iana-servers.net.

TXT Records:
  v=spf1 include:_spf.example.com ~all
  google-site-verification=abcd1234efgh5678
```

**Record Types Explained**:

- **A (Address)**: IPv4 addresses where the domain points
- **AAAA (IPv6 Address)**: IPv6 addresses where the domain points
- **CNAME (Canonical Name)**: Alias pointing to another domain
- **MX (Mail Exchange)**: Mail servers that handle email for the domain
- **NS (Name Server)**: Authoritative DNS servers for the domain
- **TXT (Text)**: Arbitrary text data (SPF, DKIM, domain verification, etc.)

**Use Cases**:
- Domain troubleshooting
- Mail server configuration
- DNS migration verification
- Security research (SPF, DKIM analysis)
- CDN detection
- Domain reconnaissance

**Commands**:
- `BACK` - Return to main console
- `CLEAR` - Clear screen
- `EXIT` - Exit program

---

## 🎯 Console Commands

### Global Commands

Available in all tools:

| Command | Description |
|---------|-------------|
| `HELP` | Show available tools and commands |
| `CLEAR` | Clear the screen |
| `EXIT`, `QUIT`, `Q`, `E` | Exit the console/program |
| `LOGOUT`, `CLOSE` | Alternative exit commands |

### Tool-Specific Commands

Most tools support:

| Command | Description |
|---------|-------------|
| `BACK` | Return to main console from tool |
| `CLEAR` | Clear screen while in tool |
| `EXIT` | Exit program from tool |

---

## 💡 Tips & Best Practices

### Performance

1. **DSTAT**:
   - Press Ctrl+C to stop (don't use `EXIT` command)
   - Updates every 1 second
   - Low CPU overhead on all platforms

2. **CFIP**:
   - One-time fetch per execution
   - Save output to file: `./ddos-tools --console > cf-ranges.txt`
   - Use for firewall automation scripts

3. **DNS**:
   - Lookups are cached by OS resolver
   - Multiple queries on same domain are faster
   - Some records may not exist (normal)

### Network Requirements

- **DSTAT**: No network required (local stats)
- **CHECK**: Requires HTTP/HTTPS access to target
- **INFO**: Requires internet (ipwhois.app API)
- **TSSRV**: Requires DNS access
- **PING**: Requires TCP port 80 access
- **CFIP**: Requires internet (cloudflare.com)
- **DNS**: Requires DNS access

### Error Handling

All tools handle errors gracefully:
- Network timeouts (10-20 seconds)
- DNS resolution failures
- Invalid input
- API failures

---

## 📊 Platform-Specific Features

### Linux
- **DSTAT**: Reads `/proc/net/dev` for accurate stats
- Full raw socket support
- Best performance

### Windows
- **DSTAT**: Uses Windows API (`GetIfTable2`)
- Requires `unsafe` package for API calls
- Full functionality

### macOS
- **DSTAT**: Uses BSD socket stats
- Full support on Intel and Apple Silicon
- Native performance

---

## 🔒 Security Considerations

### Firewall Rules

Some tools may trigger firewall alerts:
- **PING**: Multiple TCP connections
- **CHECK**: HTTP requests
- **DNS**: DNS queries

### Rate Limiting

Be mindful of:
- **INFO**: API rate limits (ipwhois.app)
- **DNS**: DNS resolver rate limits
- **CHECK**: Target server rate limits

### Privacy

- **INFO**: Sends domain/IP to third-party API
- **CFIP**: Connects to cloudflare.com
- Other tools: Local or direct DNS queries only

---

## 🐛 Troubleshooting

### Common Issues

**DSTAT shows zeros on Windows**:
- May need administrator privileges
- Check network adapter is active

**INFO returns errors**:
- Check internet connection
- API may be rate-limited (wait and retry)
- Domain may not resolve

**PING always times out**:
- Target may block TCP port 80
- Use ICMP ping as alternative
- Check firewall settings

**DNS returns "No records found"**:
- Domain may not have that record type
- This is normal (not all domains have all records)

**CFIP fails to fetch**:
- Check internet connection
- CloudFlare URLs may be blocked
- Firewall may block HTTPS

---

## 📝 Examples

### Example 1: Full Domain Analysis

```bash
# Check if website is online
CHECK
https://example.com

# Get IP and location info
INFO
example.com

# Perform DNS lookup
DNS
example.com

# Ping the server
PING
example.com
```

### Example 2: Network Monitoring

```bash
# Start network monitoring
DSTAT

# (Press Ctrl+C after observing)
# Monitor shows live traffic during attacks
```

### Example 3: CloudFlare Detection

```bash
# Get CloudFlare IP ranges
CFIP

# Check if target uses CloudFlare
DNS
target.com

# Compare IP with CloudFlare ranges
INFO
target.com
```

### Example 4: TeamSpeak Server Discovery

```bash
# Find TeamSpeak server
TSSRV
ts.example.com

# Ping the discovered server
PING
voice.example.com
```

---

## 🔄 Integration with Attack Tools

### Reconnaissance Workflow

1. **DNS** - Find all IPs and services
2. **INFO** - Identify ISP and location
3. **CFIP** - Check if behind CloudFlare
4. **PING** - Verify connectivity
5. **CHECK** - Test web service
6. Launch appropriate attack method

### Monitoring During Attacks

1. Start **DSTAT** in separate terminal
2. Launch attack
3. Monitor network utilization
4. Adjust threads based on stats

---

## 📚 Additional Resources

### Related Documentation

- [USAGE.md](USAGE.md) - Main usage guide
- [LAYER7-METHODS.md](LAYER7-METHODS.md) - Layer 7 attacks
- [LAYER4-METHODS.md](LAYER4-METHODS.md) - Layer 4 attacks
- [PROXIES.md](PROXIES.md) - Proxy configuration

### External Tools

- `dig` - Advanced DNS queries
- `nslookup` - DNS lookup
- `whois` - Domain registration info
- `traceroute` - Network path tracing

---

## ⚖️ Legal Notice

**FOR EDUCATIONAL AND AUTHORIZED TESTING ONLY**

These tools should only be used:
- ✅ On your own infrastructure
- ✅ With explicit written permission
- ✅ For authorized penetration testing
- ✅ For educational purposes

**NEVER use these tools:**
- ❌ Against systems you don't own
- ❌ Without proper authorization
- ❌ For malicious purposes
- ❌ To violate laws or regulations

Unauthorized use may violate:
- Computer Fraud and Abuse Act (CFAA)
- Computer Misuse Act
- Local and international laws

**You are responsible for your actions.**

---

## 🤝 Contributing

### Adding New Tools

1. Add tool function to `pkg/tools/console.go`
2. Add case in switch statement
3. Update help message
4. Add documentation here
5. Update STATUS.md
6. Add tests if applicable

### Improving Existing Tools

1. Enhance features
2. Improve error handling
3. Add more output formats
4. Optimize performance
5. Update documentation

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 📞 Support

### Getting Help

- 📖 Read this documentation
- 🐛 Report bugs via GitHub Issues
- 💬 Ask questions via GitHub Discussions
- 📧 Contact maintainer

### Feature Requests

We welcome suggestions for:
- New tools
- Enhanced features
- Better output formats
- Performance improvements

---

**Maintained By**: Muhammad Thariq  
**Copyright**: © 2025 Muhammad Thariq  
**License**: MIT with Educational Use Terms  
**Last Updated**: December 2025

---

**Status**: All 7 tools fully implemented ✅  
**Quality**: Production-ready  
**Platform Support**: Linux, macOS, Windows
