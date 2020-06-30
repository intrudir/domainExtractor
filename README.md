# domainExtractor
Best effort attempt to extract all possible domains and subdomains / FQDNs from a specified file

<h1>Installation:</h1>

```bash
git clone https://github.com/intrudir/domainExtractor.git
```

<h1>Usage Examples:</h1>
Run script without args to see usage

```bash
python3 domainExtractor.py
usage: domainExtractor.py [-h] [-f INPUTFILE] [-u URL] [-t TARGET] [-v]

This script will extract domains from the file you specify and add it to a final file

optional arguments:
  -h, --help            show this help message and exit
  -f INPUTFILE, --file INPUTFILE
                        Specify the file to extract domains from
  -u URL, --url URL     Specify the web page to extract domains from. One at a time for now
  -t TARGET, --target TARGET
                        Specify the target top-level domain you'd like to find and extract e.g. uber.com
  -v, --verbose         Enable slightly more verbose console output

```
<h2> Matching a specified target domain </h2>
Specify your source and a target domain to search for and extract. 

<h3>Extracting from a file</h3>
Using any file with text in it, extracting all domains with yahoo.com as the TLD.

```bash
python3 domainExtractor.py --file test.html --target yahoo.com
```
It will extract, sort and dedup all domains that are found.

![image](https://user-images.githubusercontent.com/24526564/85906292-dd7e8a80-b7db-11ea-84b2-dbb7df9bec74.png)

<h5>Example output:</h5>

![image](https://user-images.githubusercontent.com/24526564/85906625-dd32bf00-b7dc-11ea-9c22-415c76c01ae4.png)

<h3> Extracting from a web page </h3>
Pulling data directly from Yahoo.com's homepage extracting all domains with 'yahoo.com' as the TLD.

```bash
python3 domainExtractor.py -u https://yahoo.com --target yahoo.com
```

![image](https://user-images.githubusercontent.com/24526564/86146580-68a29d80-bac6-11ea-8457-7d73b2a6d1c4.png)


<h2> Specifying all domains </h2>
You can either omit the --target flag completely, or specify 'all' and it will extract all domains it finds (at the moment .com, .net, .org, .tv, .io)

```bash
python3 domainExtractor.py --file test.html --target all
```

![image](https://user-images.githubusercontent.com/24526564/85906901-c50f6f80-b7dd-11ea-8fea-e7adad964d97.png)

<h5>Example output:</h5>

![image](https://user-images.githubusercontent.com/24526564/85907449-81b60080-b7df-11ea-9c10-d389b3558605.png)

<h1>Domains not previously found</h1>
If you run the script again while checking for the same target, a few things occur: 
<br>1) if you already have a final file for it it will notify you of domains you didnt have before
<br>2) It will append them to the final file
<br>3) It will also create a new file with the date and log them in there with the time.

<br>This allows you to check the same target across multiple files and be notified of any new domains found!

<h3>Example: extracting from Amass and Assetfinder output files</h3>

![image](https://user-images.githubusercontent.com/24526564/85907726-7f07db00-b7e0-11ea-820f-8912d779c065.png)

I first use it against my Amass results, then against my Assetfinder results. 
<br>The script will sort and dedup as well as notify me of how many new, unique domains came from assetfinder's results.

![image](https://user-images.githubusercontent.com/24526564/85907913-27b63a80-b7e1-11ea-8d8b-c887a19d61ca.png)

It will add them to the final file as well as log just the new ones to a file with the date and time.

![image](https://user-images.githubusercontent.com/24526564/85908016-706df380-b7e1-11ea-8986-fe96181c6b6d.png)


