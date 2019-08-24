# CP-Workshop-Codes

## Check if it is palindrome
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
