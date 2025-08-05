# Custom Connector & Authorization Header
Custom Connector + Local Gateway + Authorization Header

# Description
Working with a client, I needed to consume or call an internal web API.

I thought, "It is just a custom connector with a local gateway enabled, No big deal."

<img width="1074" height="787" alt="image" src="https://github.com/user-attachments/assets/96646599-3ccb-44d3-96b5-990de3e16342" />

# Issue
But when I tried to set up the “Authorization” header I got this error.

<img width="1139" height="276" alt="image" src="https://github.com/user-attachments/assets/ad867adf-1a36-4ff5-8dc9-a32e1ec852bb" />

Basically, the problem is that we cannot configure the Authorization header in the Gateway-enabled connector.

After a research , I found some solutions :
* Changing the authorization mode: Not possible.
* Using a custom intermediate API (wrapper): Doable, but time-consuming.
* Implementing a custom policy: Sounds good.

# Fix
I got implemented  the “Policy” option, basically, I am inserting the Token/Value in a header “token” (as a parameter because is created in other place).
<img width="1197" height="865" alt="image" src="https://github.com/user-attachments/assets/aeb48000-53ba-429a-bc50-5b0fcfbf39f4" />


Then, I have used the   “Set HTTP header” policy, this policy  takes that value and set the “Authorization”  header on the fly.

And that's it, the Authorization header will be sent correctly.
