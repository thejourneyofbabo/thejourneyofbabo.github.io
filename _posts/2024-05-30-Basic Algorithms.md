---
layout: single
title: Basic Algorithms
categories:
  - Programming
tags:
  - rust
  - algorithm
aliases:
  - Basic Sorting Algorithms
connected: 
toc: true
author_profile: true
---
>**Lecture Notes:** Basic Sorting Algorithms
>**Objective:** Understand and implement basic sorting algorithms (Bubble Sort, Insertion Sort in Rust)

## 1. Introduction to Sorting Algorithms
**Definition:** Sorting algorithms are methods for arranging elements in a list or array in a particular order (ascending or descending).

**Importance:**
- Fundamental in computer science for organizing data.
- Improve the efficiency of other algorithms (like search algorithms).
- Often used as building blocks in more complex algorithms.

## 2. Bubble Sort
**Definition:** Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compare adjacent elements, and swaps them if they are in the wrong order. the process repeats until the list is sorted

**Time Complexity:** O(n^2)

**Implementation in Rust:**
```rust
// Bubble Sort Implementation
fn bubble_sort(arr: &mut [i32]) {
	let len = arr.len();
	for i in 0..len {
		for j in 0..len - 1 - i {
			if arr[j] > arr[j + 1] {
				arr.swap(j, j+1);
			}
		}
	}
}

fn main() {
	let mut arr = [5, 3, 8, 4, 2];
	bubble_sort(&mut arr);
	println!("Sorted array: {:?}", arr);
}
```

## 3. Insertion Sort
**Definition:** Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is much less efficient on large  lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

**Time Complexity:** O(n^2)

**Implementation in Rust:**
```rust
fn insertion_sort(arr: &mut [i32]) {
	let len = arr.len();
	for i in 1..len {
		let key = arr[i];
		let mut j = i;
		while j > 0 && arr[j - 1] > key {
			arr[j] = arr[j - 1];
			j -= 1;
		}
		arr[j] = key;
	}
}

fn main() {
	let mut arr = [5, 3, 8, 4, 2];
	insertion_sort(&mut arr);
	println!("Sorted array: {:?}", arr);

}
```






## Reference

