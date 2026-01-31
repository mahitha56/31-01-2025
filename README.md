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



#
