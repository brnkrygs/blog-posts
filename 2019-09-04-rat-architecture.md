# Architecture to support The RAT
### 2018-09-04

Response to 10,000 Feet episode #13: The Riskiest Assumption Test.

https://www.ostusa.com/blog/whats-your-rat/

Goal: iterate in riskiest spot of a project.

Support: architecture is intended to manage volitility (usually by isolating it). The iteration of a RAT inside a project is the most volitile part!

There's certainly a lot to consider when designing the architecture of a software project. [Examples here].

One of the major goals or outcomes of a successful architecture is adaptability - does the way your components are organized and communicate together support ongoing change?

Well, how do you predict what is going to change. There are a couple of tools you can use to expose ares of an architecture that have increased risk of volitility. One of them is the outcome of your RAT.

The RAT (riskiest assumption test) is a tool used to validate ... your riskiest assuption. This often can be the assumption that your users actually want what you're making. Or, that the problem you're solving is a real problem. It can also be used to validate if there is a business case for the thing you want to build - can you as an organization even support this thing once it is in the wild and people are depending on it?

Often, doing a RAT can expose misaligned goals, unclear expectations, etc. which isn't necssary the death knell for a project, but instead is an opportunity to explore. Critically, it helps to uncover the specific areas that need focused iteration that can turn a project around from unviable to a uniocrn.



Title: RAT-ing out your Architecture

Intro: Consider how RAT can inform architectural patterns.

 1. Some characteristics of good architecture
 2. What is RAT
 3. How can RAT inform architecture
 4. Stay in the room / engaged


I was recently listening to the OST pocast (10,000 feet) - an episode where Jim VanderMey and Andrew Powell [discuss the Riskiest Assumption Test](https://www.ostusa.com/podcast_post/13/). It struck me that the effort invested in RATs and their related iterations can be valuable not just to product owners as they solidify the vision for their product, but also to the architect responsible for bringing that product vision to life.

One of my favourite parts of being an architect for [OST](https://www.ostusa.com/expertise/connected-products/) is when I get a chance to tackle a fresh problem from a technical perspective. There's a lot of aspects that go into a solid architecture - but the technical implementation details strike just the right note for me. As an example, since I focus a lot of the IoT and Connected Products space, I'm commonly challenged with data ingest and messaging problems at scale. How do you securely ingest gigs of data from field sensors over sometimes-reliable uplinks, reacting to some of those messages in near-real-time while funnelling the rest of them off into archives, backups, and analytics processes? Fascinating stuff. 

Once the initial problem is well-defined, explored, and cracked we need to think about the second (supporting) system. That is, the wider environment in which the direct solution lives, and the people and processes that will support it. This quickly raises questions about "ility"s if they haven't already been addressed: scalability, adaptability, maintainability, observability, cost-efficiencility(!), securitility(!), etc. In some cases asking those questions can cause a revisit to the original solution until one arrives at an architectural vision and approach that solves for the necessary outcomes.

Adaptability is one of the harder system characteristics to measure, much less get right. How do I know if this system can handle future change gracefully? How do I know if future implementation teams will have a straightforward answer on "where should I make this change?" Answering these questions well is almost impossible unless you have a good idea about what that future change might look like. Instinct, patterns, and experience go a long way to helping with this, but if we had a way to understand _likely_ change (or volitility), we can design a system in such a way that it encapsultes that volitility, reducing the blast radius of change to a specific, well-defined, and well-known subset of the system.

https://medium.com/@hurlbert/architect-the-business-not-the-requirements-71c6a643ec2f

The RAT

The RAT (riskiest assumption test) is a tool used to ... test ... your riskiest assuption. More can be found in the discussion from [Jim and Andy](https://www.ostusa.com/blog/whats-your-rat/), or [Jim and Andrew](https://www.ostusa.com/podcast_post/13/). In short though - its an approach to product validation that focuses energy on testing to see if your assumptions as prouct owners and implementors will hold. It answers questions like: Is this product solving a problem people actually have? If so, is it solving that problem in a better way than folks are solving it now? If both of those hold, is my business structured in a way that I can sustainably run this solution?

Design teams take these questions and bring them to the field, testing lightweight prototypes with real customers and stakeholders, evolving the definition of the product to fit their findings. Turns out, customers don't actually need x, but they would love help solving y!

The fast iteration and evolution of a product during this phase can give an observant architect a much more concrete idea about what areas of a product are ripe for volatility. For example, after showing a dashboard prototype to several customers, a design team may realize that the value they're assuming customers will place on particular set of metrics for their device fleet isn't going to hold, and they actually will need to track something else, or surface those metrics in an entirely different way.

That's a huge hint to the architect that the individual measurements being collected by a given field sensor will likely continue to be tuned to fit other use cases or evolving customer needs over the lifetime of the solution. The solution should therefore be architected to support adaptability in this area, and ecapsulate the expected volitility as much as possible. 

Granted, there's lots of good reasons for an architect to be involved in early product discussions. From clearly understanding business objectives, to getting a better sense of non-functional requirements, and many others. Paying attention during RATs in particular gives an architect insight into how product teams and business owners have defined their product, but more helpfully how they might *change* the definition of their product to serve their customers.
