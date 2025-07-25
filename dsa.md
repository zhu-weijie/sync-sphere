Data Structure and Algorithm Patterns for LeetCode Interviews – Tutorial - YouTube
https://www.youtube.com/watch?v=Z_c4byLrNBU

Transcript:
(00:00) Welcome to this comprehensive course on data structures and algorithms. Whether you're preparing for coding interviews or looking to strengthen your foundational programming skills, this is a great course for you. Sheldon Chai developed this course. Sheldon will break down the most essential data structures like arrays, strings, sets, hashmaps, and heaps, and will show you exactly how and when to use them.

(00:31) You'll also master core algorithmic patterns such as two pointers, sliding windows, binary search, breadth first search, depth first search, and backtracking. All explained with clear examples and real interview problems. This course will help you build your intuition for efficiency and help you recognize which patterns to apply and how to avoid brute force solutions.

(00:54) And each concept is taught step by step with practical code walkthroughs and tips for common pitfalls. Let's start with the absolute foundation. Arrays. Arrays are the default data structure for basically everything. Whether it's list of numbers, characters, coordinates, or even objects. If it's linear and ordered, it's probably going to be stored as an array.

(01:21) Now, here's the important part. Arrays give you constant time access by index. So if I say a r at index 4, we can go straight there. That's o of one time. And the reason this is possible is because arrays are stored in contiguous memory. It's like having a row of houses all next to each other. You know exactly how far to walk to get to house number five.

(01:47) That's what makes arrays fast for reading and indexing. Where arrays start to break down is when you want to insert elements or delete elements in the middle. So let's say we have 1 2 3 4 5 and we want to insert a zero at the beginning. What happens? Well, you have to shift everything one position to the right to make room for it. That is an O of N operation.

(02:15) And the same goes for deleting something in the middle. We have to shift everything left to fill the gap. So, the trade-off is pretty simple with arrays. If you're accessing by index, super fast. Appending at the end, also usually fast. However, if it's inserting or deleting from the middle or front, that is when it gets expensive.

(02:37) So, how do you use arrays in interviews? Honestly, you will use them constantly. In particular, in problems where you need to traverse a structure in order, access specific indices, compare elements from both ends, or even for doing tricks like sliding windows or prefix sums. A lot of people think of arrays as basics they don't need to spend much time on.

(03:04) But almost every single clever interview problem comes down to how well you can leverage the array structure to avoid unnecessary work or build into other data structures. Strings are just arrays of characters, but with a few catches. First, in most languages, strings are immutable. That means if you change a string, even slightly, you're not really modifying the original.

(03:29) You're creating an entirely new one under the hood. This has big implications for code efficiency. Let's say you're solving a problem where you're building a result string for multiple steps. A common beginner mistake is doing something like this. It looks clean, but under the hood, that's creating a new string on every iteration.

```python
result = ""
for char in chars:
    result += char
```

(03:55) Concatenating strings in a loop like this can lead to an O of N squared time complexity. Instead, you should be building a list of characters and joining them at the end. What you want is something like this. That gets you back to ON. Aside from this, strings work largely very similarly to arrays, and you can almost think of them in the same way. Strings also show up a ton, especially in interview problems.

```python
result = []
for char in chars:
    result.append(char)
result = "".join(result)
```

```python
def valid_parentheses(s: str) -> bool:
    stack = []
    for char in s:
        if char in "([{":
            stack.append(char)
        elif char in ")]}":
            if not stack or stack[-1] != char:
                return False
            stack.pop()
    return not stack
```

(04:24) You'll see tons of questions like, find the longest substring without repeating characters. Check if two strings are anagrams, or return all the substrings that match a pattern. Here's the thing. Most of these are actually hidden as sliding window problems, a pattern we're going to get to later in the video or another pattern called two-pointer.

(04:48) We'll actually cover both of these patterns in detail, but the key insight for now is string problems are almost never about brute force character checking. They're about smart windowing, fast lookups, and efficient traversal. Sets are one of the simplest data structures and one of the most useful for time efficiency. A set is just a collection of unique values. No duplicates, no particular order, just a group of things where each one only appears once.

(05:13) Let's say you're given a list of numbers and you want to quickly check whether a certain number is in it. If you store that list as a set instead, you can check for existence in constant time on average. In Python, for example, you can write this. This check once you convert it to a set actually runs in O of one time which is much faster than looping through the entire list.

```python
nums = [1, 2, 3, 4, 5]
seen = set(nums)
print(3 in seen)
```

(05:43) So when do you want to use sets? You should always use a set instead of a list when you care about uniqueness like checking for duplicates. Existence where you're saying have I seen this before? Fast membership checks saying is this value in the current group? For example, in a problem where you're scanning an array to find the first repeated element, using a set is usually the cleanest and fastest solution.

(06:06) Sets also come up in problems where you're maintaining a sliding window. And you want to make sure that all elements in the window are unique. In that case, the set becomes a quick way to track what's currently in play and what needs to be removed. But we'll get to that a bit later.

(06:24) So, just to sum it up, sets are not for storing key value pairs, which is a mistake people often make. They're for tracking whether something exists. They do it quickly and cleanly, and you'll use them in place of lists a lot more than you think. This might sound obvious, but it's worth saying.

(06:43) You need to be extremely comfortable with basic loops and control flow. Almost all interview problems boil down to three things. A loop, some condition, and a few variables being updated. And that's it. Here are the basics you should know like the back of your hand. Now, these might sound basic, but it's where a ton of people stumble. They forget to update the loop pointer correctly, or they don't think through what the loop they're making should be doing.

```python
for i in range(n):

for val in arr:

while start < end:

if, elif, else

break

continue
```

(07:12) One of the best habits you can build early is walking through your code with an actual example input. Mentally run it. Where do the pointers move? What changes on each iteration? This one habit will save you dozens of bugs, especially once you start working with more complicated data structures and algorithms. You absolutely need to know these basics. It's time to talk about efficiency.

(07:35) Big o notation is how we measure how a program's performance scales with input size. Now, I'll be honest, you don't need to memorize 20 different bigo classes. And that's a misconception that puts people off of learning this concept. You really just need to learn the few basic ones and from then it will just be intuition to you.

(07:56) You should be able to look at a nested loop and think, "Oh, that's O of N squ that's probably too slow." Or see a binary search and know instantly O of login that's fast. So let's go through the most common ones you'll see. The fastest one is O of one constant time. In this case, it doesn't matter how big the input is. The time complexity never changes.

(08:23) Some good examples are accessing a specific index in an array or checking if X exists in a set. The next fastest is O of log N, which is logarithmic time. This is where you divide the problem in half each time. Think of binary search, which we'll get to in a bit. Next is O of N, linear time. In this case, you're going through each item once.

(08:51) This is probably the most common time complexity and is often associated with loops and traversing through lists. Next, we have O of N login. This is almost always related to sorting and that includes the default sort methods built into each programming language. The last one of importance is O of N squ. This is almost always associated with nested loops. So a for loop within a for loop.

```python
def quick_sort(arr: List[int]) -> List[int]:
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

```python
def merge_sort(arr: List[int]) -> List[int]:
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left: List[int], right: List[int]) -> List[int]:
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result
```

(09:17) Often this is when you're doing brute force comparisons. And just as a hint, this is usually too slow for large inputs and will not be accepted as a viable solution for interview problems. Now here's the basic rule of thumb. For inputs up to 10 the^ of 5, you probably need O of N log N or better. For inputs up to 10 ^ 4, you can maybe get away with O of N^2.

(09:45) And anything higher than that, you absolutely need to optimize. That about covers the introductory concept you need to know before moving on and learning these patterns. Now, if you feel comfortable, let's get started with learning the patterns and getting ready to ace these interviews.

(10:04) Hashmaps are the first data structure we'll be covering, and they're arguably the most useful pattern you'll learn in this entire video. At the most basic level, a hashmap is a way to store data using a key to find a value. It's a key value pair system. Think of how arrays work, but instead you use custom indices instead of the default numbers. Now, it's more complex than that, but that's a good way to start thinking about them.

(10:30) What makes hashmap so powerful is how it does this in constant time O of one on average for both lookup and insertion. Now how does this actually work? Imagine you have a huge row of mailboxes. Each mailbox has a unique number and instead of looking through every mailbox for someone's letter, you can just run their name through a formula known as a hash function and it tells you exactly which mailbox to open.

(11:00) So if I gave you a key like the string banana, the hash function will take banana and spit out a number like 243. That number points to a slot in memory and that's where your value is stored. You don't need to scan all keys. You don't need to sort anything.

(11:24) You just ask where does this key go? And the hash function gives you an immediate answer. And this is why hashmaps are so fast and so powerful. They don't depend on the size of the data. Whether you have 10 elements or a million, getting or setting a value takes the same amount of time. Now, in practice, two keys might sometimes get the same hash.

(11:45) This is called a collision. For example, maybe both banana and peach hash to 243. Fortunately, we don't have to worry about that. Most languages have built-in hashmap implementations that handle these collisions for us. I'm just mentioning it here so that you understand a bit more about how hashing actually works. And if you're interested, I recommend spending some free time and really digging into it because it's quite fascinating.

(12:12) Now, there's one really big rules about keys for hashmaps. They must be what's called hashable. What that mean depends on the specific language. But in general, numbers, strings, and tpples are all hashable. Whereas lists and dictionaries, which is just another name for hashmaps, are not hashable.

(12:35) So if you try to use a list or another hashmap/dictionary as a key, it'll throw an error because their contents can change. And hashmaps need keys that stay the same. This comes up more often than you'd think. For example, if you're grouping elements by their structure, like sorting strings and using them as keys, you'll need to convert them into a format that's hashable first.

(13:01) So, why are hashmaps so common in interviews? Because they're your go-to structure when brute force is too slow. Let's say you need to find a value that already exists. Without a hashmap, you're looping through everything you've seen so far, and that's O of N. But with a hashmap, you just need to check once, O of one.

(13:25) In a lot of interview problems, the real trick isn't some clever algorithm. It's just storing information in a smarter way. And a hashmap gives you that for free. Here's the mindset shift you need to make. When you solve problems with brute force, you're asking the same questions over and over. When you solve problems with a hashmap, you're remembering the answers as you go.

(13:49) It's a small shift, but it saves you tons of time and unlocks O of N solutions where others get stuck at O of N squ. Now, let's take a second to look at how hashmaps actually look in code. The syntax might vary by language, but the pattern stays the same. You're essentially doing three things. First, you're storing something. Then, you're looking something up.

(14:14) And optionally, you might update or initialize more values as you go. Here's a basic sketch of the code structure you'll use again and again. This structure is often referred to as a frequency map, and it's one of the most common patterns you'll see. As you can see, we're basically going through all of the items in some data list. And if an item doesn't already exist in our map, we're setting its count to one.

(14:41) And if it does exist, we're updating its count by plus one. There are language specific helpers that help clean up this code, such as defaultdict or map.get ordefault in Java, but the underlying logic is always the same. You're storing something under a key and either retrieving it or updating it later.

(15:06) Also, hashmaps are often used while you loop, not just after. So you're building and using the map in real time, which is what lets you write a onepass solution instead of having to loop twice. We'll come back to this idea when we look at real problems in a moment or two. For now, just keep this shape in your head. Initialize a map, use it while looping, and it gives you fast lookup and storage.

(15:32) Hashmaps are the most flexible structure in your toolbox. You'll use them in string problems, array problems, recursion, dynamic programming, graph traversal, literally everything. If you're ever stuck and don't know how to avoid brute force, just ask, "What could I store to avoid doing extra work later?" And if you can answer that, you're already halfway to a halfmap solution.

(15:59) All right, let's solve one of the most iconic interview problems, twosome. The setup is simple. You are given an array of integers and a target number. You need to return the indices of two numbers that add up to the target. This problem is deceptively simple and a perfect example of how using the right data structure makes all the difference. So, we start by identifying the pattern.

```python
def two_sum(nums: List[int], target: int) -> List[int]:
    num_to_index = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in num_to_index:
            return [num_to_index[complement], i]
        num_to_index[num] = i
    return []
```

(16:24) For this one, I'm going to choose the hashmap pattern. How did I know that? Well, because we know that we want to track which numbers we've seen before and be able to look them up instantly. Hashmaps are often great for questions like this where you need to ask, "Have I seen the corresponding value that completes this pair?" In this case, it's the number that adds to the current number we're looking at to create the target. Now, let's see how the code works.

(16:53) We start by creating an empty hashmap called num to index. This is going to store each number we see along with its index so we can quickly look it up later. Then we loop through the array using enumerate which gives us both the index i and the current number num. At each step we calculate the complement.

(17:19) That is the number we need to pair with the num to hit the target. And then we check our hashmap. Have we already seen this complement? If we have, it means the current number and that earlier complement add up to the target. So we should return their indices. If we haven't seen it yet, we store the current number in the map with its index.

(17:42) That way it'll be available for future numbers to match against. So doing this, we're only looping through the array once. And at each step, we're doing constant time lookups and inserts, making the whole thing super efficient. Now, analyzing the time and space complexity of this is quite easy once we just trace through what we're doing.

(18:04) So, let's start with the time complexity. Well, we know that in a worst case scenario, we might have to go through each element in nums exactly once. So that is going to be O of N time complexity because we might have to see all N elements. Now what about space complexity? Well, let's look at what we're doing. We're creating a new hashmap.

(18:29) And again, in worst case scenario, we might need to add every single number with its index to that hashmap. So the hashmap could be n elements long, meaning that our space complexity is also O of N. And that's it. Just like that, we solved a super popular interview problem using skills you didn't even know 10 minutes ago. Now, let's talk about another very common interview pattern. Two pointers.

(18:55) This is one of the most foundational patterns for solving problems that involve linear structures like arrays, strings, and even sometimes linked lists. You'll see it constantly in coding interviews. And the key is recognizing when to use it and how to adapt it to the shape of the problem. At a high level, two pointers is exactly what it sounds like.

(19:20) You use two indices or pointers to move through a structure. Usually in a way that helps you avoid nested loops or repeated scanning. You can think of it as reading a book with two fingers. One tracks the start of something, the other tracks the end. The trick is in how they move and why. There are two major types of the two-pointer technique.

(19:47) Both pointers move in the same direction and pointers move towards each other from opposite ends. Let's break each one down. The same direction pattern usually shows up when you're doing a single pass over the data, but you need to track a range, not just one element at a time. A classic example is the fast and slow two-pointer setup.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def find_middle(head: ListNode) -> ListNode:
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

```python
def has_cycle(head: ListNode) -> bool:
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

(20:12) You'll often see one pointer moving one step at a time, which is the slow pointer, and another one moving faster, two steps at a time. Now, why would you ever do that? Well, it lets you detect patterns in a single pass. For example, if the fast pointer reaches the end while one is halfway, you found the middle. or if the fast pointer ever laps the slow pointer, you've detected a cycle.

(20:39) The ability to find the middle of something or detect cycles are not only incredibly useful for a variety of reasons, but as you can see, extremely simple. Now, the opposite direction pattern is the more classic two-pointers implementation where one pointer starts at the beginning and the other starts at the end and they move inward.

```python
def most_water(height: List[int]) -> int:
    left, right = 0, len(height) - 1
    max_area = 0
    while left < right:
        max_area = max(max_area, min(height[left], height[right]) * (right - left))
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1
    return max_area
```

