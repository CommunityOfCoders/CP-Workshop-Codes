# CP-Workshop-Codes

# Arrays and String
## Is Palindrome
```cpp
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
```cpp
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
```cpp
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
```cpp
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
```cpp
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
## Pair sum
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t; cin >> t;
    while (t--) {
        int n, sum; cin >> n >> sum;
        int arr[n];
        for (int i = 0; i < n; i++) {
            cin >> arr[i];
        }
        bool found = false;
        sort(arr, arr + n);
        int i = 0, j = n - 1;
        while (i < j) {
            if (arr[i] + arr[j] == sum) {
                found = true;
                break;
            }
            if (arr[i] + arr[j] > sum) j--;
            else i++;
        }
        if (found) cout << "Yes" << endl;
        else cout << "No" << endl;
    }
	return 0;
}
```

## Sort array of 0, 1, 2
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	//code
	int T;
	cin>>T;
	while(T--)
	{
	    int N;
	    cin>>N;
	    int A[N];
	    for(int i = 0; i < N; i++)
	        cin>>A[i];
	    int low = 0, mid = 0, high = N-1;
	    while(mid <= high)
	    {
	        switch(A[mid])
	        { 
	            case 0:
	                swap(A[low++],A[mid++]);
	                break;
	            case 1:
	                mid++;
	                break;
	            case 2:
	                swap(A[mid],A[high--]);
	                break;
	        }
	    }
	    for(int i = 0; i < N; i++)
	        cout<<A[i]<<" ";
	    cout<<endl;
	}
	return 0;
}
```
## Next Greater Element on Right
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() 
{
	int t; 
	cin >> t;
	while(t--) 
	{
	    int n; 
	    cin >> n;
	    long long int arr[n];
	    for(int i = 0; i < n; i++)
	        cin >> arr[i];
	        
        stack<long long int> st;
        long long int ans[n];
        for (int i = n - 1; i >= 0; i--) 
        {
            while (!st.empty() and st.top() < arr[i])
                st.pop();
            if (st.empty())
                ans[i] = -1;
            else 
                ans[i] = st.top();
            
            st.push(arr[i]);
        }
        
        for (int i = 0; i < n; i++)
            cout << ans[i] << " ";
        cout << endl;
	}
	return 0;
}
```
## Rain Water Harvesting

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
	int T;
	cin >> T;
	while(T--)
	{
	    int ans = 0;
	    int n;
	    cin >> n;
	    int A[n];
	    for(int i = 0; i < n; i++)
	        cin >> A[i];
	    int left[n],right[n];
	    left[0] = A[0];
	    for(int i = 1; i < n; i++)
	        left[i] = max(left[i-1], A[i]);
	    right[n-1] = A[n-1];
	    for(int i = n - 2; i >= 0; i--)
	        right[i] = max(right[i+1], A[i]);
	    for(int i = 0; i < n; i++)
	        ans += min(left[i], right[i]) - A[i];
	    cout << ans << endl;
	}
	return 0;
}
```
## Anagram (Sorting solution)
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t; cin>>t;
    while(t--)
    {
        string s1,s2;
        cin>>s1;
        cin>>s2;
        if(s1.length()==s2.length())
        {
            sort(s1.begin(),s1.end());
            sort(s2.begin(),s2.end());
            if(s1.compare(s2)==0)
            {
                cout<<"YES\n";
            }
            else
            {
                cout<<"NO\n";
            }
        }
        else
        {
            cout<<"NO\n";
        }
    }
	
    return 0;
}
```
# Recursion
## Binary Search
```cpp
#include<bits/stdc++.h>
using namespace std;
int bin_search(int A[],int left,int right,int k);
int main()
{
    int t; cin >> t;
    while(t--)
    {
        int N;
        cin>>N;
        int a[N];
        for(int i=0;i<N;i++)
            cin>>a[i];
        int key;
        cin>>key;
        int found = bin_search(a,0,N-1,key);
        cout<<found<<endl;
    }
}

int bin_search(int A[], int left, int right, int k)
{
    if(left>right) return -1; //  if left> right, value not found

    int mid = (left+right)/2;

    if(A[mid]==k) return mid;

    if(left==right) return -1;
    else{

        if(k<A[mid]) return bin_search(A,left,mid-1,k);

        else return bin_search(A, mid+1, right, k);
    }
}

```
## Fast Expo
```cpp
#include <iostream>
using namespace std;

long power(int a, int b, int c){
    if(b==1) return a;
    else{
        long x = power(a, b/2 , c);
        
        if(b%2 == 0) return (x*x) % c;
        else{
            return (x*x *a) % c;
        }
    }
}
int main() {
	int t; cin>>t;
	while(t--){
	    int a,b,c; cin>>a>>b>>c;
	    cout<<power(a,b,c)<<endl;
	}
	return 0;
}
```
## sqrt
```cpp
#include<bits/stdc++.h>
using namespace std;
long long int floorSqrt(long long int x);
  
//Position this line where user code will be pasted.
int main()
{
	int t;
	cin>>t;
	while(t--)
	{
		long long n;
		cin>>n;
		cout << floorSqrt(n) << endl;
	}
    return 0;   
}
// x: element to find square root

long long int getSquare(int val, int lo, int hi) {
    if (lo == hi) return lo;
    if (lo + 1 == hi) {
        if (hi * hi <= val) return hi;
        return lo;
    }
    
    long long int mid = (lo + hi) / 2;

    if ((mid * mid) > val) {
        return getSquare(val, lo, mid - 1);
    } else {
        return getSquare(val, mid, hi);
    }
}

long long int floorSqrt(long long int x) 
{
    return getSquare(x, 1, x);
}
```
# Dynamic Programming
## Longest Increasing Sub (Iterative Solution)
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    int t, n; cin >> t;
    while (t--) {
        cin >> n;
        int arr[n];
        for (int i = 0; i < n; i++) cin >> arr[i];
        
        int dp[n];
        dp[0] = 1;
        for (int i = 1; i < n; i++) {
            dp[i] = 1;
            for (int j = 0; j < i; j++) {
                if (arr[j] < arr[i]) {
                    dp[i] = max(dp[i], 1 + dp[j]);
                }
            }
        }
	
	// returns the max element of the array
        cout << *max_element(dp, dp + n) << endl;
    }
    return 0;
}
```
## Word Break (Recursion + Memoization Solution)
```cpp
#inlcude <bits/stdc++.h>
using namespace std;

