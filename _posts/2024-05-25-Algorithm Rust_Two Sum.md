---
layout: single
title: Algorithm Rust_Two Sum
categories:
  - Programming
tags:
  - rust
  - algorithm
aliases:
  - Two Sum
connected:
  - "[[Algorithms]]"
  - "[[Rust]]"
toc: true
author_profile: true
---
## Daily Algorithm Study Start.
*Since_ 25.05.2024(Sat)*<br/>
-Even I couldn't solve it, let's have a look and get used to the problems-

## Problem. Two Sum
- Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_. <br/>
- You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.<br/>
- You can return the answer in any order.
- **Example 1:** <br/>
  **Input:** nums = [2,7,11,15], target = 9<br/>
  **Output:** [0,1]<br/>
  **Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].
- **Example 2:**<br/>
  **Input:** nums = [3,2,4], target = 6<br/>
  **Output:** [1,2]
- **Example 3:**<br/>
  **Input:** nums = [3,3], target = 6<br/>
  **Output:** [0,1]

### First attempt
```rust
// My Solution
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut v: Vec<i32> = Vec::new();
        for i in 0..=nums.len()-1 {
            for j in i+1..=nums.len()-1 {
                if (nums[i] + nums[j]) == target { // check all the values in nums
                    v.push(i.try_into().unwrap()); // if it work, push into vector
                    v.push(j.try_into().unwrap());
                    break;
                } else{};
            }
        }
		return v; // return the result vector
    }
}
```

### Second attempt using Hashmap
```rust
use std::collections::HashMap;

impl Solution {
	pub fn two_sum(num: Vec<i32>, target: i32) -> Vec<i32> {
		let mut map = HashMap::new();

		for(i,&num) in nums.iter().enumerate() {
			let complement = target - num;
			if let Some(&index) = map.get(&complement) {
				return vec![index as i32, i as i32];
			}
			map.insert(num, i);
		}

		vec![]
	}
}

```






## Reference
[Leedcode_Two Sum](https://leetcode.com/problems/two-sum/description/)