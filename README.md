# 🕵️ AbuseIPDB Bulk Checker

A simple Bash automation I use when dealing with a bulk list of suspicious IP addresses.  
It queries the [AbuseIPDB API](https://www.abuseipdb.com/) and saves summarized results to a text file.

---

## ⚙️ Setup

1. Create an account on [abuseipdb.com](https://www.abuseipdb.com/).  
2. Obtain your personal API key.  
3. Add it to the script under the variable `API_KEY`.

---

## 🧠 Usage

### Single IP
```bash
check-abuseip 1.2.3.4
```

### Bulk from file
You can move the script to your system path to use it globally:
```bash
sudo mv check-abuseip /usr/bin/
```

Then pipe IPs via standard input:
```bash
cat suspicious_ips.txt | check-abuseip
```

---

## 📄 Output

The script displays formatted results in your terminal and also creates a file named  
`abuse-ip-results.txt` in the current directory.

**Example Output**
```
104.207.48.140 {Report: 0, Abuse: 0, Country: KR, LastReported: 2025-04-22T16:42:07+00:00}
139.162.155.181 {Report: 0, Abuse: 0, Country: DE, LastReported: 2024-10-30T16:50:56+00:00}
144.24.2.212 {Report: 0, Abuse: 0, Country: US, LastReported: 2025-03-21T22:00:19+00:00}
185.202.74.245 {Report: 2, Abuse: 2, Country: GB, LastReported: 2025-09-18T15:34:47+00:00}
196.189.144.191 {Report: 4, Abuse: 0, Country: ET, LastReported: 2025-08-26T22:06:23+00:00}
65.111.13.239  {Report: 2, Abuse: 14, Country: US, LastReported: 2025-10-03T19:13:31+00:00}
65.111.20.48   {Report: 0, Abuse: 0, Country: US, LastReported: 2025-01-01T05:04:04+00:00}
```

---

## 🧩 Notes

- Requires `curl` and `jq` to be installed.
- API free tier limits apply (see [AbuseIPDB API Docs](https://docs.abuseipdb.com/)).
- You can easily modify the script to output JSON, CSV, or filter based on abuse score.
- Example snippet for quick testing:
  ```bash
  echo "8.8.8.8" | check-abuseip
  ```

---

## 💡 Example Script Header

```bash
#!/bin/bash
# AbuseIPDB Bulk Checker
# Author: Natan Hailu (Geez Security)
# Description: Checks IP reputation on AbuseIPDB using the public API

API_KEY="YOUR_API_KEY_HERE"
```

---

**⭐ Pro Tip:**  
Combine this with cron or your SIEM log parser to automatically vet new IPs detected during incident response.
