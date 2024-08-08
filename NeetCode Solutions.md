 1. Contains Duplicates.
	1. Optimal solution:
		1. HashSet.
		2. Iterate through array.
		3. If HashSet contains value, return true.
		4. Else you add the number to hashset.
		5. If all through iteration it does not contain, return false. 
		6. O(n) time and space (iterating through array, and then creating structure that is of size n)
2. Valid anagram:
	1. REMEMBER: ARRAYS.SORT IS VOID AND YOU CANNOT CHAIN WITH IT.
	2. To check if two arrays are equal: Arrays.equals()
	3. First approach:
		1. Sort array using toCharArray, if both arrays are equal (Arrays.equals()) then they are anagrams.
		2. O(n log n) approach
	4. Another approach:
		1. Two hashsets for both string character arrays.
		2. Do a frequency of each string character array.
		3. See if they are equal
		4. O (n) time complexity, but two additional objects made. 
		5. CHECK EDGECASE: ARE THE TWO STRINGS NOT THE SAME LENGTH? IF SO AUTOMATICALLY NOT A VALID ANAGRAM.
	5. Optimal approach.
		1. See point five above.
		2. Then, create a shared frequency array.
		3. Iterate over one string, and for s increment position of the character in the vocabulary, and for t decrement position of the character in the vocabulary (the frequency array).
		4. Iterate through the frequency array, and then if any of the numbers are not zero, that means one of the strings has that character and the other does not, so that means false (they are not palindromes).
3. Two integer sum:
	1. Optimzed solution:
		1. Create hashmap that stores number and index.
		2. Create solution array.
		3. For each element in the array, calculate difference.
		4. Then, if difference exists in the hashmap, return the index of the difference first, then the present i.
		5. else, just add the number present at i, and then its key is i.
		6. At end, return array.
		7. O(n) complexity (loop over array once, and then hashmap opps O(1)).
4. Group Anagrams:
	1. Optimized Solution:
		1. Creating a hashmap with String and list of strings.
		2. Generate a frequency map for each string, then make into a string.
		3. If does not exist in hashmap, make a new arraylist for that, then add the current string to the arraylist. 
		4. from there, make an arraylist of anagrams, then add the list of words for each key. 
		5. O(n + m) (n is the number of strings, m is the number of unique frequency maps for each string)
5. Top K Frequent Elements
	1. Optimized Solution:
		1. First, generate a frequency hashmap of the elements.
		2. Then, utilize bucket sort technique where the frequency of each element is the index.
			1. THIS MEANS ARRAY MUST BE ONE MORE THAN THE SIZE OF ELEMENTS.
			2. ALSO MEANS THAT ARRAY MUST BE INITIALIZED WITH HASHMAPS AT FIRST.
		3. Then, go through each Map.Entry from freq.entrySet, and do above where value is the index, and the element is what gets added. 
		4. Then, go through the bucket sort array backwards, and iterate through each element of the list. Use a helper variable that will automatically return results when its greater than k - 1 (as that is the max index that can be added).
6. Encode and Decode Strings
	1. Encoding: we encode the length of the string, then a # delimiter, then the actual string.
		1. USE STRING BUILDER BECAUSE OG STRING IS IMMUTABLE. 
	2. Then for decoding, two variables.
		1. i = 0.
		2. While i < str.length(), j = i, and while the character at the j position is not '#', we increment j++. 
		3. When j hits a #,  i is before. So, substring (i, j) gives you the length (i inclusive, j exclusive)
			1. USE INTEGER.VALUEOF.
		4. i is then equal to j + 1 + length, so essentially going to the next length. 
		5. Then, add to the list of strings, the substring from j+1 (j is the location of the hash), to i (the location of the next length)
7. Product Except Self
	1. Optimal solution: prefix and postfix multiplicatin.
		1. Prefix multiplication: entry will consist of the multiplication of all the numbers to the left of it. 
			1. Literally a simple loop, results[i] is equal to the left, and then multiply the left by the number at that position.
		2. Post fix multiplication: same concept here, except in reverse. entry will be the multiplication of all numbers to the right. 
			1. Literally a simple loop, results[i] equal to results[i] * right (since there is a value here)
		3. O(2n)