(21:00) You'll see this pattern used when the array is sorted and you're trying to find a pair or combination. You're comparing symmetric parts of a structure like checking for palendromes or you want to avoid nested loops when looking at all pairs. Now, here's the mental model for this. Your left pointer starts at zero.

(21:18) Your right pointer starts at the last index. Then you check the current pair and based on some condition which is problem dependent. So it could be their sum or checking if the two characters match. You move one of the pointers inward. The condition is always problem specific, but this pattern is consistent.

(21:43) Opposite direction two pointers are especially powerful in sorted arrays because each time you move a pointer, you can eliminate an entire range of possibilities. Instead of checking all combinations, which would be O of N^ squ, you're solving it in O of N. The reason two pointers are so powerful is because they let you reduce the number of iterations you need, track a relationship between two places in a structure, and avoid extra space by not needing sets or maps.

(22:10) This is one of the few techniques that can actually optimize both time and space complexity at once. It's also extremely intuitive once you practice it. You don't really need to memorize much at all. You just need to recognize the shape of the problem. In particular, two pointers come up a lot in problems involving the following.

(22:34) Often the problem won't say use two pointers. But if the brute force solution is checking all pairs or scanning repeatedly, it's usually a sign there's a more efficient way. So you should always ask yourself, can I do this by just walking the array once from both sides or in one pass? And if the answer is yes, two pointers is probably the most efficient way to go.

(22:59) Valid palendrome. The problem is simple in concept. We're given a string and we need to check if it reads the same forwards and backwards. But we're only supposed to consider letters and numbers, and we have to ignore casing. So, this isn't just a straight up mirror check.

```python
def is_palindrome(s: str) -> bool:
    left, right = 0, len(s) - 1
    while left < right:
        while left < right and not s[left].isalnum():
            left += 1
        while left < right and not s[right].isalnum():
            right -= 1
        if s[left].lower() != s[right].lower():
            return False
        left += 1
        right -= 1
    return True
```

(23:18) We have to skip over punctuation, spaces, and special characters. Let's look at how this solution handles that using two pointers. We start by setting up our left and right pointers. L starts at the beginning of the string and R starts at the end. Classic setup for this pattern.

(23:40) Now while the two pointers haven't crossed each other, that is while left is still less than right, we enter a loop. Inside the loop, the first thing we do is skip over non-alpha numeric characters. We do that by moving the left pointer forward until it's pointing at a valid character. And we do the same thing with the right pointer, moving it backward. This is important because we're only supposed to compare letters and numbers. Everything else just gets ignored.

(24:08) Once both pointers are on valid characters, we compare them. But we don't compare them directly because remember we're supposed to ignore case. So we lowerase both characters and then check if they're equal. If they're not equal, we can immediately return false because that means the string isn't a palendrome. If they are equal, we're good.

(24:35) So, we move both pointers inward, one step from the left, one step from the right, and keep going. This loop keeps repeating until the pointers meet in the middle. And if we never hit a mismatch, we return true because the string passed all our checks. So, the beauty of this solution is that it only scans each character at most once.

(25:00) No extra space, no reversing strings, just two pointers doing a clean pass through the input. And that's why the two-pointer pattern is so powerful for problems like this. Let's move on to the next one. All right, now let's look at another super common interview problem. It uses the same direction two pointers technique. Finding the middle of a linked list.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def find_middle(head: ListNode) -> ListNode:
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow
```

(25:19) The problem is simple on the surface. Given a linked list, return the middle node. And if the list has an even number of nodes, you return the second middle one. So for something like 0 points to 1, 1 to 2, 2 to 3, and 3 to 4, the middle is clearly two. But how do we find that efficiently in just one pass? Let's walk through the code and break it down.

(25:47) We start by creating two pointers, slow and fast, and we set both of them to the head of the list. Now, here comes the magic. We enter a loop. And while fast and fast next are still valid, we do two things. We move fast two steps forward, and we move slow just one step forward. So, fast races ahead while slow walks at a steady pace.

(26:08) Eventually, fast will hit the end of the list. And when that happens, slow will be sitting at the middle. We return slow.val. val which gives us the value of the middle node. Why does that work? Because for every two steps fast takes, slow only takes one. So by the time fast reaches the end, slow has only gone halfway.

(26:27) That's the beauty of this pattern. One traversal, no extra space, and it works for both odd and even length lists. In the even case, the slow pointer lands right on the second middle, which is exactly what we want. So that's it. The fast and slow pointer in action. Simple, elegant, and interview approved.

(26:49) The sliding window pattern is one of the most versatile techniques in coding interviews. It is a natural extension of the two-pointers pattern we just talked about, but with a tighter focus. Instead of tracking just two positions, you're managing an entire range of values. This range is what we call your window.

(27:09) And as the name suggests, you'll be sliding it across your data structure to inspect or process different segments of it without retraversing the same data over and over. If a problem is asking about contiguous segments like a substring, subarray, or a group of consecutive elements, a sliding window is almost always the right answer. Now, imagine you have a scanner and you're dragging it across a line of text.

(27:36) The scanner starts small and grows as you move forward or maybe shrinks depending on what you're looking for. At any given moment, you're only interested in what's inside the window. You don't care about anything before or after it. This is what makes sliding window efficient.

(27:59) You're looking at a subset of the data, adjusting the window as needed, and never revisiting the same element twice. And that last part is key. Just like two pointers, this gives us a clean way to reduce time complexity to O of N, even when the problem feels like it should require nested loops. Just like with two pointers, there are two main types of sliding window patterns.

(28:23) The first is fixed size, where the size of the window is predetermined and stays the same throughout. And the second is dynamic, where the window can shrink and expand as necessary. Now, let's break each one down. A fixedsized sliding window is used when the problem gives you a specific window size, usually with language like find the maximum average of any subarray of size k, return the sum of every klength block, or find the subarray of length k with the largest or smallest x.

```python
def max_average_subarray_of_size_k(nums: List[int], k: int) -> float:
    window_sum = sum(nums[:k])
    max_sum = window_sum
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        max_sum = max(max_sum, window_sum)
    return max_sum / k
```

```python
def sum_of_every_k_length_subarray(nums: List[int], k: int) -> List[int]:
    result = []
    window_sum = sum(nums[:k])
    result.append(window_sum)
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        result.append(window_sum)
    return result
```

```python
def subarray_with_smallest_sum_of_size_k(nums: List[int], k: int) -> int:
    window_sum = sum(nums[:k])
    min_sum = window_sum
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        min_sum = min(min_sum, window_sum)
    return min_sum
```

(28:56) In these problems, the windows length never changes. It always includes exactly k elements. And as you slide the window over the data, you add one new element from the right and remove one old element from the left, keeping the window size constant. The key is that you're maintaining a running window.

(29:18) And at every step, you're updating your result based on the current contents of the window. Now, let's walk through the code template you'll see over and over again. This is the template. Now let's break it down a bit. We start by grabbing the first window size elements as our initial window. This gives us a valid starting point to build from.

(29:41) Then we loop from window size till the end of the input. On each step, we're calculating left as right minus window size to give us the index of the element that just fell out of the window. Then we remove that old element from the window. We add the new input right to the end. And then we update our answer based on whatever the problem is asking.

(30:04) Max, min, sum, average, etc. Now let's move to the more flexible and more powerful version, the dynamic sized sliding window. This is used when the window size is not fixed and you're trying to find the largest, smallest, or optimal range that satisfies some condition.

(30:30) You'll usually see problems that sound like find the length of the longest substring with at most k unique characters. What's the smallest subarray with a sum greater than a target? Or return the longest window where a certain rule is valid. In these problems, the window grows and shrinks depending on the data. You expand the window to include more elements.

(30:51) And once the condition is violated, you start shrinking it from the left until it becomes valid. Again, this gives you complete control. You're not just sliding the window across. You're adjusting it in real time to maintain the right conditions. Here is the core pattern. Again, let's break this down so we understand it.

(31:13) You start with an empty window and grow it one element at a time from the right. Every time you add a new element, you check if the window is still valid. Once the window is valid, you update your answer. This usually means something like tracking the characters in the window to see if they meet some condition.

(31:34) If the window is invalid, you start removing elements from the left. and shrinking the window until it becomes valid again. Now let's see these two templates in action. Let's put the fixed size sliding window pattern into action with this problem. Maximum subarray of length k. We're given an array of non-gative numbers and a number k.

(32:00) And we need to find the largest possible sum of any subarray of length k. Since the subarrays must be exactly length k and consecutive, this is a perfect case for a fixed size sliding window. So here's how we solve it. First, we build the initial window by summing up the first k elements of the array. That gives us a starting point to compare against. We store that in a variable called window sum.

```python
def max_subarray_of_size_k(nums: List[int], k: int) -> int:
    window_sum = sum(nums[:k])
    max_sum = window_sum
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i - k]
        max_sum = max(max_sum, window_sum)
    return max_sum
```

(32:26) Then we copy that into a largest variable since this is our first and currently best subarray sum. Next, we slide the window forward through the rest of the array. We do this by looping from index K all the way to the end of the list. Each step forward means one number falls out of the window on the left and one new number enters on the right. So, first we figure out the index of the element that's now outside the window.

(32:51) That's right minus k, which we call left. Then we subtract nums at index left from our window sum since that value is no longer in the window. Next, we add in the new number at nums at index right which just entered the window.

(33:11) Now that our window is updated, we check if this new sum is larger than what we've seen before and update largest if so. We repeat that process until we've scanned the entire array. Finally, we return largest, which will hold the maximum sum we found across all klength windows. This is a classic example of how sliding window avoids extra work. We're not resuming each subarray from scratch.

(33:33) Instead, we're just adjusting the total by removing one number and adding another. Time complexity stays linear big O, which is exactly what we want in an interview. And that's it. Smooth and efficient. All right, let's try another real coding problem. And this one's a textbook example of when to use a dynamic sliding window. Find the length of the longest substring without repeating characters.

(33:57) We're given a string and we need to find the length of the longest substring that doesn't have any repeated characters. This kind of problem is perfect for the sliding window pattern because we're working with contiguous characters and we need to grow and shrink the range based on some rule. In this case, uniqueness.

```python
def longest_substring_without_repeating_characters(s: str) -> int:
    longest = 0
    left = 0
    counter = defaultdict(int)
    for right in range(len(s)):
        counter[s[right]] += 1
        while counter[s[right]] > 1:
            counter[s[left]] -= 1
            left += 1
        longest = max(longest, right - left + 1)
    return longest
```

(34:17) Let's look at a quick example to build some intuition before diving into the code. We'll use the input string A B CDB E A and walk through how the sliding window works. We'll start with both pointers, red on the right and blue on the left at the first character. That gives us the substring A, which is valid, and its length is one. Now we move the right pointer to B.

(34:44) Our window is now AB. No repeats, so we update our longest to two. Add C to the window. Now it's ABC. Still all unique. And we bump the longest up to three. Add D. We've got A B C D. All unique. Longest becomes four. Now we hit a repeat. We add B. And that gives us A B C DB. But B is already inside the window. So this window is invalid.

(35:12) To fix that, we slide the left pointer, the blue one, forward, one step at a time until B is no longer duplicated. We remove A, then remove the first B. Now we're left with C DB, which is valid again. Next, we add E. The window becomes B CDE E. No repeats, but the length is still four, so longest doesn't change. Add A.

(35:44) Now it's B CDE E A all unique again and now we have a new longest of five. At this point we've scanned through the whole string and we're done. The final answer is five. Now let's walk through how the code captures that exact logic. We start by setting up two variables longest which will track the maximum substring length we've seen so far and L which marks the start of our sliding window.

(36:09) We also set up a dictionary called counter which keeps track of how many times each character appears in the current window. We use default dict so that every character automatically starts with a count of zero. Then we loop through the string using a right pointer r. For each character at index r, we add it to our window by incrementing its count in counter. Now here's the important part.

(36:30) If the character we just added appears more than once, that means we have a duplicate and we need to fix the window. So, we use a while loop to shrink the window from the left. We subtract one from the character at the left pointer and move L forward by one.

(36:48) We repeat this until the character count goes back to one, meaning the window is valid again. Once the window is valid, we calculate its size using R minus L + 1. And if that's larger than our current longest, we update it. This process continues as we scan through the whole string, always expanding the window from the right and shrinking from the left as needed to maintain uniqueness. At the end, we return the value of longest, which gives us the length of the longest substring without repeating characters. This is a great example of a dynamic sliding window in action.

(37:18) You're not just moving across the string, you're constantly adjusting the window to match the rule you're enforcing. It's efficient. The time complexity is linear big O since every character is visited at most twice and the pattern is super reusable.

(37:38) Once you get comfortable tracking conditions like no repeats inside the window, you'll start to see this technique everywhere. Binary search is one of the most efficient algorithms in all of computer science. At its core, it's a way to take a big problem and cut it in half over and over again until you land on the answer. And that's the key idea. Cut the problem in half at every step.

(38:00) Instead of scanning the array from start to finish, which would take O of n time, binary search lets you find the answer in O log N time. But here's the thing. Binary search is so much more powerful than just searching for a number. And most people don't even realize it. So, let's start with the basics and then we'll generalize it to see how truly powerful it is.

(38:26) But first, the intuition. Imagine you're playing a number guessing game. I pick a number between 1 and 80, and you have to guess it in the least amount of moves. Each time you guess, I tell you if it's too high or too low. What should your first guess be? Well, you would probably guess 40 because it's right in the middle and you can automatically eliminate half the answers.

```python
def guess(arr: List[int], target: int) -> int:
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

(38:51) Now, based on this answer, you would then make another guess and cut the range in half again and again and so on until you find your answer. That's essentially what binary search is. Each guess lets you eliminate half the remaining options. And that's what gives you logarithmic time.

(39:12) You can even go from 1 million down to one in just about 20 steps. Far more efficient than scanning all 1 million values, which would take at worst a million steps. Now, let's take a look at starting with the binary search template that you might recognize. Let's start by taking a look at the vanilla binary search template, which is what most people may recognize.

(39:37) Now, let's break down how this vanilla binary search algorithm works line by line. This is our function definition. We're given a sorted list of integers ar and a target number that we want to find the index of. We set two pointers. Left starts at the beginning of the array and right starts at the end. These define the current search range we're looking at.

