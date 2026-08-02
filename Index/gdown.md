

# gdown [Link](https://github.com/wkentaro/gdown)

Downloading public files from Google Drive with curl or wget doesn't work — Google serves a confirmation page for large files, and the URL formats are a mess.


## Install

```pip install gdown```

## Quick Start

### Just paste a Google Drive URL
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ```

### Or copy-paste a share link directly
```gdown 'https://drive.google.com/file/d/0B9P1L--7Wd2vU3VUVlFnbTgtS2c/view?usp=sharing'```

## Files

### Download by URL
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ```

### Download by file ID
```gdown 1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ```

### Download from a share link
```gdown 'https://drive.google.com/file/d/0B9P1L--7Wd2vU3VUVlFnbTgtS2c/view?usp=sharing'```

### Save to a specific path
```gdown https://drive.google.com/uc?id=0B9P1L--7Wd2vU3VUVlFnbTgtS2c -O /tmp/spam.txt```

### Resolve the filename (with its real extension) without downloading
```gdown https://drive.google.com/uc?id=0B9P1L--7Wd2vU3VUVlFnbTgtS2c --json```

## Folders

### Download an entire folder
```gdown https://drive.google.com/drive/folders/15uNXeRBIhVvZJIhL4yTw4IsStMhUaaxl -O /tmp/folder --folder```

### List folder contents as a JSON array (each entry has url and path)
```gdown https://drive.google.com/drive/folders/15uNXeRBIhVvZJIhL4yTw4IsStMhUaaxl --folder --json```

## Google Docs, Sheets, Slides

### Download a Google Slides file (default: pptx)
```gdown "https://docs.google.com/presentation/d/15umvZKlsJ3094HNg5S4vJsIhxcFlyTeK/edit?usp=sharing"```

### Export as PDF instead
```gdown "https://docs.google.com/presentation/d/15umvZKlsJ3094HNg5S4vJsIhxcFlyTeK/edit" --format pdf```

## Resume, speed limit, proxy

### Resume a partially downloaded file
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --continue```

### Limit download speed
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --speed 10MB```

### Download via proxy
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --proxy http://proxy:8080```

## Other options

### Skip TLS certificate verification
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --no-check-certificate```

### Don't use cookies from ~/.cache/gdown/cookies.txt
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --no-cookies```

### Use a custom User-Agent
```gdown https://drive.google.com/uc?id=1l_5RK28JRL19wpT22B-DY9We3TVXnnQQ --user-agent "MyApp/1.0"```

### Pipe to stdout

```gdown https://github.com/wkentaro/gdown/archive/refs/tags/v4.0.0.tar.gz -O - --quiet | tar zxvf -```

## Any URL

gdown also works with regular URLs, not just Google Drive:
```gdown https://httpbin.org/ip -O ip.json```