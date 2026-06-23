Distinct Numbers
```
#include <bits/stdc++.h>
using namespace std;
int main() {
ios::sync_with_stdio(0);
cin.tie(0);
int n;
cin>>n;
set<int> a;
for (int i=0; i<n; i++) {
int x;
cin>>x;
a.insert(x);
}
cout<<a.size()<<"\n";
}
```
Apartments
```
#include <bits/stdc++.h>
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m, k, x;
    cin>>n>>m>>k;
    vector<int> a, b;
    F(i, n){
        cin>>x;
        a.PB(x);
    }
    F(i, m){
        cin>>x;
        b.PB(x);
    }
    ss(a);ss(b);
    int u=0, l=0, count=0;
    while(u<n && l<m){
        
            if (a[u]-b[l]>k) l++;
            else if (a[u]-b[l]<-k) u++;
            else {count++;u++;l++;}
            
 
    }
    cout<<count;
 
}
```
Ferris Wheel
```
#include <bits/stdc++.h>
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, x, p;
    cin>>n>>x;
    vector<int> a;
    F(i, n){
        cin>>p;
        a.PB(p);
    }
 
    ss(a);
    int u=n-1, l=0, count=0;
    while(l<u){
        
            if ((a[u]+a[l])<=x) {
                count++;
                u--;
                l++;
            }
            else if (a[u]<=x) {
                count++;
                u--;
            }
            else u--;
            
 
    }
    if (u==l && a[u]<=x) count++;
    cout<<count;
 
}
```
Sort Colors
```
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int l=0, m=0, r=nums.size()-1;    
        while (m<=r) {
            if (nums[m]==0) {
                std::swap(nums[l], nums[m]);
                l++;
                m++;
            } 
            else if (nums[m]==1) {
                m++;
            } 
            else {
                std::swap(nums[m], nums[r]);
                r--;
            }
        }
    }
};
```
Factory Machines
```
#include <bits/stdc++.h> 
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
#define vi vector<int>
#define vll vector<ll>
const int mod=1e9+7;

bool check(ll m, const vector<ll>& a, ll t) {
    ll total=0;
    for (ll b: a) {
        total+=m/b;
        if (total>=t) return true;
    }
    return total>=t;
}

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n;
    ll t;
    cin>>n>>t;
    vll a(n);
    ll b=LLONG_MAX;
    
    F(i, n){
        cin>>a[i];
        b=min(b, a[i]);
    }
    ll l=1, r=b*t, ans=r;
    while (l<=r) {
        ll m=l+(r-l)/2;
        if (check(m, a, t)) {
            ans=m;
            r=m-1;
        } 
        else l=m+1;
    }
    
    std::cout << ans << "\n";
}
```
Container With Most Water
```
class Solution {
public:
    int maxArea(vector<int>& height) {
        int l=0, r=height.size()-1, ans=0;        
        while (l<r) {
            int curr=min(height[l], height[r]);
            ans=max(ans, curr*(r-l));
            if (height[l]<height[r]) l++;
            else r--;
        }
        
        return ans;
    }
};
```
Longest Substring Without Repeating Characters
```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        int n=s.length(), a=0, ans=0;
        vector<int>last(128,-1);
        for (int i=0; i<n; i++) {
            char ch=s[i];
            if (last[ch]>=a) a=last[ch]+1;
            last[ch]=i;
            ans=max(ans, i-a+1);

        }
        return ans;
    }
};
```
Static Range Sum Queries
```
#include <bits/stdc++.h>
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, q, a, b;
    ll val, sum=0;
    cin>>n>>q;
    vector<ll>nums, sums;
    sums.PB(0);
    F(i, n){
        cin>>val;
        nums.PB(val);
    }
    
    F(i, n){
        sum=sum+nums[i];
        sums.PB(sum);
    }
    while (q--) {
        cin>>a>>b;
        cout<<sums[b]-sums[a-1]<<"\n";
    }
}
```
Corporate Flight Bookings
```
class Solution {
public:
    vector<int> corpFlightBookings(vector<vector<int>>& bookings, int n) {
        vector<int> d(n+2, 0);
        for (const auto& booking : bookings) {
            int f=booking[0], l=booking[1], seats=booking[2];
            d[f]+=seats;
            d[l+1]-=seats;
        }
        vector<int> answer(n);
        int curr=0;
        for (int i=1; i<=n; i++) {
            curr+=d[i];
            answer[i-1]=curr;
        }
        return answer;
    }
};
```
Interesting Drink
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int i=0; i<n; i++) {int q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n,q;
    vector<int> a, b;
    cin>>n;
    read(a, n);
    cin>>q;
    read(b, q);
    ss(a);
    F(i, q){
        auto k= upper_bound(a.begin(), a.end(), b[i])-a.begin();
        cout<<k<<"\n";
    }
    
}
```
Books
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int i=0; i<n; i++) {int q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n,t;
    cin>>n>>t;
    vector<int>a;
    read(a, n);
    int l=0, m=0, sum=0;
    F(i, n){
        sum+=a[i];
        if (sum<=t) m=max(m, i-l+1);
        else {sum-=a[l];l++;}
    }
    cout<<m;
    
}
```
Number of Pairs
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int i=0; i<n; i++) {ll q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n, l, r;
        cin>>n>>l>>r;
        vector<ll>a;
        read(a, n);
        ss(a);
        int lower=n-1, upper=n-1;
        ll count=0;
        F(i, n){
            while (lower>=0 && a[lower]+a[i]>=l) lower--;
            while (upper>=0 && a[upper]+a[i]>r) upper--;
            int right=max(upper, i), left=max(lower, i);
            count+=right-left;
            
        }
        cout<<count<<"\n";
    }
    
}
```
Ilya and Queries
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int i=0; i<n; i++) {int q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int m;
    string s;
    cin>>s>>m;
    int n=s.length(), a=n-1;
    vector<int>switches(n, 0);
    int count=0;
    F(i, a){
        if (s[i]==s[i+1]) count++;
        switches[i+1]=count;
    }
    int l, r;
    while(m--){
        cin>>l>>r;
        cout<<switches[r-1]-switches[l-1]<<"\n";
    }
    
}
```
Little Girl and Maximum Sum
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int i=0; i<n; i++) {int q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, q;
    cin>>n>>q;
    vector<int>a, b(n+1, 0), c;
    read(a, n);
    ss(a);
    while(q--){
        int l,r;
        cin>>l>>r;
        b[l-1]++;
        b[r]--;
    }
    int sum=0;
    F(i, n){
        sum+=b[i];
        c.PB(sum);
    }
    ss(c);
    ll s=0;
    for (int i=0; i<n; i++) s+=(long long)a[i]*c[i];
    cout<<s;
    
    
}
```
