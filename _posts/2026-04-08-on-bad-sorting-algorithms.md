---
layout: post
title: "on bad sorting algorithms"
---
  
I was looking at sorting algorithms and some of them are just… bad.  
  
Not slightly inefficient. Just completely impractical.  
  
And for some reason, I find them interesting.  
  
## Bogosort  
  
Bogosort is probably the dumbest one.  
  
Take a list, check if it’s sorted.    
If it isn’t, shuffle it randomly and try again.  
  
Repeat until it works.  
  
```rust  
use rand::seq::SliceRandom;  
use rand::thread_rng;  
  
fn is_sorted(arr: &[i32]) -> bool {  
    arr.windows(2).all(|w| w[0] <= w[1])  
}  
  
fn bogosort(arr: &mut [i32]) {  
    let mut rng = thread_rng();  
  
    while !is_sorted(arr) {  
        arr.shuffle(&mut rng);  
    }  
}
```
It technically works. Eventually.

Time Complexity: O(n!) 

The time it takes grows insanely fast, so this is useless for anything real. But it’s easy to understand, which is probably why it sticks.

---

## Bogobogosort

This one is worse.

Instead of just checking if the list is sorted, it tries to sort part of the list first. And it does that using the same algorithm.

So it’s like:

- try to sort most of the list
- check if the whole thing is sorted
- if not, shuffle and try again

```rust
use rand::seq::SliceRandom;  
use rand::thread_rng;  
  
fn is_sorted(arr: &[i32]) -> bool {  
    arr.windows(2).all(|w| w[0] <= w[1])  
}  
  
fn bogobogosort(arr: &mut [i32]) {  
    let mut rng = thread_rng();  
  
    if arr.len() <= 1 {  
        return;  
    }  
  
    while !is_sorted(arr) {  
        let len = arr.len();  
        bogobogosort(&mut arr[..len - 1]);  
  
        if arr[len - 2] > arr[len - 1] {  
            arr.shuffle(&mut rng);  
        }  
    }  
}
```

I don’t even know why this exists. It just makes something already bad even worse.

Time Complexity: worse than O(n!), probably not worth checking.

---

## Stalinsort

Oh, this one is beautifully stupid.

You go through the list and remove anything that breaks the order.

That’s it.

```rust
fn stalinsort(arr: &[i32]) -> Vec<i32> {  
    let mut result = Vec::new();  
  
    for &x in arr {  
        if result.last().map_or(true, |&last| x >= last) {  
            result.push(x);  
        }  
    }  
  
    result  
}
```

It doesn’t really sort the list. It just throws away the parts that don’t fit.

You end up with something sorted, just not the original list.

Time Complexity: O(n), which finishes in one run. Perfect!

---

## Nuclear sort

This one isn’t really an algorithm.

If the list isn’t sorted, just give up.

```rust
fn nuclear_sort(arr: &[i32]) -> Vec<i32> {  
    if arr.windows(2).all(|w| w[0] <= w[1]) {  
        arr.to_vec()  
    } else {  
        panic!("array not sorted");  
    }  
}
```

Which is basically saying: if it’s broken, I’m not fixing it.

Time Complexity: O(n) to check, then gives up.

---

## Why I find these interesting

They’re completely useless, but they make things really obvious.

With normal algorithms, performance is something you read about.

With these, you feel it immediately.

They’re also simple enough that you can understand the whole thing without thinking too much.

And somehow that makes the better algorithms make more sense. After looking at these, stuff like quicksort doesn’t just feel faster, it feels necessary.

Also they’re just kind of stupid in a way that’s hard to forget.

---

## Takeaway

Not everything interesting is useful.

And sometimes the worst ways of doing something make the better ways easier to understand.

These were really fun to research about, but there are more of these as well. I'm too lazy to write about them though, and there's no way to fit them all in without making the post too long.

Thanks for reading :)