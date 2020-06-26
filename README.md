# domainExtractor
Best effort attempt to extract all possible domains / FQDNs from a specified file

<h1>Installation:</h1>

```bash
git clone https://github.com/intrudir/domainExtractor.git
```

<h1>Usage:</h1>
Run script without args to see usage

```bash
python3 domainExtractor.py
usage: domainExtractor.py [-h] [--file INPUTFILE] [--target TARGET] [--verbose]

This script will extract domains from the file you specify and add it to a final file

optional arguments:
  -h, --help        show this help message and exit
  --file INPUTFILE  Specify the file to extract domains from
  --target TARGET   Specify the target top-level domain you'd like to find and extract e.g. uber.com
  --verbose         Enable slightly more verbose console output

```
<h2> Matching a specified target domain </h2>
Specify a file and a target domain to search for and extract from the file. The test.html file I am using is just the source HTML of yahoo.com index page.

```bash
python3 domainExtractor.py --file test.html --target yahoo.com
```
It will extract, sort and dedup all domains that are found.

![image](https://user-images.githubusercontent.com/24526564/85906292-dd7e8a80-b7db-11ea-84b2-dbb7df9bec74.png)

<h3>Example output:</h3>

![image](https://user-images.githubusercontent.com/24526564/85906625-dd32bf00-b7dc-11ea-9c22-415c76c01ae4.png)

<h2> Specifying all domains </h2>
Specifying 'all' as the target extracts all domains it finds (at the moment .com, .net, .org, .tv, .io)

```bash
python3 domainExtractor.py --file test.html --target all
```

![image](https://user-images.githubusercontent.com/24526564/85906901-c50f6f80-b7dd-11ea-8fea-e7adad964d97.png)