```python
def binary_search(arr: List[int], target: int) -> int:
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

(39:56) This loop runs as long as there's something to search, meaning our left pointer hasn't passed the right one. Once they cross, we know we've exhausted the search space. We calculate the middle index of the current range. Python's double slash is integer division. So this gives us a whole number.

(40:14) If you're using another language that handles division differently, check out documentation online. This is the ideal case. We found the target. So we return the index where it lives. If the middle value is less than our target, that means the target must be to the right of mid. So we discard the left half including mid and shift our left pointer to mid plus one.

(40:38) And if the middle value is greater than the target, then the target has to be on the left side. So we move the right pointer to mid minus one, cutting off the right half. If we exit the loop without finding the target, we return negative 1, meaning the element wasn't found in the array. And there we have it.

(40:56) This version of binary search is what you'll use anytime you're directly looking for a number in a sorted array. Here's where binary search gets really powerful. Remember how in the vanilla version we needed a sorted array to cut our search space in half? Turns out we don't actually need a sorted array. All we really need is a monotonic condition. A monotonic condition is one that only changes in one direction. If it's increasing, it won't ever decrease.

(41:21) And if it's decreasing, it won't ever increase. The reason this is powerful is because we can make definitive claims about what happens past a certain point. For example, take a look at the graph on screen. At the point where x= 5, y = 100. What if I asked you, will all the y values to the left of this be smaller than 100? On the monotonic slope, we can definitively say yes. So, we know that every value left of this is smaller and every value right of this is larger.

(41:55) but on the non-monotonic slope. We can't say that for certain because some values to the left are higher while some are lower. Doesn't this sound familiar? This is the exact premise that our vanilla binary search is based on. We look at a middle value and because we know everything to the left is smaller and everything to the right is larger, we can cut out half of the list immediately.

(42:19) So having a sorted array is a type of monotonic condition. But there are other types that don't appear as sorted arrays. Let's say we have a function f(x) that returns either true or false. If we plot the values of fx over a range, it might look like this. Once the function turns true, it stays true. That's what makes it monotonic. It only transitions once and in one direction.

(42:43) Binary search can help us find that first true the boundary in logarithmic time as long as we can write a feasible function that answers is this index valid. This comes up a lot in problems such as ones where you're not given a sorted array but you're trying to minimize or maximize something and you can check whether a solution is valid for a given guess.

```python
def first_true(arr: List[bool]) -> int:
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid]:
            right = mid - 1
        else:
            left = mid + 1
    return left
```

(43:09) Sort of make sense? Let's take a look at the template line by line, and I'm sure it will make more sense. We're still using two pointers to define our search space. Nothing new yet. We keep track of the best candidate we've seen so far. If we find a position that returns true, we store it here, but keep searching left to see if there's an even earlier one. Classic binary search loop.

(43:34) We keep going until we've narrowed down the search space. Grab the midpoint as usual. Here's where things get different. We're not comparing values directly. Instead, we check if this index satisfies some condition. Think of this as asking, is this index good enough? If it is good enough, we store it as a possible answer and then move left in case there's an earlier index that also works.

(43:59) This is the key move when you're trying to find the first valid solution. If mid is not feasible, we discard it and move right. Finally, we return the best answer we found or negative one if nothing was ever feasible. This template might feel abstract at first, but once you plug it into a real problem, it clicks.

(44:20) Now, let's plug that pattern into a real problem to see it in action. We're given a sorted array of booleans. All the falses come first, followed by a bunch of TRs, and our job is to find the first index where the value is true. This setup is a classic monotonic condition.

```python
def first_true(arr: List[bool]) -> int:
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid]:
            right = mid - 1
        else:
            left = mid + 1
    return left
```

(44:39) Once the array turns true, it stays true. It never flips back. So the array might not look traditionally sorted, but it still has that one directional property we need. So how do we find that first true efficiently? Binary search. We start by setting our usual left and right pointers to cover the full array. and we'll keep track of the best candidate we've seen so far, the earliest index that's returned true.

(45:05) Inside the loop, we grab the midpoint and ask, is this index good enough? If the value at that index is true, that means it could be our answer. But we're greedy here. We want the first true. So, we update our boundary and keep searching to the left. If it's false, then this index and everything before it is invalid. So we shift our search to the right.

(45:29) This is the core idea of binary search on a feasibility function. We're not comparing values in the usual way. We're asking yes no questions about whether the index satisfies a condition. That lets us confidently shrink the search space in the right direction. Once the loop ends, we return the best index we found.

(45:53) If the array was all false, that fallback value of negative 1 gets returned. This approach lets us find the boundary, the first true in logarithmic time, no matter how big the array is. Pretty slick, right? Let's tackle a classic interview problem. Find the minimum in a rotated sorted array. We're given a sorted array that's been rotated at some unknown pivot.

```python
def find_min_in_rotated_sorted_array(arr: List[int]) -> int:
    left, right = 0, len(arr) - 1
    best = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] <= arr[-1]:
            best = mid
            right = mid - 1
        else:
            left = mid + 1
    return best
```

(46:14) So something like 10 20 30 40 50 might become 30 40 50 10 20. Our goal is to find the index of the smallest number in that array. At first, it might seem like binary search won't help here. The array isn't fully sorted anymore. But if you look closely, there's still structure we can use. Before the rotation point, the numbers are increasing. Then suddenly they drop.

(46:43) That drop is the pivot and the smallest number sits right at that turning point. What's cool is that this creates a kind of split in the array. Every number before the minimum is greater than the last number in the array, and every number starting from the minimum is less than or equal to the last number. That's a one-way transition.

(47:02) We've got a yes or no condition that only flips once. In other words, a monotonic pattern. So for each index, we can ask a question like, is this number less than or equal to the last number in the array? This gives us a series of false values followed by TRS.

(47:26) And now the problem becomes find the first index where the answer is true. If you've already seen the pattern for finding the first true in a boolean array, this should feel familiar. We're going to apply that same boundary finding binary search here. Let's walk through the code logic. We start with two pointers left and right covering the whole array. We also track the best candidate index we've seen so far.

(47:49) Each loop we find the midpoint and ask our condition. Is this number less than or equal to the last number? If the answer is yes, we store that index and move left looking for an earlier one. If the answer is no, we know we're still in the too big part of the array, so we shift right.

(48:11) Eventually, the pointers converge, and at that point, we found the boundary, the index of the smallest number. Even though the array looks unsorted, the key is that the condition we're testing is monotonic, which makes binary search possible. It's a clever way to turn a tricky-l looking array into something we can solve in logarithmic time.

(48:30) BFS, breath first search, is one of the most common and powerful patterns for traversing nonlinear structures like trees and graphs. The core idea is this. You explore the structure level by level. Start at the root or source node. Then visit all its neighbors, then all their neighbors, and so on before going deeper.

(48:51) This pattern is useful because it naturally gives you the shortest number of steps to reach something. A clean level order traversal and a guaranteed way to explore everything evenly and fairly. At the heart of BFS is a simple tool, a Q. This cue ensures we always explore nodes in the exact order we discovered them. First in, first out.

(49:15) But how we apply this differs slightly depending on whether we're working with a tree or a graph. Let's break down both cases. Trees are a special kind of graph that don't have cycles, meaning you can't loop back to a node you've already visited. That makes BFS on trees simpler. You don't need a visited set because the structure itself guarantees no repeats.

(49:37) Here's the exact template for running BFS on a tree. Let's break it down. We start with the root node and place it into a que. While the queue isn't empty, we remove the first node, FIFO. We look at all of its children. If any child meets the goal, we return it. Otherwise, we add the children to the queue and keep going. The Q ensures that we always finish one level before moving to the next.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def bfs_tree_level_order(root: TreeNode) -> List[int]:
    if not root:
        return []
    queue = deque([root])
    result = []
    while queue:
        node = queue.popleft()
        result.append(node.val)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
    return result
```

(50:01) This is what makes BFS so great for things like finding the shortest path in a tree or processing level by level. And because trees are a cyclic by definition, we don't need to worry about visiting the same node twice, which simplifies the logic a lot.

(50:20) Use this pattern when you're traversing a tree from top to bottom or root to leaves or when you care about depth, distance, or level based logic, or if you're looking for the first match or the closest node to the root. As long as you're working with a true tree, this version is clean and efficient. But once cycles are possible, we need something more. Graphs are more general than trees.

(50:40) They can have cycles, loops, and multiple connections between nodes, which means you can revisit the same node more than once if you're not careful. To prevent this, BFS on a graph must track visited nodes. Otherwise, you'll either do redundant work or worse, get stuck in an infinite loop. Here's the template for graph BFS. Let's break it down. Start with the root node in the queue and in the visited set.

(51:00) While the Q isn't empty, pop the next node from the front. Look at all of its neighbors. If a neighbor has already been visited, skip it. Otherwise, mark it as visited and incue it. This version guarantees two things. Every node is visited once you never enter a cycle or revisit paths unnecessarily.

