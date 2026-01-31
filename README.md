# 31-01-2025
#Theory
Anagram means two words (or strings) have the same characters with the same frequency, usually same length, but arranged in a different order.
✅ Simple definition
Two strings are anagrams if:
Lengths are equal
Characters are the same
Order can be different
Examples
✔️ Anagrams:
"listen" ↔ "silent"
"eat" ↔ "tea"
"rat" ↔ "tar"
❌ Not anagrams:
"rat" ↔ "rate" → length different
"cat" ↔ "car" → characters different
Why same length?
Because:
If characters are the same count → automatically length is same.
Example:
"eat" → 3 letters
"tea" → 3 letters
Python check methods
Method 1: sorting (easy)
s = "listen"
t = "silent"
print(sorted(s) == sorted(t))
Method 2: dictionary/count (faster)
from collections import Counter
print(Counter(s) == Counter(t))
Interview tip
👉 Sorting = O(n log n)
👉 Counter/HashMap = O(n) (better)
#problem
from collections import Counter
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # if len(s)!=len(t):
        #     return False
        # s1=sorted(s)
        # s2=sorted(t)
        # for i,j in zip(s1,s2):
        #     if i!=j:
        #         return False
        #         break
        # return True
        return Counter(s)==Counter(t)



#theory for unique character
Since you’re learning Python and practicing problems like anagram, duplicates, frequency, Counter is VERY useful for you.
✅ What is Counter?
Counter counts how many times each element appears.
It is from:
from collections import Counter
✅ Simple Example
from collections import Counter
s = "banana"
print(Counter(s))
Output:
Counter({'a': 3, 'n': 2, 'b': 1})
👉 Meaning:
a → 3 times
n → 2 times
b → 1 times
So it automatically creates a frequency dictionary.
✅ Same using dictionary (manual way ❌ long)
Without Counter:
d = {}
for ch in "banana":
    if ch in d:
        d[ch] += 1
    else:
        d[ch] = 1

print(d)
More code 😓
✅ With Counter (easy ✅)
Counter("banana")
Done 🎉
✅ Uses of Counter
1️⃣ Anagram check (very common)
from collections import Counter
s = "anagram"
t = "nagaram"
print(Counter(s) == Counter(t))
Why works?
Because both have same counts.
2️⃣ Find duplicates
nums = [1,2,3,1,2,1]
c = Counter(nums)
print(c)
Output:
Counter({1: 3, 2: 2, 3: 1})
Now you know which repeats.
3️⃣ Most frequent element
c = Counter([1,2,2,3,3,3])
print(c.most_common(1))
Output:
[(3, 3)]
👉 number 3 appears 3 times
4️⃣ Count words
text = "hi hello hi bye hello hi"
words = text.split()
print(Counter(words))
Output:
Counter({'hi': 3, 'hello': 2, 'bye': 1})
✅ How Counter looks internally?
It is basically:
Counter = dict + counting
Like:
{'a':3, 'b':2}
🔥 When YOU should use Counter
Since you’re solving coding problems, use Counter when:
✅ counting frequency
✅ anagram problems
✅ duplicates
✅ most common elements
✅ histogram type problems
✅ Quick summary
👉 Counter = automatic frequency dictionary
Counter("aabbc")
→ {'a':2, 'b':2, 'c':1}
If you'd like, I can next explain:
✅ most_common()
✅ elements()
✅ subtract()
✅ or practice problems using Counter




