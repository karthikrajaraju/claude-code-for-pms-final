# Brief: fix for responders going quiet after 4.2 (first draft)

**For:** Helen Achebe, Director of Product
**From:** PM, Rook Dispatch

## Problem
Since 4.2, four responders have almost stopped getting pings. The Undertow
went from about 9 jobs a week to 0. The cause is in routing: the ping wait
was cut from 90 to 60 seconds, a missed ping is scored the same as a
turned-down one, and the score never recovers.

## Fix
1. Score a missed ping lower than a turned-down one.
2. Let the recent-acceptance score ease back over time.
3. Give a little extra time once a responder has opened the ping.
4. Show handlers when a responder is getting far fewer pings than usual.

## Success
- Missed pings back to pre-4.2 levels (about 2–3%).
- The four quiet responders back to normal work within a month.

## Owners
Wen Li (routing), Marcus Oyelaran (engineering), Sofia Marino (console).
