Reading Books
```
#include <bits/stdc++.h> 
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n;
    cin>>n;
    vector<ll>a;
    ll sum=0,m=0;
    F(i, n){
        ll p;
        cin>>p;
        if (p>m) {
            sum+=m;
            m=p;
        }
        else sum+=p;
    }
    if (sum<m) cout<<2*m;
    else cout<<sum+m;
    
}

```
Missing Coin Sum
```
#include <bits/stdc++.h> 
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n;
    cin>>n;
    vector<ll> a;
    read(a, n);
    ss(a);
    ll m=0;
    for (auto x: a){
        if (x>m+1) break;
        m+=x;
    }
    cout<<m+1;
    
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
Valuable Cards
```
#include <bits/stdc++.h> 
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {int q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
#define vi vector<int>
#define vll vector<ll>
const int mod=1e9+7;

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n,x;
        cin>>n>>x;
        vi a;
        int ans=1;
        set<int> products;
        F(i, n){
            int q;
            cin>>q;
            if (x%q==0){
                if (products.count(x/q)){
                    ans++;
                    products.clear();
                }
                vi new_p;
                new_p.PB(q);
                for (int p: products) {
                    if (p*q<=x) new_p.PB(p*q);
                }
                for (int p: new_p) products.insert(p);
            }
        }
        cout<<ans<<"\n";
    }
    
}
```
Strange Beauty
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

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    ll l;
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        map<int, int> freq;
        int m=0;
        F(i, n){
            int q;
            cin>>q;
            freq[q]++;
            m=max(m, q);
        }
        vi dp(m+1, 0);
        int ans=0;
        for (const auto& [x, f] : freq) {
            int pre=0;
            for (int i=1; i*i<=x; i++){
                if (x%i==0) {
                    pre=max(pre, dp[i]);
                    pre=max(pre, dp[x/i]);
                }
            }
            dp[x]=f+pre;
            ans=max(ans, dp[x]);
        }
        cout<<n-ans<<"\n";
    }
    
}
```
