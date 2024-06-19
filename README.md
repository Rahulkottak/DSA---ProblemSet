# DSA---ProblemSet
# Question 1 -> Unique Outcomes of Pair Deletions.


 Alex has a string 𝑠, consisting of lowercase Latin letters.
 One day, Alex decided to experiment with his string by removing two consecutive characters from it. Now, you are curious to find out how many distinct strings can be obtained after such an operation.

 For instance, if Alex has a string "aaabcc", you can get the following different strings: "abcc" (by deleting the first two or second and third characters), "aacc" (by deleting the third and fourth characters), "aaac" (by deleting the fourth and fifth characters), and "aaab" (by deleting the last two characters). So, there are 4 unique outcomes after deletion.

Constraints - 3 ≤ n ≤ 2⋅10^5

### Task - Print the number of Unique Outcomes after Pair Deletions.

Example- <br/>
1.
 Input- n=6, s="aaabcc"<br/>
 Output - 4 [Discussed in the question description]

2. Input- n=7, s="abacaba" <br/>
 Output - 3 <br/>
[Exaplanation - if Alex has a string "abacaba", you can get the following different strings: "acaba" (by deleting the first two or second and third characters), "ababa" (by deleting the third and fourth characters or fourth and fifth characters), "abaca" (by deleting the sixth and fifth characters or sixth and seventh characaters), So, there are 3 unique outcomes after deletion.] 

<br/>
Critical Cases
<br/>

3. Input- n=69, s="ojvqyaimlvkceujbwgjwhzjkelelytpntcafernwtdtnlqzpsccswbumdclhpffivfloz"<br/>
 Output - 65 
<br/>

4. Input- n=39, s="fzeamgptytxrfmpgkdwbkwnpmxxgkpavontstaf"<br/>
 Output - 36 
<br/>

5. Input- n=231, s="mhneqtevyqomtdofczbsjpmyrjpumnfdpqlufbtnvynangxjownjzwsbgisjuiberkmqpamfgujtolkslgikcvaczdhvxssmlhirpvdrxeekjpomtalalstfcdsvuvjuvkntflrhmfnbkxnruqicdanmntnquofwdsjmysrgsgbxilpvkzqkanxslxkihnzicfytelrhdxiaebradpfeyptqpbezxfctvtmtbax"<br/>
 Output - 221 
<br/>

```bash
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;
    string s;
    cin >> s;
    int res = n - 1;
    for (int i = 1; i + 1 < n; ++i) {
        if (s[i - 1] == s[i + 1]) {
            res--;
        }
    }
    cout << res << '\n';
}
```
#

# Question 2 -> Textoria's Smallest Spell

In the magical land of Textoria, there exists a special string s consisting of lowercase Latin letters.
In this land, you can perform two types of magical operations on the string:

Trim: Remove the last character of the string.
Duplicate: Cast a spell to duplicate the string, transforming s into s=s+s.

You can perform each of these operations any number of times.
Your quest is to find the lexicographically smallest string of length exactly 𝑘 that can be obtained by performing these operations on the original string s.
A string a is considered lexicographically smaller than a string b if one of the following conditions is met: 

-   a is a prefix of b, but 𝑎 ≠ 𝑏;
-   In the first position where a and b differ, the string a has a letter that appears earlier in the alphabet than the corresponding letter in b.

Constraints - 1 ≤ n , k ≤ 5000

### Task - Print the lexicographically smallest string of length k that can be obtained by doing the operations on string s.

1. Input- n=4, k=5, s="abcd"<br/>
 Output - aaaaa<br/>
[Exaplanation - "abcd" → "abc" → "ab"→"a"→ "aa" → "aaaa"→"aaaaaaaa" → "aaaaaaa" → "aaaaaa"→ "aaaaa".]
<br/>

2. Input- n=8, k=10, s="rghkbaqm"<br/>
 Output - rghkbaqmrg [Exaplanation - "rghkbaqm" → "rghkbaqmrghkbaqm" → "rghkbaqmrghkbaq"→"rghkbaqmrghkba"→ "rghkbaqmrghkb" → "rghkbaqmrghk"→"rghkbaqmrgh" → "rghkbaqmrg".]
<br/>

Critical Cases
<br/>

3. Input- n=1, k=100, s="z"<br/>
 Output - zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
<br/>

4. Input- n=58, k=1, s="zpmfhemekujuaxllscuoauxfcfguhxannmftoxpcmpqkrnktngxceenbdi"<br/>
 Output - z 
<br/>

5. Input- n=4, k=10, s="ddcd"<br/>
 Output - ddcddcddcd
<br/>

```bash
#include "bits/stdc++.h"
using namespace std;
 
string get(string s, int k){
    while((int)s.size() < k){
        s = s + s;
    }
    while((int)s.size() > k)
        s.pop_back();
    return s;
}
int main()
{
    int n, k;
    string s;
    cin >> n >> k;
    cin >> s;
 
    string pref = "";
    pref += s[0];
 
    string mn = get(pref, k);
 
    for(int i = 1;i < n;i++){
        if(s[i] > s[0]) break;
        pref += s[i];
        mn = min(mn, get(pref, k));
    }
    cout << mn << "\n";
}
```
