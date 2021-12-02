# --- Day 1 | Save The Gifts [Web Exploitation] ---
## --- Story ---
The inventory management systems used to create the gifts have been tampered with to frustrate the elves. It's a night shift, and McStocker comes to McSkidy panicking about the gifts all being built wrong. With no managers around to fix the issue, McSkidy needs to somehow get access and fix the system and keep everything on track to be ready for Christmas!

## --- Learning Objectives ---
1. What is an IDOR vulnerability?
2. How do I find and exploit IDOR vulnerabilities?
3. Challenge Walkthrough.
   
---

## --- What is an IDOR vulnerability? ---
IDOR stands for Insecure Direct Object Reference and is a type of access control vulnerability. An access control vulnerability is when an attacker can gain access to information or actions not intended for them. An IDOR vulnerability can occur when a web server receives user-supplied input to retrieve objects (files, data, documents), and too much trust has been placed on that input data, and the web application does not validate whether the user should, in fact, have access to the requested object. It is usually found in **query component data**, **post variables**, and **cookies**.

## --- Questions --- 
1. **After finding Santa's account, what is their position in the company?**
    - The Boss!
2. **After finding McStocker's account, what is their position in the company?**
    - Build Manager
3. **After finding the account responsible for tampering, what is their position in the company?**
    - Mischief Manager
4. **What is the received flag when McSkidy fixes the Inventory Management System**?
    - THM{AOC_IDOR_2B34BHI3}


# Solve
## Methodology
- Use the query component data to traverse between all users

Since the story is about Santa and his elves and we need to find Santa's account we can assume he will be the `1` user_id. `1` representing a admin/root of the system. 

![Santa's Account](/images/santa.PNG)

Next we need to find another user's account named McStocker. To do this we just need to traverse through the user_id's ranging from *1-20*. Once we do this we find the his user_id is `3`.

![McStocker's Account](/images/mcstocker.PNG)

To find the person responible for tampering we follow the same process as before and find that the Grinch is user_id `9`.

![The Grinch's Account](/images/grinch.PNG)

To fix the Inventory Management System we must revert all of the Grinches `SKU Changes`. Once we do that we recieve the flag.

![McSkidy's Flag](/images/mcskidy.PNG)