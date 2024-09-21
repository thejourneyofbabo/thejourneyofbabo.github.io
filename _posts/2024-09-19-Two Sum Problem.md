---
layout: single
title: Two Sum Problem
categories:
  - Algorithms
tags:
  - Leetcode
  - Everyday_Coding
aliases: 
connected: 
toc: true
author_profile: true
---
## Two Sum Problem
**Problem 01. from Leetcode**\
Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.
You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.
You can return the answer in any order.

## My Solution
```rust
impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let len = nums.len();
        for i in 0..len-1 {
            let mut a = target - nums[i];
            for j in i+1..len {
                if a - nums[j] == 0 {
                    return vec![i.try_into().unwrap(), j.try_into().unwrap()];
                }
            }
        }
        return Vec::new();
    }
}

// Testcases
// Example1:
// Input: nums = [2,7,11,15], target = 9
// Output: [0,1]
// Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

// Example2:
// Input: nums = [3,2,4], target = 6
// Output: [1,2]
```


## Second Idea
```rust
use std::collections::HashMap;

impl Solution {
	pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
		let mut map = HashMap::new();
		for (i, &num) in nums.iter().enumerate() {
			if let Some(&j) = map.get(&(target - num)) {
				return vec![j as i32, i as i32];
			}
			map.insert(num, i);
		}
		vec![]
	}
}
```


## Reference
[LeetCode Problem](https://leetcode.com/problems/two-sum/)