8. Valid Sudoku:
	1. ALWAYS CHECK FOR IF IT ISN'T A PERIOD.
	2. Three hashmaps that map a row, column, or box to a hashset of integers
		1. Why hashset? Sudoku invalidated if there are nonunique numbers. 
	3. Iterate over two-d array (rows, columns).
		1. For each element, if the row/column/box is not in the hashmap, put it alongsize new hashmap.
		2. If any of the hashmaps contain the element, return false.
		3. Else, add them to their appropriate hashmaps with correct key.
		4. Formula for box: (i/3*3 + c/3).
		5. AGAIN, CHECK FOR IF ITS NOT A PERIOD.
	4. Solution (O(81)) --> O(n) here.
	5. But if the number of rows increase, you are increasing at a square rate. So O(n^2).
9. Longest Consecutive Sequence:
	1. We need to get a unique list of elements bceause the sequence only considers that. 
	2. Once added to a list, we check for each element if an element that is one less than it exists. 
	3. If it doesn't, then while the set contains the number that is one ahead of it, increment the length and increment the number.
	4. Then, figure out whether the current sequence is larger than the previous sequence (Math.max).
	5. EDGE CASE: IF THE ARRAY IS ZERO, YOU CAN DIRECTLY RETURN IT. WORRY ABOUT EDGE CASES AT THE END. 
	6. LENGTH SHOULD ALWAYS START AT 1. NOT ZERO. THE FIRST CHARACTER IS CONSIDERED PART OF THE SEQUENCE. 
10. Valid Parenthesis:
	1. Solution I like:
		1. Iterate through string.
		2. Add opening to a stack.
		3. Use a HashMap to check for opening, where keys are closing corresponding to their opening. 
		4. When you encounter a closing, see if the stack is empty. If it is empty, that means there is no matching opening for that closing, so return false.
		5. Keep doing this, after you reach end return whether the stack is empty or not. 
		6. Obviously O(n)
	2. Optimal:
		1. Create a stack.
		2. Create hashmap that maps closings to openings.
		3. For each character in the string, if hashmap key contains it (meaning its a closing):
			1. if the stack is non empty and the first element in the stack (sought through peeking) is equal to its key, then pop that from the stack.
			2. Else, we return false.
		4. If its not a closing, we add the character to the stack.
		5. STACK THUS CONTAINS ALL THE BEGINNING PARENTHESIS.
		6. Obviously O(n) as well. 
11. Min Stack:
	1. Trick: have two stacks, one that tracks the minimum at each insertion, and the another that is the normal stack.
	2. MAKE SURE TO REMEMBER HOW TO DO JAVA.
	3. push: 
		1. Normal Stack: just add normal stack.
		2. Min stack: if the stack is empty, or the value is less than peek of the min stack, add the value. Else, just add the last minimum again.
	4. pop:
		1. Normal pop: just pop from both.
			1. REMMBER TO POP FROM BOTH. 
	5. top:
		1. peek from the normal stack.
	6. get min:
		1. peek from the minimum stack.
	7. Everything: O(n)
12. Evaluate Reverse Polish Notation:
	1. First, initialize number stack.
	2. Iterate through.
		1. If number, then add.
		2. Else, if addition, pop the first two numbers (KEEP IN MIND THAT THE FIRST NUMBER IN THE OPERATION IS THE SECOND ONE POPPED), add. READD THIS NUMBER TO YOUR STACK. 
		3. This process repeats for all of the operations (*, /, -).
		4. Return stack.pop() --> because if valid, the last element will be subject to all the other operations.