// creating a global hash table
unordered_map<int, bool> H;

bool isPossible(string &s, vector<string> &dict, int index, int &len) {
    // base case
    if (index == len) return true;
    
    // if value for current index is already calculated return it directly
    // Memoization
    if (H.find(index) != H.end()) return H[index];
    
    // trying for all words begining with current index
    for (int i = index; i < len; i++) {
        string sub = s.substr(index, i - index + 1);
	
	// if the word exist in dict
        if (find(dict.begin(), dict.end(), sub) != dict.end()) {
	
 	    // then check for the remaining part recursively
            if(isPossible(s, dict, i + 1, len)) {
	    
	        // store the curr val in hash table before returning
                H[index] = true;
                return true;
            }
        }
    }
    
    // store the value in hash table before returning
    H[index] = false;
    return false;
}

int main() {
    int t; cin >> t;
    while (t--) {
        int n; cin >> n;
        vector<string> dict(n);
        for (int i = 0; i < n; i++) {
            cin >> dict[i];
        }
        string s; cin >> s;
        int len = s.length();
        H.clear();
        cout << isPossible(s, dict, 0, len) << endl;
    }
    return 0;
}
```
## Word Break (Iterative solution)
```cpp
#inlcude <bits/stdc++.h>
using namespace std;

int main() {
    int t; cin >> t;
    while (t--) {
        int n; cin >> n;
        vector<string> B(n);
        for (int i = 0; i < n; i++) {
            cin >> B[i];
        }
        string A; cin >> A;
        int N = A.length();
	
	// solution
        bool dp[N + 1];
        memset(dp, 0, sizeof dp);
        dp[0] = true;
        
        for (int i = 1; i <= N; i++) {
            for (int j = 1; j <= i; j++) {
                if (dp[j - 1] and find(B.begin(), B.end(), A.substr(j - 1, i - j + 1)) != B.end()) {
                    dp[i] = true;
                    break;
                }
            }
        }
        
        cout << dp[N] << endl;
    }
    return 0;
}
```
