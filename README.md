# Unique-substring-implementation-in-cpp
**Problem statement**
Given a string 's'. The task is to find the smallest window length that contains all the characters of the given string at least one time.
For eg.

A = aabcbcdbca, then the result would be dbca as of the smallest window will be dbca.

**code**

```


#include <bits/stdc++.h>

using namespace std;

string solve(string s)
{
    int i=0;
    int j=0;
    unordered_map<char,int>a;
    int window_len=0;
    int max_window_len=0;
    int start_window=-1;
    while(j<s.size())
    {
        char ch=s[j];
        if(a.count(ch) && a[ch]>=i)
        {
            i=a[ch]+1;
            window_len=j-i;
        }
        a[ch]=j;
        window_len++;
        j++;
        if(window_len>max_window_len)
        {
            max_window_len=window_len;
            start_window=i;
        }
        
    }
    return s.substr(start_window,max_window_len);
    
}
int main()
{
    string s;
    cin>>s;
    cout<<solve(s);

    return 0;
}