(51:18) The key move here is when we mark nodes as visited. We do it when we incue them, not when we process them. That way, we avoid adding the same node more than once. Use this version when you're working with grids, adjacency lists, or networks. The structure can contain cycles or duplicate paths. You need to find the shortest number of steps or minimum moves. You're exploring possible states in puzzles, games, or logic problems.

```python
def bfs_graph_shortest_path(graph: Dict[int, List[int]], start: int, target: int) -> int:
    queue = deque([(start, 0)])
    visited = set([start])
    while queue:
        node, distance = queue.popleft()
        if node == target:
            return distance
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append((neighbor, distance + 1))
    return -1
```

(51:40) BFS on graphs is especially useful when all edges or moves have the same cost because it will always find the shortest path first. Both versions for trees and graphs follow the same fundamental structure. a queue for the current layer of exploration, a loop to process each node, and a branching step where neighbors or children are added to the queue.

(51:58) You'll see this structure everywhere from tree traversals to maze solving to social networks to shortest path problems. Once you know the pattern, you can recognize it immediately and fill in the details. And on that note, let's take a look at applying these patterns to some real life interview problems.

(52:16) All right, let's walk through a classic BFS problem. Binary tree level order traversal. The idea is simple. We're given the root of a binary tree and we want to return a list of values level by level. So the root level comes first, then the next layer of nodes, then the next, and so on, always from left to right. This is a perfect use case for BFS because BFS is all about exploring one layer at a time.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def bfs_tree_level_order(root: TreeNode) -> List[int]:
    if not root:
        return []
    queue = deque([root])
    result = []
    while len(queue) > 0:
        n = len(queue)
        new_level = []
        for _ in range(n):
            node = queue.popleft()
            new_level.append(node.val)
            for child in [node.left, node.right]:
                if child:
                    queue.append(child)
        result.append(new_level)
    return result
