multi-origin-proxy
==================

HTTP reverse proxy server with multiple origins.

The intent of this server is to combine multiple origins which are not easily duplicated, for example Amazon S3 buckets containing millions of files.

Usage
-----

		moproxy --loglevel=WARN --port=${PORT} ${ORIGIN_1} ${ORIGIN_2}

Example
-------

		moproxy --loglevel=WARN --port=9090 http://bucket1.example.com http://bucket2.example.com

In the example above, a request for "/robots.txt" on port 9090 will first attempt to reverse-proxy http://bucket1.example.com/robots.txt . If that location fails, http://bucket2.example.com/robots.txt will be attempted. If all origins fail, a 404 status will be returned.

History
-------

I created this app in my spare time to replace an Apache+PHP implementation for my work QA environment. As of this writing in March 2014, my evaluation deployment built with Go 1.1 in November 2013 has been running continuously for over 3 months and has served almost 5 million requests.

