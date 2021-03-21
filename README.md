# Knock Subdomain Scan v5.0.0

Knockpy is a python tool designed to enumerate subdomains on a target domain through dictionary attack.

### Very simply
```$ knockpy domain.com```

# Install

```$ git clone https://github.com/guelfoweb/knock.git```

edit ```knockpy/config.json```
add your ```virustotal API_KEY```
```
"api": {
		"virustotal": "YOUR VIRUSTOTAL API_KEY HERE"
	},
```
save.

```$ sudo python setup.py install```

# Knockpy -h

```
$ knockpy -h
usage: knockpy [-h] [-v] [--no-local] [--no-remote] [--no-http] [-w WORDLIST] [-o FOLDER] [-t SEC] domain

positional arguments:
  domain         target to scan

optional arguments:
  -h, --help     show this help message and exit
  -v, --version  show program's version number and exit
  --no-local     local wordlist ignore
  --no-remote    remote wordlist ignore
  --no-http      http requests ignore
  -w WORDLIST    wordlist file to import
  -o FOLDER      report folder to store json results
  -t SEC         timeout in seconds
```

# Usage

### Full scan
```$ knockpy domain.com```

- Attack type: **dns** + **http(s)** requests
- Knockpy uses internal file ```wordlist.txt```. If you want to use an external dictionary you can use the ```-w``` option and specify the path to your dictionary text file.
- Knockpy also tries to get subdomains from ```google```, ```duckduckgo```, and ```virustotal```. The results will be added to the general dictionary.
- It is highly recommended to use a [virustotal](https://virustotal.com/) ```API_KEY``` which you can get for free. The best results always come from ```virustotal```.
- But, if you only want to work with local word lists, without search engines queries, you can add ```--no-remote``` to bypass remote recon.

### Fast scan
```$ knockpy domain.com --no-http```

- Attack type: **dns**
- DNS requests only, no http(s) requests will be made. This way the response will be much faster and you will get the IP address and the Subdomain.
- The subdomain will be cyan in color if it is an ```alias``` and in that case the real host name will also be provided.

### Set timeout
```$ knockpy domain.com -t 5```

- default timeout = ```3``` seconds.

### Show report
```$ knockpy domain.com_yyyy_mm_dd_hh_mm_ss.json```
- Show the report in the terminal.

### Output folder

```$ knockpy domain.com -o /path/to/new/folder```

- All scans are saved in the default folder ```knock_report``` that you can edit in the ```config.json``` file. 
- Alternatively, you can use the ```-o``` option to define the new folder path.

# License

Knockpy is currently under development by [@guelfoweb](https://twitter.com/guelfoweb) and it's released under the GPL 3 license.
