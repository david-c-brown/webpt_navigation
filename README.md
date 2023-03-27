# WebPT: Kind of isn't like super fun to use
Navigating WebPT with Selenium to gather visit volume accurately

## problem:
1. WebPT analytics is slow, and occasionally inaccurate, and doesn't report visits under a certain threshold of fields logged (and that threshold seems to differ). To maintain an adequate real time understanding of our clinic's performance, we need  all visit information to be as accurate and as up to date as possible. 
1a. doing this by hand is a minimum 3 hour long process, that is highly susceptible to human error. Often it takes longer and the longer it takes the more likely errors are made.
2. WebPT has a 2 stage login, and injects schedule events through Javascript, so using bs4 is out of the question despite being the faster method otherwise.
3. WebPT fails to load items about 20% of the time on a new calendar. It also fails to read when a checkbox is clicked 10% of the time.

## solution:
1. Build a simple script to count items in the same way we do it by hand
2. Use Selenium to extract the key elements from the JS injected calendar.
3. Overengineer checkbox clicking.

## process:
* First iteration: Initialize driver, by hand run 2 functions to get the count, copy the output into the main worksheet. repeat n of week * n of pt per clinic * n of clinics
* Second: build out the backward > forward > forward navigation and copy that over repeat n of pt per clinic * n of clinics
* Third: becomes what we see now. 
* Next: figure out an accurate method of gauging utilization. For now, the PTO counter is my reminder to double check their availablity, but the weaknesses of this approach are just barely above nothing.

## usage for others:
* build a config file with relevant info (user, pw, clinics)
* confirm the values in both value_counts() functions and the count_evals() function. Our clinics differ pretty widely on how they choose to log things.

