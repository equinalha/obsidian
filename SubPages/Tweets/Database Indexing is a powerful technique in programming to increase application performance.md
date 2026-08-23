---
base: "[[Tweets.base]]"
Type: Thread
Created: 2022-12-12T11:36:00
Author: Chris Staudinger
Tags:
  - Db
Tweet Link: https://twitter.com/ChrisStaud/status/1602188427134488577
---
> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Database Indexing is a powerful technique in programming to increase application performance.

Here's a dead simple guide to understanding it:

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Database indexing is a technique that improves the speed of data retrieval operations on a database table.

Indexes are used to quickly locate data WITHOUT having to search every row in a table every time the table is accessed.

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Usually, the data structure for a DB index will be a binary search tree. 

This allows the time complexity of accessing data to be lowered from linear time O(n) to logarithmic time Olog(n).

This can save significant amounts of time off queries that use an indexed column.

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Example:

If you had 10,000 users & your app has a page that looks up a user by their username.

An un-indexed query would check every row in the users table until it finds the user matching the username passed into the query. 

That could take up to 10,000 row examinations O(n).

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Example continued:

By creating an index for the “username” column, the database could pull out that row under logarithmic time complexity Olog(n). 

In this case, the maximum number of row examinations would be only 14 instead of 10,000!

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
Takeaways:

• Indexing significantly boosts query performance leading to better user experience.

• It also helps with scaling by reducing load on the database via increasing efficiency.

• Indexing should be one of first scaling/performance patterns implemented on a database.

> [!note] 📌
> **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
If you enjoyed this thread,  like, comment, and retweet the first tweet so others can read it.

I simplify programming and getting into tech.

Follow [**@ChrisStaud**](https://www.twitter.com/ChrisStaud) for more threads like this.
> > [!note] 📌
> > **Chris Staudinger **[***@ChrisStaud:***](https://www.twitter.com/ChrisStaud)
> Database Indexing is a powerful technique in programming to increase application performance.
> 
> Here's a dead simple guide to understanding it: