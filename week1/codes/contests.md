Polycarp and Sums of Subsequences
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
    int t;
    cin>>t;
    while(t--){
        vector<ll>a;
        read(a, 7);
        cout<<a[0]<<" "<<a[1]<<" "<<a[6]-a[0]-a[1]<<"\n";
        
    }
    
}
```
Sum of Two Numbers
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
    int t;
    cin>>t;
    while(t--){
        ll n;
        cin>>n;
        ll x=0,y=0,m=1;
        bool xtra=true;
        
        while(n>0){
            int digit=n%10;
            if (digit%2==0){
                x+=(digit/2)*m;
                y+=(digit/2)*m;
            }
            else{
                if (xtra){
                    x+=((digit+1)/2)*m;
                    y+=(digit/2)*m;
                }
                else{
                    y+=((digit+1)/2)*m;
                    x+=(digit/2)*m;
                }
                xtra=!xtra;
            }
            m=m*10;
            n=n/10;
            
        }
        cout<<x<<" "<<y<<"\n";
        
    }
    
}
```
The Delivery Dilemma
```
#include <bits/stdc++.h> 
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
 
bool possible(ll x, int n, const vector<ll>&a, const vector<ll>&b){
    ll walk=0;
    F(i, n) if (a[i]>x) walk+=b[i];
    return walk<=x;
        
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vector<ll>a, b;
        read(a, n);
        ll bsum=0;
        for (int i=0; i<n; i++){
            ll q;
            cin>>q;
            b.PB(q);
            bsum+=q;
        }
        
        
        ll l=0,r=bsum,ans=r;
        while (l<=r){
            ll mid=(l+r)/2;
            if (possible(mid, n, a, b)) {ans=mid; r=mid-1;}
            else l=mid+1;
        }
        
        cout<<ans<<"\n";
        
        
    }
    
}
```
Meeting on the Line
```
#include <bits/stdc++.h> 
using namespace std;
 
#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
#define PB push_back
#define ss(a) sort(a.begin(), a.end())
#define ll long long
 
bool possible(double y, int n, const vector<ll>&a, const vector<ll>&b, double &x){
    double l=-1e10, r=1e10;
    
    F(i, n){
        if (y<b[i]) return false;
        double walk=y-b[i],xmin=a[i]-walk,xmax=a[i]+walk;
        
        l=max(l, xmin);
        r=min(r, xmax);
    }
    
    if (l<=r){
        x=(l+r)/2.0;
        return true;
    }
    return false;
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        vector<ll>a, b;
        ll amax=0, bmax=0;
        F(i, n){
            ll q;
            cin>>q;
            a.PB(q);
            amax=max(amax, q);
        }
        F(i, n){
            ll q;
            cin>>q;
            b.PB(q);
            bmax=max(bmax, q);
        }
    
        
        double l=0,r=1e9,ans=0;
        F(i, 75){
            double mid=(l+r)/2.0, current=0;
            if (possible(mid, n, a, b, current)){
                ans=current;
                r=mid;
            }
            else l=mid;
        }
        
        cout<<fixed<<setprecision(15)<<ans<<"\n";
        
        
    }
    
}
```
Joyboard
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
    int t;
    cin>>t;
    while(t--){
        ll n,m,k,ans;
        cin>>n>>m>>k;
        
        if (k>3) ans=0;
        else if (k==1) ans=1;
        else if (k==2) ans=min(m, n-1) +m/n;
        else ans=m- min(m, n-1) -m/n;
        
        cout<<ans<<"\n";
        
    }
    
}
```
Shawarma Tent
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
    ll n,sx,sy;
    cin>>n>>sx>>sy;
    ll u=0,d=0,l=0,r=0,p,q;
    F(i, n) {
        cin>>p>>q;
        if (p<sx) l++;
        if (p>sx) r++;
        if (q<sy) d++;
        if (q>sy) u++;
    }
    ll ans=0,x,y;
    if (l>ans) {
        ans=l;
        x=sx-1;
        y=sy;
    }
    if (r>ans) {
        ans=r;
        x=sx+1;
        y=sy;
    }
    if (u>ans) {
        ans=u;
        x=sx;
        y=sy+1;
    }
    if (d>ans) {
        ans=d;
        x=sx;
        y=sy-1;
    }
    cout<<ans<<"\n"<<x<<" "<<y;
    
}
```
Modulo Equality
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
    ll n,m;
    cin>>n>>m;
    vector<ll>a,b,temp(n);
    read(a, n);
    read(b, n);
    ss(b);
    ll ans=LLONG_MAX,x;
    
    F(i, n){
        x=(b[i]-a[0]+m)%m;
        for (int j=0; j<n; j++) temp[j]=(a[j]+x)%m;
        ss(temp);
        
        if (temp==b && x<ans) ans=x;
    }
    
    cout<<ans<<"\n";
    
}
```
Guess the K-th Zero
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
    int n, t, k;
    cin>>n>>t>>k;
    int l=1,r=n,mid,ans;
    
    while(l<r){
        mid=(l+r)/2;
        cout<<"? "<<1<<" "<<mid<<"\n";
        cout.flush();
        
        int ones, zeros;
        cin>>ones;
        
        if (ones==-1) exit(0);
        zeros=mid-ones;
        
        if (zeros>=k) r=mid;
        else l=mid+1;
    
    }
    ans=l;
    
    cout<<"! "<<ans<<"\n";
    cout.flush();
    
    
    
}
```