```

(52:41) Let's jump into the code. We start off by importing DK from Python's collections module. This gives us a superefficient queue that we'll use for our levelby level traversal. Now into the main logic, the level order traversal function. We first create an empty list called res, short for result, which will store all the levels of the tree as we go. Next, we initialize our queue with the root node already inside.

(53:07) Even if the tree has only one node, this is enough to kick off the traversal. We now enter a while loop and this is key. The loop keeps running as long as there are nodes left in the queue. In other words, as long as there's something to process at any level of the tree. Inside the loop, we grab the current size of the queue that tells us how many nodes are in this level.

(53:32) Think of it like freezing the queue at this moment in time. We're going to process only those nodes before moving on. We make a new level list to collect the values from this level. Now comes the core BFS step, a for loop that runs exactly n times, where n is the number of nodes in the current level.

(53:51) For each node, we pop it from the front of the queue, classic fifo behavior, and we add its value to the new level list. Then we look at its children. If the node has a left child or a right child, we append them to the queue so they'll be processed in the next round. That's it. We just rinse and repeat.

(54:10) After we finish processing all nodes at this level, we append the new level list to our result list. And when the queue finally runs out, meaning we've hit the bottom of the tree, we return res, which now holds all the levels in order. So to recap, we use a queue to control the order of traversal. At each level, we process the current set of nodes.

(54:36) For each node, we add its children to the queue, and we repeat until there's nothing left. This structure gives us a clean left to right level order traversal of the tree. Exactly what the problem is asking for. Let's walk through another real life interview problem, the flood fill problem, which is basically like simulating the paint bucket tool in MS Paint.

```python
def flood_fill(image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
    num_rows, num_cols = len(image), len(image[0])
    original_color = image[sr][sc]
    replacement_color = color
    def get_neighbors(coord: Tuple[int, int], color: int) -> List[Tuple[int, int]]:
        row, col = coord
        delta_row = [-1, 0, 1, 0]
        delta_col = [0, 1, 0, -1]
        for i in range(4):
            neighbor_row = row + delta_row[i]
            neighbor_col = col + delta_col[i]
            if 0 <= neighbor_row < num_rows and 0 <= neighbor_col < num_cols and image[neighbor_row][neighbor_col] == original_color:
                yield (neighbor_row, neighbor_col)
    def bfs(root: Tuple[int, int]):
        queue = deque([root])
        visited = [[False for _ in range(num_cols)] for _ in range(num_rows)]
        r, c = root
        color = image[r][c]
        image[r][c] = replacement_color
        visited[r][c] = True
        while len(queue) > 0:
            node = queue.popleft()
            for neighbor in get_neighbors(node, color):
                r, c = neighbor
                if visited[r][c]:
                    continue
                image[r][c] = replacement_color
                queue.append(neighbor)
                visited[r][c] = True
    bfs((sr, sc))
    return image
```

(55:01) You're given an image as a 2D grid where each number represents a color. Starting from a given pixel at row R, column C, you want to change the color of that pixel and every connected pixel with the same color to a new one. The key here is connected pixels, meaning all the ones that are directly touching up, down, left, or right, and have the same original color, not diagonally, just the four cardinal directions.

(55:27) This is a perfect place to use BFS on a grid since we want to explore all the connected regions evenly without going too deep too fast. Let's work through the code. We're starting off by grabbing the number of rows and columns from the image. Just some prep to help with boundary checks later. Then we define a helper function called get neighbors.

(55:47) This is where we figure out which adjacent pixels are part of the same region. We take a coordinate which is just a row call pair. And for each of the four directions, we calculate the neighbors row and column. We make sure the neighbor is still inside the bounds of the grid.

(56:06) And then we check if that neighbor has the same color as the one we started with. If it does, we yield it. That just means we found another connected pixel to explore later. Now comes the main part, BFS. We define a BFS function that takes in the starting coordinate or root. We initialize a Q with that starting pixel. Remember BFS always starts with a Q.

(56:31) We also create a visited grid, same size as the image, to track which pixels we've already handled because unlike trees, grids can loop back and we don't want to visit the same pixel more than once. Then we extract the row and column from our starting point, get the color we're trying to replace, and immediately update that pixel to the new replacement color.

(56:49) And of course, we mark it as visited. Now we start the actual BFS loop. As long as the queue isn't empty, we keep pulling out the next pixel to process. For each pixel, we use the get neighbors helper to find all its same color neighbors. If we find one we haven't visited yet, we update its color, add it to the queue so it can spread to its neighbors later, and mark it as visited.

(57:15) So, this is where the flood fill effect happens, one level at a time, expanding outward like ripples in water. Finally, once BFS is done, we return the updated image now with the connected region filled in with the new color. And that's it. A clean BFS on a grid with visited tracking to avoid cycles. Depth first search or DFS is one of the most common ways to explore tree or graph structures.

(57:41) If BFS is about going wide layer by layer, then DFS is about going deep. You pick a path and follow it as far as it can go. Only when you reach the end of that path do you back up and explore other options. The key idea behind DFS is this. Fully explore one branch before moving on to the next. DFS is used in problems where you need to explore every possibility.

(58:01) You want to visit all nodes, possibly in a specific order. You care about structure, not distance, like whether something exists, not how close it is. DFS is often implemented recursively using the call stack to manage where you are in the structure. In some cases, it can also be done iteratively with an explicit stack, but recursion is more common in interviews and easier to read.

(58:19) Let's look at how it plays out. Starting with trees, trees are a cyclic by definition. They branch downward and you can't loop back. That makes them a perfect fit for DFS. Here's the clean recursive DFS template for a tree. How it works? We first check if the current node is none. If it is, there's nothing to search. Return.

```python
def dfs_tree_target_exists(root: TreeNode, target: int) -> bool:
    if not root:
        return False
    if root.val == target:
        return True
    return dfs_tree_target_exists(root.left, target) or dfs_tree_target_exists(root.right, target)
```

(58:35) Then we check if the current node matches the target. If not, we go left and search down that entire subree. If we find something there, we return it. If not, we backtrack and go right. This is classic DFS. Go deep into the left sub tree first, then back up and try the right. The recursive call stack handles everything.

(58:54) It keeps track of where we are and automatically returns us to the previous node after exploring each path. And because trees don't have cycles, we don't need a visited set. DFS is what you'll use in many recursive tree problems such as flattening trees, building or checking structures, searching for nodes based on custom logic. The structure is simple and surprisingly powerful. When we move to graphs, the challenge changes.

(59:10) Now you can have cycles and it's possible to revisit the same node multiple times unless you're careful to handle that. DFS on graphs must track visited nodes just like BFS. Here's the template for recursive DFS on a graph. Breaking it down, you start at a root node and for each neighbor, if the neighbor has already been visited, skip it.

(59:29) Otherwise, mark it as visited and explore it recursively. This is where the graph DFS differs from tree DFS. There's no parent child assumption. You must manually avoid cycles and you might visit the same node from multiple paths unless blocked. The visited set is what guarantees each node gets visited exactly once and that you don't enter infinite recursion.

(59:47) DFS is especially powerful for problems involving puzzles and state exploration. Graph coloring, recursive traversal, backtracking, which we'll cover later. Just remember the presence of cycles is what separates trees from graphs in DFS logic. That's why visited is required here.

(1:00:05) As we can see, like the other strategies we've covered, DFS follows a reusable structure. You start at a node, mark it, and recursively explore neighbors or children. That's it. The variations come from when you return values, when you check conditions, how you track state across recursive calls, but the overall shape stays the same. Once you've seen this pattern a few times, it becomes second nature.

(1:00:23) So, let's start now and practice a few problems. All right, let's walk through a classic recursive DFS problem. Maximum depth of binary tree. So the idea here is simple. Given the root of a binary tree, we want to find the maximum depth. In other words, how far down does this tree go? What's the longest path from the root to a leaf? We're going to use DFS to solve this because, well, it's perfect for problems where we want to go all the way down each path.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def tree_max_depth(root: TreeNode) -> int:
    def dfs(node: TreeNode) -> int:
        if not node:
            return 0
        return 1 + max(dfs(node.left), dfs(node.right))
    return dfs(root) - 1 if root else 0
```

(1:00:53) Now, the helper function here is called DFS, and it follows that clean recursive template we looked at earlier. First up, we check if the current node is none. If it is, that means we've hit the end of a path, so we just return zero. There's no more depth to add here.

(1:01:12) Otherwise, we're at a real node, so we want to explore both its left and right sub trees. We do that by recursively calling DFS on both sides. We're asking, hey, what's the max depth of the left side? And what's the max depth of the right side? Once we have those two numbers, we take the bigger one because we care about the longest path and then we add one for the current node we're on.

(1:01:39) So it's like the depth of this subree is the max of my left and right plus one for myself. That's the recursive part building upward as we return from the calls. Now at the very end, we return DFS root minus one. Why minus one? It depends on how you're counting depth. In this solution, the author treats the root level as depth zero, not one. So we subtract one to match that definition.

(1:02:06) If the root is none, we just return zero directly. And that's it. Clean recursive DFS to find the depth of a tree. No visited set, no loops, no fancy tricks, just classic recursion going all the way down and bubbling the answers back up. All right, let's tackle the number of islands problem. So, here's the setup. You're given a two-dimensional grid of ones and zeros.

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def count_number_of_islands(grid: List[List[int]]) -> int:
    num_rows, num_cols = len(grid), len(grid[0])
    def get_neighbors(coord: Tuple[int, int]) -> List[Tuple[int, int]]:
        res = []
        row, col = coord
        delta_row = [-1, 0, 1, 0]
        delta_col = [0, 1, 0, -1]
        for i in range(4):
            neighbor_row = row + delta_row[i]
            neighbor_col = col + delta_col[i]
            if 0 <= neighbor_row < num_rows and 0 <= neighbor_col < num_cols:
                res.append((neighbor_row, neighbor_col))
        return res
    def dfs(coord: Tuple[int, int]):
        r, c = coord
        if grid[r][c] == 0:
            return
        grid[r][c] = 0
        for neighbor in get_neighbors(coord):
            nr, nc = neighbor
            if grid[nr][nc] == 1:
                dfs(neighbor)
    count = 0
    for r in range(num_rows):
        for c in range(num_cols):
            if grid[r][c] == 1:
                dfs((r, c))
                count += 1
    return count
```

(1:02:31) Think of ones as land and zeros as water. Your job is to count how many separate islands there are. And an island is just a group of land tiles connected vertically or horizontally, not diagonally. This problem can be solved in a few different ways, but we're using DFS here. We're exploring connected land, and we want to mark it all once we visited it. Let's break down how the solution works.

(1:02:56) We start by getting the number of rows and columns in the grid. Nothing fancy here, just setting up some variables so we know our bounds. Next up is a helper function called get neighbors. This gives us all the valid adjacent tiles up, right, down, and left for a given cell. We use two arrays, delta row and delta column to represent the movement in each direction.

(1:03:22) For each one, we calculate the new row and column and check that we're still inside the grid. If we are, we add that coordinate to the result. So, this function just returns the four connected neighbors for any given tile. Super useful for traversal. Now comes the core of the logic, the df's function. Here's what it does.

(1:03:42) It takes in a coordinate, a tile on the grid, and checks. Is this tile water? If it is, we just return. Nothing to explore. If it's land, we mark it as visited by setting it to zero. In other words, we're syncing this part of the island so we don't come back to it again. Then we loop through each of its neighbors.

(1:04:06) If any neighbor is also land, meaning it's a one, we recursively call DFS on that neighbor. So, we keep exploring outward, marking every connected land tile as visited. This is depth first search in action. We pick a direction and go deep until there's nothing left to explore. Once we've defined those helper functions, we move on to the main part of the code.

(1:04:26) We loop through every cell in the grid row by row, column by column. If we find a one, that means we've discovered an unvisited island. We call DFS to sync that entire island to mark all of its land as visited. And then we increment our island count. We keep going until we've checked every tile.

(1:04:45) And by the end, count tells us how many islands we found. And that's it. Each DFS call handles one full island. And because we mark every part of it as visited, we don't double count anything. It's clean, efficient, and a great example of how DFS shines in grid-based problems. Backtracking is a recursive problem solving technique that explores all possible configurations of a solution, but efficiently backs up when it realizes a path won't work. Think of it like this.

(1:05:16) You're trying to solve a puzzle by filling in decisions step by step. At every step, you try all possible options. If one leads to a dead end, you undo the last move and try something else. That undo part, that's what makes it backtracking. It's basically DFS with the ability to reverse a choice. You use backtracking when the solution involves combinations, permutations, partitions, or paths.

(1:05:33) You're building up a partial solution one step at a time. You want all possible solutions or the first valid one and you need a way to discard bad paths early instead of exploring them fully. It's commonly used in sudoku solvers, word searches, subset and permutation problems, constraintbased problems like end queens.

(1:05:51) Now let's look at the core pattern. We'll be storing our final results in this list. It could be valid permutations, combinations, solutions to a puzzle, etc. The core of backtracking is a recursive DFS function. Start index keeps track of where we are in the input. path is the current in progress solution.

(1:06:09) The additional states are optional things like counters, visited arrays, frequency maps, etc. that track constraints or states outside of the path. This is the base case. A leaf means we've reached a complete solution. Notice that we store a copy of path, not the path itself because the path will keep changing as we backtrack. If we didn't copy it, we'd overwrite all of our answers.

(1:06:27) At each step, we try all valid next choices or edges from the current state. In the case of permutations, this could be choosing the next available number. In wordbreak problems, this could be slicing the next substring. In subset generation, it could be whether to include or exclude the next element. This is a critical performance step. Prune early.

(1:06:44) If an option breaks a constraint, skip it. This keeps your algorithm from going down paths that can never lead to valid solutions. The earlier you can prune, the faster your backtracking runs. We commit to a decision. Add the current edge choice to our path. This is like choosing a number, a character, a tile, or a subset.

(1:07:02) This is where you update things like marking a number as used, decrementing a counter, flipping a value, tracking sum, product, frequency, etc. This lets you encode complex rules like you can only use this letter once or you can't exceed a sum. We move to the next step and repeat the process. This is where the search continues deeper and where all paths are explored.

(1:07:19) After we return from the recursive call, we undo the decision we just made. This is the back and backtracking. Without this, we'd be stuck on our first path forever. We also revert any state changes if needed to make sure the next iteration starts fresh. Here are some signs you're looking at a backtracking problem.

(1:07:36) The question wants you to generate all possible combinations or find all valid arrangements. You're making a series of choices, each of which affects the remaining options. The solution space is exponential, but you can prune it with smart rules. You're given a grid, board, set of digits, or string, and asked to form, build, place, or explore.

(1:08:00) If a problem sounds like try all the ways to do X but only return the valid ones, it's probably a backtracking problem. Once you've written backtracking a few times, you'll see that the structure is always the same. Only the details of pruning, edge generation, and state tracking change. And those details are what you get good at over time. Let's get started now by applying it to a few practice problems.

(1:08:18) All right, let's break down the solution to word search, which is a classic example of backtracking on a 2D grid. The goal here is to find whether a given word can be traced through adjacent letters on the board, moving up, down, left, or right without reusing the same cell. So, we're using backtracking to explore all possible paths through the board that could spell out the word.

```python
def word_search(board: List[List[str]], word: str) -> bool:
    def dfs(r: int, c: int, word_index: int) -> bool:
        if board[r][c] != word[word_index]:
            return False
        if word_index == len(word) - 1:
            return True
        char = board[r][c]
        board[r][c] = "*"
        coord = [(r + 1, c), (r - 1, c), (r, c + 1), (r, c - 1)]
        for nr, nc in coord:
            if dfs(nr, nc, word_index + 1):
                return True
        board[r][c] = char
        return False
    for r in range(len(board)):
        for c in range(len(board[0])):
            if dfs(r, c, 0):
                return True
    return False
```

(1:08:39) Inside the DFS function, the first thing we check is, does the current board cell match the letter we're looking for at this position in the word? If it doesn't match, we return false right away. That's pruning. No need to go further if the current path is already invalid. Then we check the base case.

(1:09:01) Are we on the last letter of the word and it matches? If yes, we've successfully found the entire word. So we return true. Now to avoid reusing the same cell, we mark the current one with a special character. Here it's an asterisk. This is our way of saying, hey, this cell is already used in this path. Next, we define the four directions we can move in.

(1:09:24) Up, down, left, and right. For each of these directions, we check if the next cell is still inside the board boundaries. If it is, we recursively call DFS to explore that cell as the next character in the word. If any of those recursive calls return true, that means we found a valid path. So, we bubble up that result and return true.

(1:09:46) And here comes the backtracking part. After exploring, we reset the current cell back to its original letter. This is the undo step, so the board is clean for the next path we want to try. Outside the DFS, we loop over every cell in the board. We treat each one as a potential starting point for the word.

(1:10:07) If DFS from any of them returns true, we're done. The word exists in the grid. And if we finish checking every cell and none of the paths worked out, we return false. So again, this is classic backtracking. We're exploring all paths, pruning ones that can't work, and carefully restoring state after each step. Lastly, but not least, we have priority cues, also known as heaps.

(1:10:34) A priority Q is a special kind of Q where elements are removed in order of priority, not just in the order they were added. Under the hood, priority cues are usually implemented as binary heaps, which are just binary trees stored in arrays. There are two main kinds. For a min heap, every parent is smaller than its children. For a max heap, every parent is larger than its children.

(1:10:52) In Python, the default is a min heap, meaning the smallest element comes out first. But we can easily simulate a max heap by negating the values. That means insertion and removal both take big O of log time, which is fast enough for most real-time scheduling or selection problems.

(1:11:10) Priority cues show up in a ton of interview problems, especially when you want to repeatedly extract the smallest or largest item efficiently. You're maintaining a top k or bottom k set of values. You need real-time ranking, greedy selection, or dextra style path finding. You need to sort on the fly, but don't want to pay the full big O of N log N cost for sorting the entire array.

(1:11:28) Priority cues are one of the easiest implementations, often utilizing simple libraries. So, the best way to learn these is to get right into it now with some practice problems. All right, let's put that heap knowledge to work with this classic problem. Finding the k closest points to the origin.

```python
def k_closest_points_to_origin(points: List[List[int]], k: int) -> List[List[int]]:
    heap: list[tuple[int, list[int]]] = []
    for pt in points:
        heappush(heap, (pt[0]**2 + pt[1]**2, pt))

    res = []
    for _ in range(k):
        _dist, pt = heappop(heap)
        res.append(pt)
    return res
```

(1:11:47) We're given a bunch of points on a 2D plane and we want to return the k points that are closest to 0 0 using regular uklidian distance. Now, remember, since we only care about which points are closest, not the actual distances, we can just compare the squared distances. That saves us from doing a square root for every point. Let's walk through the code. First, we import heap hop and heap push from Python's heapq module.

(1:12:12) This gives us a nice way to use a min heap where the smallest elements come out first. Next, we create an empty heap. We'll use this to keep track of all the points sorted by their distance to the origin. Now, we loop through each point in the input list. For every point, we calculate its squared distance from the origin. That's just x^2 + y^2.

(1:12:36) Then we push a tuple into the heap. The distance first and the point itself second. Why do we put the distance first? Because heaps in Python use the first item in the tupole to figure out the priority. So this makes sure the point with the smallest distance will bubble up to the top. All right. Once we've pushed all the points into the heap, we're ready to grab the top k.

(1:13:02) We create a result list and for k times, we pop the smallest element off the heap. That gives us the point with the next closest distance each time. We don't care about the distance anymore, so we just extract the point and add it to our result list. And finally, return the result. So overall, we're using a priority Q to help us efficiently pull out the k closest points without having to sort the entire list. The heat makes this fast.

(1:13:26) Each insertion and removal is logarithmic, and the code stays simple and readable. All right, let's dive into a classic selection problem using heaps. Finding the key largest element in an array. So, what are we trying to do here? We're given an unsorted list of numbers, and we need to find the keith largest.

```python
def k_largest_element(arr: List[int], k: int) -> int:
    nums = [-x for x in arr]
    heapify(nums)
    for _ in range(k - 1):
        heappop(nums)
    return -heappop(nums)
```

(1:13:47) Not just the Keith item, but the one that would sit in the Keith spot from the end if we sorted it. Now, since we just learned about heaps and especially how fast they are at pulling out the largest or smallest values, this is a great chance to use them in action. Here's what we're doing.

(1:14:07) First up, we take all the numbers and negate them. Why? Because Python's heap implementation is a min heap by default, meaning it always pops out the smallest value, but we want the largest ones to come out first. So by flipping the signs, we turn it into a max heap. Once we have our max heap, we call heapify, which rearranges the list so it satisfies the heap structure.

(1:14:31) This step only takes linear time, which is a nice bonus. Now the key largest element will be the one that comes out after we've removed the largest one, ka minus one times. So we pop from the heap k minus one times. Each pop gives us the current largest number. And finally, we return the number at the top of the heap. But don't forget to flip the sign back to get the original value.

(1:14:56) That's it. Fast, efficient, and no need to sort the entire array. Just a smart use of a heap.
