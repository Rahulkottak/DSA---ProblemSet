# DSA---ProblemSet
# Question 1 -> Unique Outcomes of Pair Deletions.


 Alex has a string 𝑠, consisting of lowercase Latin letters.
 One day, Alex decided to experiment with his string by removing two consecutive characters from it. Now, you are curious to find out how many distinct strings can be obtained after such an operation.

 For instance, if Alex has a string "aaabcc", you can get the following different strings: "abcc" (by deleting the first two or second and third characters), "aacc" (by deleting the third and fourth characters), "aaac" (by deleting the fourth and fifth characters), and "aaab" (by deleting the last two characters). So, there are 4 unique outcomes after deletion.

Constraints - 3 ≤ n ≤ 2⋅10^5

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
