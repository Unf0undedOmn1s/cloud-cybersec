# Extract HTTP hosts and User-Agents without payloads (no credentials/cookies)
```bash
tshark -r capture.pcap -Y "http" -T fields -e frame.time -e ip.src -e http.host -e http.user_agent -E header=y -E separator=, > http_analysis.csv
```
# Output http_analysis.csv:
```bash
frame.time,ip.src,http.host,http.user_agent
"2025-18-07 12:00:01",192.0.2.1,example.com,"Mozilla/5.0 (Windows NT 10.0)"
"2025-18-07 12:00:02",192.0.2.2,api.example.com,"curl/7.68.0"
```
# *GitHub-Safe*
1. **No Payloads**: Only extracts headers (no POST data/cookies)  
2. **Test IPs**: Uses `192.0.2.0/24` (reserved for documentation)  
3. **CSV Format**: Easy to audit/review before committing

### Wireshark & Tshark Guide
#*A privacy-focused packet analysis reference*

## Basic Capture Syntax
`tshark -i <interface> -f <capture_filter> -w <output_file>`
- Parameters:
  - -i: Network interface to capture from "-i eth0" or `-i any`
  - -f: BPF capture filter (pre-capture filtering) `-f port 80`
  - -w: Save raw packets to file `-w capture.pcap`
  - -c: Stop after N packets `-c 1000`
  - -a: Auto-stop condition (duration/filesize) `-a duration:60 (1 minute)`

## Post-Capture Analysis
`tshark -r <input_file> -Y <display_filter> -T <output_format>`
- Parameters:
  - -r: Read from capture file `-r capture.pcap`
  - -Y: Display filter (post-capture filtering) `-Y "http.request.method==GET"`
  - -T: Output format (json, text, etc) `-T json`
  - -e: Extract specified field (with -T fields) `-e ip.src -e http.host`
  - -E: Format options for -T fields `-E separator=, (CSV output)`

## Security Analysis Examples
1. Detect Port Scans
  - `tshark -r scan.pcap -Y "tcp.flags.syn==1 and tcp.flags.ack==0" \
  -T fields -e ip.src -e tcp.dstport | sort | uniq -c`
2. Extract DNS Queries
  - `tshark -r traffic.pcap -Y "dns" -T fields \
  -e frame.time -e ip.src -e dns.qry.name `
3. Find HTTP Requests
  - `tshark -r web.pcap -Y "http.request" -T fields \
  -e ip.src -e http.host -e http.request.uri`
