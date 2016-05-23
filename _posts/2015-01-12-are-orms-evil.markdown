---
layout: post
title: "Are ORMs Evil?"
date: "2015-01-12 09:27:04 +0100"
comments: false
excerpt: "ORMs can really make our lives much easier, they can get and store our entities and can even seed our database, like magic... with a price."
---

[ORMs](http://en.wikipedia.org/wiki/Object-relational_mapping) like [Entity Framework](http://msdn.microsoft.com/en-us/data/ef.aspx) or [Nhibernate](http://nhibernate.info/) can really make our lives much easier, they can get and store our entities and can even seed our database, like magic...
But as [Rumpelstiltskin](http://en.wikipedia.org/wiki/Rumpelstiltskin) would say: "All magic comes with a price..."

In the last few days I´ve talked about this with some people and I´ve read some interesting discussions on the subject and decided to write something about it.
I have to say, I think that ORMs are pretty awesome, I used them and will keep using them, but they are not definitely suited for all kind of projects and they always should be used with care.

The abstraction level that they provide can be dangerous, as very easily, developers tend to forget what's under the hood. Queries will still be sent to the Db, and complex queries will still have a performance cost. Your database should be well structured and maintained, you still need to care about things like indexes, otherwise... Big headaches!

Of course it's possible to get good performance with ORMs but you really need to know what you are doing. It's too easy to make a mess. It's easy to add a new collection of entities to a parent entity totally forgetting the impact of that simple operation on the complexity of the queries generated to get the data.

I think that more lightweight ORMs, called Micro ORMs, like [Dapper](https://github.com/StackExchange/dapper-dot-net), [PetaPoco](http://www.toptensoftware.com/petapoco/) or [Ormlite](https://github.com/ServiceStack/ServiceStack.OrmLite), can be very useful and potentially less dangerous. With these, you basically get the ability of obtaining the result of some SQL query mapped to a C# class that you can use in your application. You have much more control over what's is sent to the DB, and over connection and entities lifecycles.
In my experience, since not all the aspects of data access are abstracted the developer has a better idea of what can be the cost of some change in data access layer, and what needs to be done in the Database.

So, maybe saying that ORMs are evil is a bit to strong... (It makes a good title though...), but you should be aware of what's happening behind the scenes otherwise you can be in trouble...