13. Valid Parenthesis:
	1. Optimal solution: backtracking.
		1. What this means; brute force under specific conditions.
		2. Two things you know:
			1. n = 3 -> there will be n open and n close brackets.
				1. OPENING BRACKETS DICTATE THE FLOW.
			2. a close bracket can only be added when close bracket count is less than open bracket count  
		3. Use recursion in order to tackle the problem.
			1. Base case: when both the number of opening parenthesis and closing parenthesis is equal to n, take the string we have and add it to list.
			2. Other wise, if the # of opening parenthesis we have is less than n, we add an opening.
			3. If the # of closing parenthesis is less than the opening, we add a closing.
			4. FOR EACH INSTANCE, TO DO SUCCESSFUL BACKTRACKING, WE DELETE THE LAST DECISION TO EXPLORE OTHER DECISIONSS.
		4. Steps:
			1. Two classes: solution class and a backtracking class
			2. Solution class: we instantiate the list of valid sequences and a stack that will contain the characters for the present. We call the base backtracking function (takes in n, the opening number of parenthesis, the closing number of parenthesis, the list of valid sequences, and the stack that will contain the characters).
			3. Basecase: when do we stop and add a generated parenthesis sequence to the list? when we have n openings, and the closing match the number of openings.
			4. Here, use string builder because mutable, and go through the stack and add all elements to the string builder, return as string and add to the list.
				1. DON'T POP BEACUSE THEN BACKTRACKING WON'T WORK BECAUSE THERE WONO'T BE A PREVIOUS STATE TO GO TO. 
			5. ELSE: if the number of starting parenthesis is less than n, we will add a starting parenthesis. 
				1. backtrack again w/ + 1 opening.
				2. pop() --> revert to previous state.
			6. if closing less than opening, add a closing, backtrack with +1 closing, pop --> revert to previous state. 
			7. Time complexity: 
				1. More confusing: just think how many nodes there can be. 2^(2n) --> O(4^n).
				2. 2^(2n-1) leaves at most --> O(4^n).
14. Daily Temperatures:
	1. Brute force approach:
		1. Nested loops, for a given i day, go through every other day and see whats greater, subtract i - j, that is how many days it takes, but its O(n^2).
	2. Answer: 
		1. Monotonic stack.
		2. Meaning, only values that are less than the previous one will be present in the stack.
		3. Create a output array that stores the results.
		4. Create a Stack of integer arrays (THIS IS VERY IMPORTANT YOU CANNOT DO THIS WITH A HASHMAP BECAUSE VALUES WILL BE OVERWRITTEN).
		5. Iterate through the array.
			1. While the stack is non empty and the peeked value is less than the current value, you pop the value off of the stack, and you set the second value of the popped array as the index where you assign the difference between i and the popped value's index.
			2. Otherwise, you just add a new array to the stack that contains value and index.
		6. O(n)
15. Car Fleet (HARD)
	1. Question confused me when I first read it, but intuitiion after makes so much sense.
		1. Idea: if a car behind another car (in terms of position) takes **LESS TIME** to reach the target, the two will form a car fleet.
	2. Therefore:
		1. Optimal solution:
			1. Group the two arrays together by making a 2d array that contains position and speed.
			2. Sort this array in descending order (items with positions that are closer to target will be in the front, iterator lambda function (b - a).
			3. Then, iterate through this array. If the i is greater than equal to one, and the time calculated present at i is less than the time at i -1, time[i] = time[i-1].
			4. Else, we add to the number of fleets.
				1. This is because this means that the cars will not catch up, and thus a unique fleet will be formed.
			5. Complexity: O(n)
16. Largest Rectangle in Histogram:
	1. Intuition: when you see a bar that is smaller than the one you are currently in, calculate area using limits of the bar, and keep repeating. The limits extend by one. 
	2. Algorithm:
		1. Iterate through the array sequentially.
		2. While the stack is not empty, and the element currently at is smaller than the element in the stack.
			1. Pop the element, and calculate the max area by doing height (of the popped)* (i - popped (index))*
			2. Then, the starting index is going to be index of the last popped.
				1. Make the smallest one's index be at the last element that is bigger than it. 
		3. Outside the while loop, insert to the array the element's index and the actual element. 
		4. After we rule out all possibilities where a larger bar hits a smaller one, we get stuck with all the smaller ones that can extend into left and/or right.
		5. Compare the areas of these smaller ones, with their areas being their length - index. 
		6. SO.... 
			1. **Monotonic increasing stack.**
				1. Why? Because the first case of rectangles can be formed going forwards, while taking into account the possibility of rectangles occuring backwards on a second pass. 
				2. Stack contains bars.
				3. Pop a bar and calculate its potential area. 
				4. When you reach the last bar, its index is going to be the start. 
		7. Complexity: O(n)