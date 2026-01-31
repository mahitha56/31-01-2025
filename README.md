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
#prblm
class Solution:
    def firstUniqChar(self, s: str) -> int:
        # count=defaultdict(int)
        # for c in s:
        #     count[c]+=1
        # for i,c in enumerate(s):
        #     if count[c]==1:
        #         return i
        # return -1
        c=Counter(s)
        for i ,j in enumerate(s):
            if c[j]==1:
                return i
        return -1
#problem of find difference
s = original string
t = shuffled(s) + one extra letter
So:

👉 All letters same
👉 Only one extra letter is added

We must find that extra letter.

✅ Example
s = "abcd"
t = "abcde"
Extra letter → e

s = "aabb"
t = "ababb"
Extra letter → b

🔥 Best Solutions (3 ways)
✅ Method 1 — Counter (Easiest for beginners ⭐)
Since you're learning Counter, this is perfect for you.

from collections import Counter

s = "abcd"
t = "abcde"

cs = Counter(s)
ct = Counter(t)

for ch in ct:
    if ct[ch] != cs[ch]:
        print(ch)
Why works?
s → a:1 b:1 c:1 d:1
t → a:1 b:1 c:1 d:1 e:1
Only e is extra.

✅ Method 2 — Math sum trick (fastest ⚡)
Convert characters → ASCII numbers.

s = "abcd"
t = "abcde"

res = sum(ord(c) for c in t) - sum(ord(c) for c in s)

print(chr(res))
Why?
extra char ASCII remains
Very efficient 🚀

✅ Method 3 — XOR trick (interview favorite ⭐⭐⭐)
This is the smartest one.

s = "abcd"
t = "abcde"

result = 0

for c in s + t:
    result ^= ord(c)

print(chr(result))
Why XOR works?
Properties:

a ^ a = 0
0 ^ b = b
So:

a^b^c^d ^ a^b^c^d ^ e
= e
All cancel → only extra remains 😎

✅ Which should YOU use?
Since you're practicing basics:

👉 Use:

Counter method
After comfortable:
👉 Learn XOR trick

✅ Final recommended code (clean)
from collections import Counter

def findTheDifference(s, t):
    return list(Counter(t) - Counter(s))[0]
If you want, I can next:
✅ dry run with example
✅ explain XOR visually
✅ give similar practice problems

Just tell 😊

You said:
for c in s + t:
    result ^= ord(c) why we add s+t  and also tell me ord()
ChatGPT said:
Great question 👍
This XOR trick is very famous in interviews, so understanding it clearly will help you a lot.

Let’s go slowly and simply 😊

✅ First question:
Why for c in s + t ?
s + t means:
Concatenate both strings

Example:

s = "abc"
t = "abce"

s + t
Result:

"abcabce"
Why combine both?
Because we want to:

👉 XOR all characters of s
👉 XOR all characters of t

Together.

Instead of writing:

for c in s:
for c in t:
We simply do:

for c in s + t:
Cleaner code ✅

✅ Main Logic (IMPORTANT)
Remember XOR properties:

a ^ a = 0
0 ^ b = b
Example
s = "abc"
t = "abce"
Combined:

abcabce
Now XOR:

a ^ b ^ c ^ a ^ b ^ c ^ e
Cancel pairs:

(a ^ a) = 0
(b ^ b) = 0
(c ^ c) = 0
Left with:

0 ^ e = e
So result = e

✅ Second question:
What is ord() ?
ord() → gives ASCII (number) value of character
Example:

print(ord('a'))  # 97
print(ord('b'))  # 98
print(ord('A'))  # 65
Why we need ord()?
Because:

❌ XOR works only on numbers
✅ Not characters

So we convert:

'a' → 97
'b' → 98
Then XOR works.

✅ Reverse of ord()
Use chr()

print(chr(97))  # 'a'
✅ Full dry run
s = "a"
t = "aa"
ASCII:

a = 97
XOR:

97 ^ 97 ^ 97
= 0 ^ 97
= 97
Then:

chr(97) = 'a'
Extra letter found ✅

✅ Final code again
result = 0

for c in s + t:
    result ^= ord(c)

print(chr(result))
✅ Quick memory tip
ord() → char → number
chr() → number → char
Since you're practicing coding problems daily, learning:
✔ Counter
✔ XOR
✔ ord/chr

will make many problems easy.

If you want, I can next explain XOR with small number examples visually 👍


