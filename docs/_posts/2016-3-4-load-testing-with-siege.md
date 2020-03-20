---
title: Load testing with Siege
categories:
  - tech
tags:
  - Siege
  - testing
---

We <a href="/getting-started-with-siege-on-mac-os-x">previously installed Siege</a>, and we are now ready to play with it a bit. Consider the following command:

```
siege -c5 -d5 -t10S http://localhost:8000/list
```

**-cNUM** is the number of concurrent users. In the example it is set to 5, and is 10 by default if not set.

**-dNUM** is any random number of seconds for the time delay (between 1 and _NUM_) that each "user" will sleep for between requests.

**-tNUMm** is the duration of the test. _m_ indicates the time unit and can be S for seconds, M for minutes or H for hours

In the above example, we are putting the server under siege with 3 concurrent users sending requests for 10 seconds, and being idle for 1 - 5 seconds between each request.

Below is the result when running the test against a Node.js app which does some queries to MongoDB to list some items. The templating engine used here is Jade with the caching mechanism enabled.

```
Lifting the server siege...
Transactions:		          18 hits		//number of server hits
Availability:		      100.00 %			//server was fully available
Elapsed time:		        9.63 secs		//duration of test
Data transferred:	        0.12 MB			//data transferred to every siege simulated user and includes header information
Response time:		        1.46 secs		//average time taken to respond to each user's requests
Transaction rate:	        1.87 trans/sec	//average number of transactions handled by server
Throughput:		        0.01 MB/sec			//average number of bytes transferred every second from the server to all the simulated users
Concurrency:		        2.73			//average number of simultaneous connections, a number which rises as server performance decreases
Successful transactions:          20		//number of times the server returned a code less then 400. Redirects are considered successful transactions.
Failed transactions:	           0		//number of transactions which didn't go through
Longest transaction:	        4.25
Shortest transaction:	        0.00
```

It is also possible to load test using a list of urls, and make the simulation closer to real cases. For instance:

```
siege -c5 -d5 -t10S -i -f sites.txt
```

where

**-i** is an option for internet user simulation, and hits URLs from the file randomly.

**-f** indicates that we should get the URLs from the file sites.txt. Each URL in the file should be on a new line.

There are many more options available which can be used, if required, based on different test cases.

**-b** is usually used to ignore any delay between requests for benchmarking purposes. If omitted the default is set to 1 second.

Type ```siege``` to get more details about the other options. More information can also be found <a href="https://www.joedog.org/siege-manual" target="_blank">here</a>.
