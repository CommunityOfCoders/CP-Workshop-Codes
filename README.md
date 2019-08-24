# CP-Workshop-Codes

## Is Palindrome
```
#include <bits/stdc++.h>
using namespace std;

int main() {
    
    // test cases
    int t;
    cin >> t;
    
    while (t--) {
        int n; cin >> n;
        string s;
        cin >> s;
        
        int i = 0, j = n - 1;
        
        bool is_palin = true;
        while (i < j) {
            if (s[i] != s[j]) {
                is_palin = false;
                break;
            }
            i++;
            j--;
        }
        
        if (is_palin) cout << "Yes" << endl;
        else cout << "No" << endl;
    }
    
	return 0;
}
```

## Reverse a string
```
#include <bits/stdc++.h>
using namespace std;

int main() {
	//code
	
	int t;
	cin >> t;
	
	while (t--) {
	    string s;
	    cin >> s;
	   // int i = 0, j = s.length() - 1;
	   // while(i < j) {
	   //     swap(s[i], s[j]);
	   //     i++; j--;
	   // }
	   
	    reverse(s.begin(), s.end());
	    cout << s << endl;
	}
	
	return 0;
}
```
## Reverse words in a string
```
#include <bits/stdc++.h>
using namespace std;

int main() {
    
    int t;
    cin >> t;
    
    while (t--) {
        // input
        string s; cin >> s;
        
        // reverse given string
        reverse(s.begin(), s.end());
        
        // reversing the words
        int start = 0;
        for (int i = 0; i < s.length(); i++) {
            
            if (s[i] == '.') {
                reverse(s.begin() + start, s.begin() + i);
                start = i + 1;
            }
        }
        
        // reversing the last word;
        reverse(s.begin() + start, s.end());
        
        // output
        cout << s << endl;
    }
    
	return 0;
}
```

## Paran Matching (only one type of brace)
```
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t; cin >> t;
    while (t--) {
        string s; cin >> s;
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(') {
                count++;
            } else count--;

            if (count < 0) {
                break;
            }
        }

        if (count == 0) cout << "True" << endl;
        else cout << "False" << endl;
    }
}
```

## Paran Matching (Multiple)
```
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t; cin >> t;
    while (t--) {
        string s; cin >> s;
        
        // CREATING A STACK!!!!!!! YAY YAY YAY --- WE DID NOT IMPLEMENT THISSS
        stack<char> st;
        
        bool is_true = true;
        for (int i = 0; i < s.length(); i++) {
            if (s[i] == '(' or s[i] == '[' or s[i] == '{') {
                st.push(s[i]);
            } else if (s[i] == ')' and !st.empty() and st.top() == '(') {
                st.pop();
            } else if (s[i] == ']' and !st.empty() and st.top() == '[') {
                st.pop();
            } else if (s[i] == '}' and !st.empty() and st.top() == '{') {
                st.pop();
            } else {
                is_true = false;
                break;
            }
        }
        
        if (is_true and st.empty()) cout << "balanced" << endl;
        else cout << "not balanced" << endl;
    }
}
```
