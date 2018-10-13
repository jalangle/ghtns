---
category: tech
---

This is a cautionary tale of unintentional data usage.

I have Comcast as my ISP.  On my current plan there are 1024GBs of data usage every month.

My data usage over the last 6 months is as follows.

| Month | Usage | 
-----------------
| April	| 791GB |
| May   | 744GB |
| June  | 621GB |
| July  | 729GB |
| Aug   | 724GB |
| Sept  | 1190GB|

You'll notice that September spiked. The mean usage before that is 721.8GB. That spike also
is 166GB over the 1024GB cap. Luckily, I don't have to pay for the overage this time but after 
2 occurances, then it costs $10 per 50GB).

Anyways, this spike bothered me so I started digging in to things. My Ubiquiti hardware allows
for some digging in to where usage is coming from so I poked around and nothing seemed out of
the ordinary.

I was at a loss.

Then I remembered a conversation I had with a coworker on Sept 17th which caused me to check
the "Enable periodic speed test" box at every 30 minutes.  I wanted to generate a pretty graph
so that he could see what my network experience with Comcast looked like.

So I grabbed a command line speed test thing to see what speedtest downloads looked like.

```
bash$ time speedtest --no-upload
Retrieving speedtest.net configuration...
Testing from Comcast Cable (98.203.220.208)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by CenturyLink, Inc (Seattle, WA) [22.39 km]: 22.882 ms
Testing download speed................................................................................
Download: 193.00 Mbit/s
Skipping upload test

real	0m41.250s
user	0m1.281s
sys	0m1.009s
```

I ran it two more times with download speeds of 224.9 and 204.6Mb for an average of 207.5Mb.  Okay.  The time was always 41s and change.  Now, how much data is this pulling? 207.5Mb for 41s is 8507.5Mb or 1,063MB.  For giggles, I created a 1.1GB file on my webserver and it pulled down in right at a minute and its hosted in a
much different part of the country.  So 41S for roughly 1GB of data doesn't seem too bad.

But I'd configured it to do this every 30 minutes.  So my speedtest configuration was pulling 1GB of data 24 times a day and it did it for 12.5 days.  Thats 300GB of data on average.

The numbers off my cloudkey say the speedtest stats run more like in the 230s on average.  So if I pulled 230Gb for 41s thats 1.18GB of data for 354GB of data.

I'm happy to assume the reality is somewhere in between but I don't think it makes much difference.  When you look at 1190GB of usage-300 you're down to 890GB which puts me under the cap and much closer to inline with
previous months.  

So after doing this back of the napkin math, I obviously chose to shut off this option to see what would happen.

Now, my billing cycle runs from the 1st of the month to the end (shocker, I know.) So I've been keeping an eye on the data used so far.

|  Date | Used  | Monthly Avg per Day | Avg since last data point |
-------------------------------------------------------------------
| 10/10	| 488GB	| 48.8GB 			  | 48.8GB                    |
| 10/12	| 565GB | 47.1GB 			  | 38.5GB                    |


