 Everyone Loves Tres
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
        if (n<2 || n==3) cout<<"-1"<<"\n";
        else if (n%2==0) {
            string ans(n-2, '3');
            ans+="66";
            cout<<ans<<"\n";
        } 
        else {
            string ans(n-4, '3');
            ans+="6366";
            cout<<ans<<"\n";
        }
        
    }
}
```
Spotlights
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
    int n,m;
    cin>>n>>m;
    vector<vi> a(n, vi(m));
    vector<vi> row(n, vi(m+1,0));
    vector<vi> col(m, vi(n+1,0));
    F(i, n){
        F(j, m){
            cin>>a[i][j];
            row[i][j+1]=row[i][j]+a[i][j];
            col[j][i+1]=col[j][i]+a[i][j];
        }
    }
 
    ll ans=0;
 
    F(i, n){
        F(j, m){
            if (a[i][j]==0) {
                if (row[i][j]>0) ans++;
                if (row[i][m]-row[i][j+1]>0) ans++;
                if (col[j][i]>0) ans++;
                if (col[j][n]-col[j][i+1]>0) ans++;
            }
        }
    }
 
    cout<<ans<<"\n";
}
```
Two Movies
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
        vi a, b;
        read(a, n);
        int p=0,q=0,r=0,s=0;
        F(i, n){
            int k;
            cin>>k;
            b.PB(k);
            if (a[i]==1){
                if (b[i]==1) r++;
                else p++;
            }
            else if (a[i]==0) {
                if (b[i]==1) q++;
            }
            else {
                if (b[i]==1) q++;
                else if (b[i]==-1) s++;
            }
        }
        while(r>0) {
            if (p<q) p++;
            else q++;
            r--;
        }
        while(s>0) {
            if (p>q) p--;
            else q--;
            s--;
        }
        cout<<min(p,q)<<"\n";
        
        
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
