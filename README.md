TLX
==========
A simple TLS proxy terminator written in Go.

How it works
============
- listens on a custom port
- offloads the incoming tls connections
- forwards the offloaded tls connections to the backend server

How to install
===============
- Download a release file from [here](https://github.com/alash3al/tlx/releases)
- Extract the file from the archive
- open your Command Line Interface in the working directory of the extraction process
- run `./tlx --help` to test it

Usage
=========

#### Creating Cert & Key
```bash
# the key
openssl ecparam -genkey -name secp384r1 -out server.key

# the cert
openssl req -new -x509 -sha256 -key server.key -out server.crt -days 3650
```

#### Run
```bash
# listen on ":9000" and forward the requests to "localhost:8000"
# then set the tls cert and key
./tlx -backend "localhost:8000" -listen ":9000" -cert "./server.crt" -key "./server.key"
```
