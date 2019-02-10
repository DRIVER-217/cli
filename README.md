# GNQL Help File

Basic Usage

    python3 gnql.py 'query'

Advanced Usage
    
    python3 qnql.py -v -q 'Query' -o OutputFormat -f OutputFile -t QueryType
    
    -v Verbose
    -q Query
    -o Output Format 
    -f Output File
    -t Query Type 

## Installation

python3 -m pip install -r requirements.txt

    dict2xml
    pydoc

## Output Formats

| Format | Description |
|--------|-------------|
| txt    | Pretty Text |
| csv    | A CSV File  |
| xml    | XML Output  |
| json   | JSON Output |
| raw    | Raw JSON from the Greynoise API |

## Query Types
| Type    | Description |
|---------|-------------|
| quick   | Check whether a given IP address is “Internet background noise”, or has been observed scanning or attacking devices across the Internet. |
| raw     | Gives all relevant information about an IP / Query |
| context | Get more information about a given IP address. Returns time ranges, IP metadata (network owner, ASN,reverse DNS pointer, country), associated actors, activity tags, and raw port scan and web request information. |
| multi   | Check whether a list of given IP addresses are “Internet background noise”, or have been observed scanning or attacking devices across the Internet. |
| bulk    | Get all noise IPs from today generated by internet scanners, search engines, and worms
| date    | Get all noise IPs from on a given day generated by internet scanners, search engines, and worms. Date format is "2018-01-01". |
| actors  | Get the names and IP addresses most up-to-date labeled actors scanning and crawling the Internet. |


## Example Queries

Basic IP Query

    python3 gnql.py 185.156.177.44 

Quick Search

    python3 gnql.py -q 185.156.177.44 -t quick

Raw Search

    python3 gnql.py -q 185.156.177.44

Date Example with pager

    python3 gnql.py -q 2018-02-07 -t date -o txt

Lots of Paths

    python3 gnql.py -q 38.91.107.213 -t context -o txt

Lots of Ports 

    python3 gnql.py -q 185.156.177.11 -t context -o txt

Verbose Output

    python3 gnql.py -q 185.156.177.11 -t context -o txt -v

Log Parse Test (for when multi works)

    python logparse.py test.log

