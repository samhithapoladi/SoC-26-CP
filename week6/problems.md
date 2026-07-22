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
    vi dp(n+1, -1);
    dp[0]=0;
    
    int ans=0;
    for (int i=1; i<=n; i++) {
        for (int j=0; j<i; j++) {
            if (dp[j]==-1) continue;
            int dist=abs(x[i]-x[j]) + abs(y[i]-y[j]);
            if (t[i]-t[j]>= dist) dp[i] = max(dp[i], dp[j] + 1);
            
        }
        ans=max(ans, dp[i]);
    }
    cout<<ans<<"\n";
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
An Alternative Way
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
const ll INF=1e17;
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vll a, b;
        read(a, n);
        read(b, n);
        ll s=0;
        bool ans=true;
        F(i, n) {
            s+=b[i]-a[i];
            if (s<0) {ans=false; break;}
        }
        if (ans) cout<<"YES\n";
        else cout<<"NO\n";
    }
}
```
RemovevomeR
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
const ll INF=1e17;
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n;
        string s;
        cin>>n>>s;
        bool a=false, b=false;
        for (char c: s){
            if (c=='0') a=true;
            else b=true;
        }
        int c=0;
        F(i, n-1) {
            if (s[i]!=s[i+1]) c++;
        }
        if (a && b && c<=1) cout<<2<<"\n";
        else cout<<1<<"\n";
    }
} 
```
Good times Good times
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
const ll INF=1e17;
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        ll x;
        cin>>x;
        int a=to_string(x).size();
        ll y=1;
        F(i, a) y*=10;
        cout<<y+1<<"\n";
    }
} 
```
Divide and Conquer
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
const ll INF=1e17;
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int x,y;
        cin>>x>>y;
        if (x%y==0) cout<<"YES\n";
        else cout<<"NO\n";
    }
} 
```
UnstableL
```
#include <bits/stdc++.h>
using namespace std;
void solve() {
    long long int n, k;
    cin >> n >> k;
    vector<long long int> a(n);
    for (int i = 0; i < n; ++i) {
        cin >> a[i];
    }

    vector<long long int > freqs;
    long long int current_count = 1;
    for (int i = 1; i < n; ++i) {
        if (a[i] == a[i - 1]) {
            current_count++;
        } else {
            freqs.push_back(current_count);
            current_count = 1;
        }
    }
    freqs.push_back(current_count); 
    sort(freqs.begin(), freqs.end());
    int num_unique = freqs.size();
    vector<long long int > suf_sum(num_unique + 1, 0);
    for (int i = num_unique - 1; i >= 0; --i) {
        suf_sum[i] = suf_sum[i + 1] + freqs[i];
    }
    long long int valid_arrays = 0;

    for (int i = 0; i < num_unique; ++i) {
        if (i > 0 && freqs[i] == freqs[i - 1]) {
            continue;
        }
        long long int v = freqs[i];
        long long int c = num_unique - i;    
        long long int f = suf_sum[i];        
        long long int diff = k - f;
        if (diff % c == 0) {
            if (k >= f - c * (v - 1)) {
                valid_arrays++;
            }
        }
    }

    cout << valid_arrays << endl;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    
    int t;
    cin >> t;
    while (t--) {
        solve();
    }
    
    return 0;
}
```
