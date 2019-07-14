# bbpot
phpBB Honeypot

## Installation
bbpot supports go modules. 

`go get github.com/d1str0/bbpot`

`go build`

## Running bbpot
`./bbpot -c config.toml`

## Configuration
`config.toml.example` contains an example of *all* currently available
configuration options.

### phpBB
    [phpbb]
    port = 80

`port` allows you to set the http port to listen on. Currently, this is only ever
served over http. Future versions will support https.

### hpfeeds
    [hpfeeds]
    enabled = true
    host = "hpfeeds.threatstream.com"
    port = 10000
    ident = "bbpot"
    auth = "somesecret"
    channel = "bbpot.events"
    meta = "phpBB scan event detected"

hpfeeds can be enabled for logging if wanted. Supply host, port, ident, auth,
and channel information relevant to an hpfeeds broker you want to report to. 

`meta` provides a static string to send in every hpfeeds request. Could be used
to differentiate phpBB versions hosted by honeypot or used to differentiate
bbpot data in busy hpfeeds channels.

### Fetch Public IP
    [fetch_public_ip]
    enabled = true
    urls = ["http://icanhazip.com/", "http://ifconfig.me/ip"]


If enabled, bbpot will attempt to fetch the public IP of itself from the listed
URLs. If enabled and no public IP can be fetched, bbpot will quit.

