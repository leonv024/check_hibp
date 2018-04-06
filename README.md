![alt text](http://leonvoerman.nl/coding/hibp.png)

# hibp.py
Check haveibeenpwned for account breaches with a list of usernames

Show of breached or not, where you got breached and date of first and latest breach.

Installation:
```Shell
pip install -r requirements.txt
```

Usage:
```Shell
python hibp.py -f ~/Documents/emails.txt -s ~/Documents/result.txt -b 2
```

Features:
```Shell
usage: hibp.py [-h] [-f FILE] [-s SAVE] [-b BURST] [-c CHECK]

Check accounts on haveibeenpwned.com

optional arguments:
  -h, --help            show this help message and exit
  -f FILE, --file FILE  Location to a list with account names or Email
                        addresses. Example: -f ~/Documents/accounts.txt
  -s SAVE, --save SAVE  Save results to a file. Example: -s
                        ~/Documents/result.txt
  -b BURST, --burst BURST
                        Set sleep time (default: 1.5). Sleep time of 0 can
                        trigger Cloudflare protection and/or false positive
                        results.
  -c CHECK, --check CHECK
                        Check a single account for breaches
lv-laptop@lv-laptop:~/Documents/directories/programmeren/py
```


Base Code:
```Python
check = requests.get('https://haveibeenpwned.com/api/v2/breachedaccount/%s' % account)
```

```Python
if check.status_code == 200:
   return ('%s \033[31m[BREACHED]\033[0m %s -> %s -> %s') % (account.ljust(50), breachdate.rjust(15), latestbreach, breachedon)
```
