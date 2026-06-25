Food for Animals
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
        ll a,b,c,x,y;
        cin>>a>>b>>c>>x>>y;
        ll p=max(0LL, x-a), q=max(0LL, y-b);
        if (p+q<=c) cout<<"YES\n";
        else cout<<"NO\n";
    }
}
```
Di-visible Confusion
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
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vll a;
        a.PB(0);
        read(a, n);
        bool possible=true;
        for (int i=1; i<=n; i++) {
            bool can=false;
            for (int j=2; j<=i+1; j++) {
                if (a[i]%j!=0) {
                    can=true;
                    break;
                }
            }
            if (!can) {
                possible=false;
                break; 
            }
        }
        if (possible) cout<<"YES\n";
        else cout<<"NO\n";
    }
}
```
Alice and the Cake
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
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
 
        map<ll, int> a;
        ll sum=0;
        F(i, n){
            ll q;
            cin>>q;
            a[q]++;
            sum+=q;
        }
 
        vll b;
        b.push_back(sum);
        bool possible=true;
        int k=b.size();
        for(int i=0; i<b.size(); i++){
            ll curr=b[i];
            if (b.size()-i>n+1) {
                possible=false;
                break;
            }
            if (a[curr] > 0) {
                a[curr]--;
            } else {
                if (curr<2) {
                    possible=false;
                    break;
                }
                ll x=curr/2;
                ll y=(curr+1)/2;
                b.PB(x);
                b.PB(y);
            }
        }
 
        if (possible && b.size()==2*n-1) cout<<"YES\n";
        else cout<<"NO\n";
    }
}
```
The Hard Work of Paparazzi
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
    int r,n;
    cin>>r>>n;
    vi t(n+1), x(n+1), y(n+1);
    t[0]=0; 
    x[0]=1; 
    y[0]=1; 
    for(int i=1; i<=n; i++) cin>>t[i]>>x[i]>>y[i];
    vi dp(n+1, -1), mdp(n+1, -1);
    dp[0]=0;
    mdp[0]=0;
    
    int ans=0, m=2*r;
    for (int i=1; i<=n; i++) {
        
        int j=i-1;
        while(j>=0 && t[i]-t[j]<m) j--;
        if (j>=0 && mdp[j]!=-1) dp[i]=1+mdp[j];
        
        for (int k=j+1; k<i; k++){
            if (dp[k]==-1) continue;
            int dist=abs(x[i]-x[k]) + abs(y[i]-y[k]);
            if (t[i]-t[k]>= dist) dp[i]=max(dp[i], dp[k]+1);
            
        }
        ans=max(ans, dp[i]);
        mdp[i]=max(mdp[i-1], dp[i]);
    }
    
    cout<<ans<<"\n";
}
```
Spy-string
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
 
bool valid(string& s, vector<string>& a){
    for (string& str:a){
        int d=0;
        for (int i=0; i<str.length(); i++) {
            if (s[i]!=str[i]) d++;
            if (d>1) return false;
        }
    }
    return true;
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    ll l;
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<string> a(n);
        F(i, n) cin>>a[i];
        string b=a[0];
        bool found=false;
        for (int i=0; i<m; i++){
            
            for (char c='a'; c<='z'; c++){
                b[i]=c;
                if (valid(b, a)) {
                    cout<<b<<"\n";
                    found=true;
                    break;
                }
            }
            b[i]=a[0][i];
            if (found) break;
        }
        if (!found) cout<<-1<<"\n";
    }
}
```
Minimizing Difference
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
    int n;
    ll k;
    cin>>n>>k;
    vll a;
    map<ll, int>freq;
    F(i, n){
        ll q;
        cin>>q;
        if (freq[q]==0) a.PB(q);
        freq[q]++;
    }
    ss(a);
    n=a.size();
    int l=0, r=n-1;
    ll ops=0;
    while (l<r && k>0){
        if (freq[a[l]]<=freq[a[r]]) {
            ll gap=a[l+1]-a[l];
            ll cost=gap*freq[a[l]];
            
            if (k>=cost) {
                k-=cost;
                freq[a[l+1]]+=freq[a[l]];
                l++;
            } else {
                ll steps=k/freq[a[l]];
                a[l]+=steps;
                k=0;
            }
        }
        else {
            ll gap=a[r]-a[r-1];
            ll cost=gap*freq[a[r]];
            
            if (k >= cost) {
                k-=cost;
                freq[a[r-1]]+=freq[a[r]];
                r--;
            } else {
                ll steps=k/freq[a[r]];
                a[r]-=steps;
                k=0;
            }
        }
    }
    cout<<a[r]-a[l];
    
    
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
Zero-Sum Prefixes
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
        int n;
        cin>>n;
        vll a(n), pre(n);
        ll sum=0;
        F(i, n){
            cin>>a[i];
            sum+=a[i];
            pre[i]=sum;
        }
        ll ans=0;
        map<ll, int> freq;
        int m=0;
        for (int i=n-1; i>=0; i--) {
            freq[pre[i]]++;
            m=max(m, freq[pre[i]]);
            if (a[i]==0) {
                ans+=m;
                freq.clear();
                m=0;
            }
        }
        ans+=freq[0];
        cout<<ans<<'\n';
        
    }
    
}
```
