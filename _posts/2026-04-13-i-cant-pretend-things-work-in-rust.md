---
layout: post
title: "i can't pretend things work in rust"
---
<!-- day 7 -->

I’ve been noticing this more the longer I use Rust.

It’s hard to leave things in a half-working state and just move on.

---
## The Difference

In a lot of other languages, I used to write code that was “good enough for now.”

It would run, give roughly the right output, and I’d tell myself I’d clean it up later.
And honestly, that worked more often than it should have.
I could keep building on top of something that wasn’t fully thought through.

With Rust, that habit doesn’t really work.
The compiler keeps asking questions I’d normally ignore.

If something can fail, I have to deal with it.  
If I’m not clear about how data is used, I have to fix that.  
If types don’t line up, I have to make them line up properly.

It slows things down, especially at the start.

---
## Where it Shows

Error handling is where this shows up the most.
When something returns a `Result`, I can’t just move past it.
I have to decide what failure actually means here.

Do I propagate it?  
Do I handle it right away?  
Do I transform it into something else?

At first it feels like extra work, but after a while it starts to feel like part of shaping the program.

Ownership took longer to get used to.

Early on, it felt like I was fighting the language over small things, and it was very annoying.

Why can’t I use this value here?  
Why do I need to clone this?  
Why doesn’t just work?

But those questions usually pointed to something real.

I was moving data around without thinking much about who should actually own it.

Rust doesn’t let that stay vague for long.

Something else I’ve started to appreciate is how changes propagate.
If I tweak a type or change how something is returned, the compiler tells me everywhere that depends on it. Sometimes it’s a lot, but it’s very direct.

I don’t have to rely on memory or hope I didn’t miss something, I can just follow the errors and warnings and fix things one step at a time.

---
## Debugging

Debugging feels different too.

There are still bugs, and I still write stupid code.

But I spend less time dealing with weird states caused by things being loosely defined.
More of the problems I hit are about logic, not about the program behaving unpredictably.

There are definitely moments where this feels like friction.
Sometimes I just want to try an idea quickly and see what happens.
Rust makes that harder than I’d like.
I can’t always sketch something out and clean it up later.

---

But when I come back to the code after some time, it usually makes more sense than I expect.

The structure is clearer, the assumptions are visible, and 
I don’t have to keep as much context in my head.

---
## Takeaway

I think that’s the main shift for me.
In other languages, I could get away with not fully thinking things through.

In Rust, that shows up pretty quickly.
It pushes me to be more deliberate about what I write.

I’m still getting used to it, though.
I still get stuck, and I still get annoyed sometimes.
But I also trust the code more once it works.
And lately, that’s started to matter more than just getting something running as fast as possible.

Thanks for reading :)