- common type of vulnerability associates with business logic flaws
- generally occurs when two process want to access same resources
- occur when website process request concurrently without adequate safeguard
- when two thread interact with same data collision occurs that cause unintended behaviour in application
- uses carefully timed requests to cause intentional collisions and exploit this unintended behavior for malicious purposes.
---
- the period of time in which a collision is possible is called race window
- this could be fraction of seconds between two interaction with the database
- impact of race condition is heavily dependent on the application and specific functionality in which it occurs

### Limit Overrun  Race Condition
- well known race condition 
- enables us to exceed some kind of limit imposed by business logic of application
![[Pasted image 20260220212223.png]]
- As you can see, the application transitions through a temporary sub-state
- that is, a state that it enters and then exits again before request processing is complete. 
- In this case, the sub-state begins when the server starts processing the first request, and ends when it updates the database to indicate that you've already used this code.
- This introduces a small race window during which you can repeatedly claim the discount as many times as you like.

There are many variations of this kind of attack, including:

- Redeeming a gift card multiple times
- Rating a product multiple times
- Withdrawing or transferring cash in excess of your account balance
- Reusing a single CAPTCHA solution
- Bypassing an anti-brute-force rate limit
Limit overruns are a subtype of so-called "time-of-check to time-of-use" (TOCTOU) flaws. 

>[!note]
>we can use burp repeater to exploit limit over run race condition

- we can detect and exploit limit overrun race condition by
1. Identify a single-use or rate-limited endpoint that has some kind of security impact or other useful purpose.
2. Issue multiple requests to this endpoint in quick succession to see if you can overrun this limit.

- The primary challenge is timing the requests so that at least two race windows line up, causing a collision
- this window is often just milliseconds and can be even shorter