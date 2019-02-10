# GreyNoise CLI Help File

Basic Usage

    greynoise 'query'

Advanced Usage
    
    greynoise -v -q 'Query' -o OutputFormat -f OutputFile -t QueryType
    
    -v Verbose
    -q Query
    -o Output Format 
    -f Output File
    -t Query Type 

## Installation

python3 -m pip install -r requirements.txt

```
dict2xml
pydoc
```

## Example Output

```
 _____________   ______________
 __  ____/__  | / /_  __ \__  /
 _  / __ __   |/ /_  / / /_  /
 / /_/ / _  /|  / / /_/ /_  /___
 \____/  /_/ |_/  \___\_\/_____/

 ┌───────────────────────────┐
 │       result 1 of 1       │
 └───────────────────────────┘

          OVERVIEW:
 ----------------------------
 IP: 185.156.177.44
 Classification: malicious
 First seen: 2018-05-30
 Last seen: 2019-02-10
 Actor: unknown
 Tags: ['VNC Bruteforcer', 'VNC Scanner']

          METADATA:
 ----------------------------
 Location: Obninsk, Russia (RU)
 Organization: HOSTKEY B.V.
 ASN: AS57043
 OS: Windows 7/8
 Category: hosting

          RAW DATA:
 ----------------------------
 Port/Proto: 5900/TCP
 Port/Proto: 5901/TCP
 ```

## Output Formats

```
| Format | Description |
|--------|-------------|
| txt    | Pretty Text |
| csv    | A CSV File  |
| xml    | XML Output  |
| json   | JSON Output |
| raw    | Raw JSON from the Greynoise API |
```

## Query Types
```
| Type    | Description |
|---------|-------------|
| quick   | Check whether a given IP address is “Internet background noise”, or has been observed scanning or attacking devices across the Internet. |
| raw     | Gives all relevant information about an IP / Query |
| context | Get more information about a given IP address. Returns time ranges, IP metadata (network owner, ASN,reverse DNS pointer, country), associated actors, activity tags, and raw port scan and web request information. |
| multi   | Check whether a list of given IP addresses are “Internet background noise”, or have been observed scanning or attacking devices across the Internet. |
| bulk    | Get all noise IPs from today generated by internet scanners, search engines, and worms
| date    | Get all noise IPs from on a given day generated by internet scanners, search engines, and worms. Date format is "2018-01-01". |
| actors  | Get the names and IP addresses most up-to-date labeled actors scanning and crawling the Internet. |
```

## Example Queries

Basic IP Query
```
greynoise 185.156.177.44 
```

Quick Search
```
greynoise -q 185.156.177.44 -t quick
```

Raw Search
```
greynoise -q 185.156.177.44
```

Date Example with pager
```
greynoise -q 2018-02-07 -t date -o txt
```

Lots of Paths
```
greynoise -q 38.91.107.213 -t context -o txt
```

Lots of Ports 
```
greynoise -q 185.156.177.11 -t context -o txt
```

Verbose Output
```
greynoise -q 185.156.177.11 -t context -o txt -v
```

