# HTTP Gauge # 

`httpgauge` is a benchmarking tool for HTTP1.0 and 1.1 web servers.  It optionally supports and correctly handles HTTP keep alive requests.  

### Requirements ###
 * python 3.3+ is required.
 * The `asyncio` must be installed for python 3.3 whereas it is included in python 3.4+
 

### Installation ###


### Usage ###

Make a total of 1000 requests to `http://localhost` with 100 concurrent requests

    `httpgauge -n 1000 -c 100 http://localhost`
    
Same as above except use HTTP Persistent Connections (Keep Alive)

    `httpgauge -k -n 1000 -c 100 http://localhost`
    
Print help message

    `httpgauge -h`
