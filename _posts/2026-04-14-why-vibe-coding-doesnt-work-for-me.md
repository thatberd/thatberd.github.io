---
layout: post
title: "why vibe coding doesn't work for me"
---
I’ve been trying vibecoding for a the last week, mostly out of curiosity, since it keeps popping up everywhere and I wanted to see what it actually feels like in practice.

---

## What it is (for those who happen to live under rocks)

Vibecoding is a trend started by renowned researcher Andrej Karpathy.
From what I understand, it's basically writing code in a very flow-based way. You don't spend much time planning structure upfront. You just start building, keep momentum, and figure things out as they come up.

It is more about staying in motion than designing everything carefully before you start.

---

## What I did with it

I tried it by building a simple chess game in Rust.

The idea was not to make something perfect or fully complete. It was just to get something playable working quickly.

So I started without a full architecture in mind. I added pieces as I needed them, handled rules when they became necessary, and adjusted things on the fly.

It actually went fine, and it was honestly kinda fun to watch the AI build it.

[repo](https://github.com/thatberd/vibe-coded-chess)

---

## Why it annoyed me

The problems showed up once the project got slightly bigger.

A lot of the code ended up being inconsistent. Some parts were structured, other parts were just quick fixes that I added because I wanted to keep moving.

Over time, it became harder to tell what was intentional design and what was just temporary patchwork that never got cleaned up.

That started to slow everything down instead of speeding it up.

I also started feeling a bit stuck in cleanup mode. Every time I wanted to add something new, I had to first fix earlier decisions that did not really scale well.

It was not just debugging. It felt like constant refactoring just to keep the project understandable.

And honestly, it also felt a bit mentally messy. I knew I was going to “fix it later,” but later kept becoming now.

---

## Takeaway

I can see why vibecoding works for quick experiments or throwing ideas together.

But for anything I actually want to keep building, it doesn't really fit how I like to work.

I prefer spending a bit more time early on thinking about structure, even if it slows me down at the start, because it usually saves me from a lot of confusion later.

The chess project was fun in the beginning, but it ended up reinforcing that I work better when the code stays understandable as it grows, not after I try to repair it later.

Thanks for reading :)