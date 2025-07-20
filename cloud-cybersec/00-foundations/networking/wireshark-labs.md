# Extract HTTP hosts and User-Agents without payloads (no credentials/cookies)
tshark -r capture.pcap -Y "http" -T fields -e frame.time -e ip.src -e http.host -e http.user_agent -E header=y -E separator=, > http_analysis.csv
