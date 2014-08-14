# HTTP Gauge #

`httpgauge` is a benchmarking tool for HTTP1.0 and 1.1 web servers.  It optionally supports and correctly handles HTTP keep alive requests.  

### Requirements ###
 * python 3.3+ is required.
 * The `asyncio` must be installed for python 3.3 whereas it is included in python 3.4+
 

### Installation ###
If you install python 3.4, you're all set no other software is required. 

If you have python3.3 installed (if you're running ubuntu, you likely do, type `python3 -V` to confirm), then you need `asyncio`.  Make sure you have pip3 installed via `apt-get install -y python3-pip` then `sudo pip3 install asyncio` and you're all set.

### Caveats ###
 * `httpgauge` only supports http, not https
 * `httpguage` is subject to [python issue 21447](http://bugs.python.org/issue21447) which can cause it to hang to due to a race condition in asyncio.  When this is merged in (likely python3.5), `httpgauge` will be ready for production.  Until then, if it hangs, Ctrl-C and retry. 


### Examples ###

Make a total of 1000 requests to `http://localhost` with 100 concurrent requests

    httpgauge -n 1000 -c 100 http://localhost/index.html
    
Same as above except use HTTP Persistent Connections (Keep Alive)

    httpgauge -k -n 1000 -c 100 http://localhost/index.html
    
Print help message

    httpgauge -h

### Output ###

`httpgauge` will print out a report when finished like the following:

    ================================================================================
    HTTP Gauge 0.1

    Host:                                                      127.0.0.1
    Path:                                                    /index.html

    Total Requests:                                                 5000
    Successful Requests:                                            5000
    Timeouts:                                                          0
    Resets:                                                            0

    Total Time:                                                 1.449597 seconds
    Mean time per successful request:                           0.006710 seconds
    Mean time per request across all requests:                  0.000290 seconds
    Requests per second:                                         3449.23
    ================================================================================

