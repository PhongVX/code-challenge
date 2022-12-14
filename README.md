# code-challenge
## Challenge 1
A.Tũn đến vào 1 tòa tháp để thăm chú, nhưng cậu không tìm được chú mình ở tầng nào, bản đồ chú đưa cho Tủn cực kỳ khó hiểu. Cậu bắt đầu ở tầng trệt (floor 0). Sau đó dựa theo hướng dẫn của bản đồ từng bước một.
Dấu mở ngoặc (, nghĩa là cậu phải đi xuống một lầu, và gặp dấu đóng ngoặc ) cậu phải đi lên một lầu. Tòa tháp rất là cao, và tầng hầm cũng rất là sâu, cậu sẽ không bao giờ đến được tầng cao nhất hoặc tần thấp nhất của nó dù có lên hay xuống liên tục.

### Examples:

(()) và ()() có kết quả là tầng 0

((( và (()(()( có kết quả là tầng -3.

))) và )())()) đều dẫn tới tầng 3
### Answer:
``` 


function floor(guide) {
  var stand = 0;
	for (var i = 0; i < guide.length; i++) {
   		if(guide[i] == "("){
        	stand -=1;
        }else{
        	stand +=1;
        }
	}
  return stand;
}

```
## Challenge 2
Alice wrote a sequence of words in CamelCase as a string s, having the following properties:
It is a concatenation of one or more words consisting of English letters, numbers and special characters.
All letters in the first word are lowercase.
For each of the subsequent words, the first letter is uppercase and rest of the characters are lowercase.
Given s, return the number of words in s.
Expected
A function or method named CamelCase, camel_case or camelCase(depends on your choice of programming language) that takes one s string in camelCase.
The function returns an integer indicates the number of words in s string.

### Examples:
CamelCase("") => Returns 0.

CamelCase("saveTheWorld") => Returns 3.

CamelCase("hitTheRoadJack") => Returns 4.

CamelCase("can'tHelpFallingInLoveWithYou") => Returns 7.
### Answer:
```
function CamelCase(s) {
  // your code here
  if(s.trim() == ""){
    return 0;
  }
  var numUpper = (s.match(/[A-Z]/g) || []).length + 1;
  return numUpper;
  
}
```
## Challenge 3

A debugger program here is having an issue: it is trying to repair a memory reallocation routine, but it keeps getting stuck in an infinite loop.

In this area, there are sixteen memory banks; each memory bank can hold any number of blocks. The goal of the reallocation routine is to balance the blocks between the memory banks.

The reallocation routine operates in cycles. In each cycle, it finds the memory bank with the most blocks (ties won by the lowest-numbered memory bank) and redistributes those blocks among the banks. To do this, it removes all of the blocks from the selected bank, then moves to the next (by index) memory bank and inserts one of the blocks. It continues doing this until it runs out of blocks; if it reaches the last memory bank, it wraps around to the first one.

The debugger would like to know how many redistributions can be done before a blocks-in-banks configuration is produced that has been seen before.
For example, imagine a scenario with only four memory banks:

The banks start with 0, 2, 7, and 0 blocks. The third bank has the most blocks, so it is chosen for redistribution.
Starting with the next bank (the fourth bank) and then continuing to the first bank, the second bank, and so on, the 7 blocks are spread out over the memory banks. The fourth, first, and second banks get two blocks each, and the third bank gets one back. The final result looks like this: 2 4 1 2.

Next, the second bank is chosen because it contains the most blocks (four). Because there are four memory banks, each gets one block. The result is: 3 1 2 3.

Now, there is a tie between the first and fourth memory banks, both of which have three blocks. The first bank wins the tie, and its three blocks are distributed evenly over the other three banks, leaving it with none: 0 2 3 4.

The fourth bank is chosen, and its four blocks are distributed such that each of the four banks receives one: 1 3 4 1.

The third bank is chosen, and the same thing happens: 2 4 1 2.

At this point, we've reached a state we've seen before: 2 4 1 2 was already seen. The infinite loop is detected after the fifth block redistribution cycle, and so the answer in this example is 5.

Given the initial block counts in your puzzle input, how many redistribution cycles must be completed before a configuration is produced that has been seen before?

### Expected
A function or method named MemoryAllocation, memory_allocation or memoryAllocation (depends on your choice of programming language) that takes one input array of integers represents the memory banks and its blocks (size of input array <= 16).

The function returns an integer indicates the redistribution cycles required to reach a state has been seen before.

### Examples
MemoryAllocation([0, 2, 7, 0]) => Returns 5.

MemoryAllocation([1, 2, 3, 4, 5, 6]) => Returns 6.

MemoryAllocation([12, 3, 27, 2, 0, 0]) => Returns 15.







