---
layout: post
title: "C# 6.0 new features"
date: "2014-12-22 17:28:18 +0100"
comments: false
excerpt: "C# 6.0 new features - What I like and what I don´t like"
---

##  C# 6.0 new features - What I like and what I don´t like

There are lots of new features coming down our way as C# Devs with version 6 of the language.

See [here](http://roslyn.codeplex.com/wikipage?title=Language%20Feature%20Status "Feature Status") for feature status and discussion, and [here](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/116 "Features Summary") for a small summary.

There are already lots of good resources all over the internet explaining all the C# 6.0 new features, so I would like to share my opinion on four of them:

- ### Initializers for auto-properties


    public DateTime StartDate { get; set; } = DateTime.UtcNow;

    public DateTime EndtDate { get; set; } = DateTime.UtcNow.AddDays(15);


 Although this one feels a bit awkward I think that it will be very useful feature from the code simplicity stand point. Many times I find my self implementing a full property with the matching private field just so that I can initialize it. This way my code will become simpler and more readable, since I will be able to use and auto-property.


- ### nameof expressions


     public void GetNames(string name, int age)
     {
       Console.WriteLine(nameof(GetNames));
       Console.WriteLine(nameof(name));
       Console.WriteLine(nameof(age));
     }


 I try my best to follow defensive programming best practices, so at the beginning of my functions I normally test all the arguments to make sure that they are valid.

     public void DoSomething(string name, string address)
     {
         if (string.IsNullOrWhiteSpace(name))
             throw new ArgumentNullException("name");

         if (string.IsNullOrWhiteSpace(address))
             throw new ArgumentNullException("address");

         Console.WriteLine(nameof(DoSomething));
         Console.WriteLine(nameof(name));
         Console.WriteLine(nameof(address));
     }


 So when, for whatever reason, I need to change any of the parameters names, if I use this new feature I will get a compilation error witch will prevent me from raise an exception with a wrong argument name.


     public void DoSomething(string name, string address)
     {
         if (string.IsNullOrWhiteSpace(name))
             throw new ArgumentNullException(nameof(name));

         if (string.IsNullOrWhiteSpace(address))
             throw new ArgumentNullException(nameof(address));

         (...)
     }


- ### Null-conditional operators

Other good practice when we talk about defensive programming is to do a null check on objects before use them. This can generate lots of code if you need to check lots of nested properties, And is very common to see NullReferenceExceptions because of poor null checking.
This feature can make the null check code much more clean and simpler as the following code:

    int? first = (customers != null) ? customers[0].Orders.Count() : null;

can be replaced by:

    int? first = customers?[0].Orders.Count();


 And we can also check if Orders is null

    int? first = customers?[0].Orders?.Count();


- ### Exception Filters

Can´t say that I like this one. I think it brings very little value to the table, if any. Of course, that it may be useful for someone and nothing is forcing me to use it.
I think that the use of Exception Filters will lead to less readable code and more confusion among developers maintaining the same code.
With Exception Filters you can write a try catch block like this:

    try
    {

    }
    catch (CustomException ex) if(ex.SystemCode>10)
    {
           (...)
    }

 I understand that filters leave the stack unharmed, and that re-throw the exception may have mess with it. I admit that as time passes by I may even get used to it. But for now I prefer the following approach witch, to me, is much more clean and readable.

    try
    {

    }
    catch (CustomException1 ex)
    {
       HandleCustomException1(ex);
    }
    catch (CustomException2 ex)
    {
       HandleCustomException2(ex);
    }

 And then implement the handling logic inside the HandleCustomException methods.

 For more information about all the C# 6.0 new features I strongly recommend the resources mentioned in the beginning of this post and this [article](http://www.dotnetcurry.com/showarticle.aspx?ID=1042 "C# 6.0 What's New").
