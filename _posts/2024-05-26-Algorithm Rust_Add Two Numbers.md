---
layout: single
title: Algorithm Rust_Add Two Numbers
categories:
  - Programming
tags:
  - rust
  - algorithm
aliases: 
connected:
  - "[[Algorithms]]"
  - "[[Rust]]"
toc: true
author_profile: true
---
## Add Two Numbers
You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)

**Input:** l1 = [2,4,3], l2 = [5,6,4]<br/>
**Output:** [7,0,8]<br/>
**Explanation:** 342 + 465 = 807.

**Example 2:**<br/>
**Input:** l1 = [0], l2 = [0]<br/>
**Output:** [0]

**Example 3:**<br/>
**Input:** l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9] <br/>
**Output:** [8,9,9,9,0,0,0,1]

### Clone Coding
```rust
impl Solution {
	pub fn add_two_numbers(l1: Option<Box<ListNode>>, l2: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
		let mut p = l1;
		let mut q = l2;
		let mut carry = 0;
		let mut dummy_head = Some(Box::new(ListNode::new(0)));
		let mut current = &mut dummy_head;

		while p.is_some() || q.is_some() {
			let sum = carry +
				p.as_ref().map_or(0, |node| node.val) +
				q.as_ref().map_or(0, |node| node.val);
			
			carry = sum / 10;
			
			if let Some(ref mut curr) = current {
				curr.next = Some(Box::new(ListNode::new(sum % 10)));
				current = &mut curr.next;
			}
			
			p = p.and_then(|node| node.next);
			q = q.and_then(|node| node.next);
		}
		
		if carry > 0 {
			if let Some(ref mut curr) = current {
				curr.next = Some(Box::new(ListNode::new(carry)));
			}
		}
		
		dummy_head.unwrap().next
	}
}
```




## Reference

