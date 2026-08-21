---
base: "[[Tweets.base]]"
Type: Thread
Created: 2022-11-26T13:40:00
Author: hipotermia
Tags:
  - Cybersecurity
Tweet Link: https://twitter.com/hipotermia/status/1596476791354687489
---
> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Yesterday, an old friend sent me an Instagram DM asking me for help for a contest. The "custom link" was a bit weird as it didn't have any path or URL params and when accessing I confirmed it was phishing as there was a fake Instagram login there. 

Thread of how I hacked it👇
> [https://pbs.twimg.com/media/FifO61AWAAEYMhB.png](https://pbs.twimg.com/media/FifO61AWAAEYMhB.png)
> 
> [https://pbs.twimg.com/media/FifO61-WIAETA_g.png](https://pbs.twimg.com/media/FifO61-WIAETA_g.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Just for fun I submitted a blind XSS payload, but I got something way better on the response. The error revealed this request was vulnerable to SQL injection as special chars were not being escaped, hence it was possible to modify the query being executed.
> [https://pbs.twimg.com/media/FifPEgwWYAE_xrw.png](https://pbs.twimg.com/media/FifPEgwWYAE_xrw.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Data could be extracted through error based sqli, so I used sqlmap to dump all users and, as I suspected, among the +200 entries there were a couple of common friends, so I immediately told them to change their passwords.
> [https://pbs.twimg.com/media/FifPL8VX0AI0fQ3.png](https://pbs.twimg.com/media/FifPL8VX0AI0fQ3.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Since I was already here, I wanted to delete the data. Unfortunately stacked queries weren't allowed and I had to find another way to get in. I fuzzed for different paths and I found a different login page whose creds were also on the db.
> [https://pbs.twimg.com/media/FifPR5CXEAAtQyV.png](https://pbs.twimg.com/media/FifPR5CXEAAtQyV.png)
> 
> [https://pbs.twimg.com/media/FifPR6TXoAE5_o5.png](https://pbs.twimg.com/media/FifPR6TXoAE5_o5.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
I stumbled upon a file upload that allowed any file type. Because the site was running on PHP, I could upload and execute code on the server, so I tried with a simple shell, but system, exec, passthru... seemed to be disabled. However, there are more ways to exploit this.
> [https://pbs.twimg.com/media/FifQSdIXwAATjWs.png](https://pbs.twimg.com/media/FifQSdIXwAATjWs.png)
> 
> [https://pbs.twimg.com/media/FifQSfFWIAEfXzf.jpg](https://pbs.twimg.com/media/FifQSfFWIAEfXzf.jpg)
> 
> [https://pbs.twimg.com/media/FifQSgMXoAII_Rw.png](https://pbs.twimg.com/media/FifQSgMXoAII_Rw.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
I searched through directories and read files to see how the database connection was being made.
> [https://pbs.twimg.com/media/FifQqepXEAE2TQ2.png](https://pbs.twimg.com/media/FifQqepXEAE2TQ2.png)
> 
> [https://pbs.twimg.com/media/FifQqfqXEAQN1IE.png](https://pbs.twimg.com/media/FifQqfqXEAQN1IE.png)
> 
> [https://pbs.twimg.com/media/FifQqg9WIAARAVt.png](https://pbs.twimg.com/media/FifQqg9WIAARAVt.png)
> 
> [https://pbs.twimg.com/media/FifQqiDX0AIVI-G.png](https://pbs.twimg.com/media/FifQqiDX0AIVI-G.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Then, I just had to replicate the connection and execute the delete, goodbye attacker's data 👋
> [https://pbs.twimg.com/media/FifQ3_NWIAMcX4g.png](https://pbs.twimg.com/media/FifQ3_NWIAMcX4g.png)

> [!note] 📌
> **hipotermia **[***@hipotermia:***](https://www.twitter.com/hipotermia)
Finally, to prevent more people from falling for the phishing, I ended up rewriting the source code.
> [https://pbs.twimg.com/media/FifRAm1XoAg85Vf.png](https://pbs.twimg.com/media/FifRAm1XoAg85Vf.png)