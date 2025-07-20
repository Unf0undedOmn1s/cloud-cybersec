# Extract HTTP hosts and User-Agents without payloads (no credentials/cookies)
```bash
tshark -r capture.pcap -Y "http" -T fields -e frame.time -e ip.src -e http.host -e http.user_agent -E header=y -E separator=, > http_analysis.csv
```
# Output http_analysis.csv:
```bash
frame.time,ip.src,http.host,http.user_agent
"2023-11-01 12:00:01",192.0.2.1,example.com,"Mozilla/5.0 (Windows NT 10.0)"
"2023-11-01 12:00:02",192.0.2.2,api.example.com,"curl/7.68.0"
```
