Abraham's Great Escape
```
#include<iostream>
using namespace std;
 
 
int main(){
    int t;
    cin>>t;
    for (int y=0; y<t; y++) {
    int n, k;
    cin>>n>>k;
    const int a = n;
    int t[a][a];
    if (k==(n*n)-1) {
        cout<<"NO"<<endl;
    }
    
    else {cout<<"YES"<<endl;
        for (int i=0; i<n; i++) {
            for (int j=0; j<n; j++) {
                t[i][j]=1;
            }
        }
        for (int i=0; i<k/n; i++) {
            for (int j=0; j<n; j++) {
                t[j][i]=1;
            }
        }
        for (int i=0; i<k%n; i++) {
            t[i][n/k]=1;
        }
        if (n-k%n==1) {t[n-1][k/n]=2;}
        if (n-k%n>1 && k!=n*n) {
            t[n-1][k/n]=1;
            t[k%n][k/n]=3;}
            for (int p=k/n+1; p<n; p++){
                t[0][p]=3;
                for (int l=1; l<n; l++) t[l][p]=1;
            }
        
        for (int i=0; i<n; i++) {
            for (int j=0; j<n; j++) {
                if (t[i][j]==1) cout<<"U";
                if (t[i][j]==2) cout<<"R";
                if (t[i][j]==3) cout<<"D";
            }
            cout<<endl;
        }
    }
    }
}
```
Fruits
```
#include <bits/stdc++.h>
using namespace std;
long long int big = 1e9 + 7;

int main(){
    int n,m;cin>>n>>m;
    vector <int> a(n);
    for(int i=0;i<n;i++) cin>>a[i];
    map <string,int> fruit;
    for(int i=0;i<m;i++){
        string s;cin>>s;
        fruit[s]++;
    }
    vector<int> fnum;
    for(auto &pairf : fruit){
        fnum.push_back(pairf.second);
    }
    long long int bs=0;
    long long int as=0;
    sort(fnum.begin(),fnum.end());
    sort(a.begin(),a.end());
    for(int i=0;i<fnum.size();i++){
        as+= fnum[fnum.size()-1-i]*a[i];
        bs+= fnum[fnum.size()-1-i]*a[a.size()-i-1];
    }
    cout<<as<<" "<<bs<<endl;
    
}
```
Zero Sum Prefix
```
#include <bits/stdc++.h>
using namespace std;
long long int change(const vector<long long int> &v,int start, int end,long long int value){
    multiset <long long int> m;
    long long int csum=value;
    for(int i=start;i<end;i++){
        csum+=v[i];
        m.insert(csum);
    }
    map <long long int,long long int> idk;
    for(auto x:m){
        idk[x]++;
    }
    long long int ans=0,el=0;
    for(auto x:m){
        if(idk[x]>ans){
        ans=max(ans,idk[x]);
        el = x;
        }
    }
    return el;
}
int main(){
    int t;cin>>t;
    while(t--){
        int n;cin>>n;
        vector<long long int>arr(n),zeros;
        for(int i=0;i<n;i++) {cin>>arr[i];
                             if (arr[i]==0) zeros.push_back(i);}
                
        if(zeros.size()>0){
            long long int value=0;
            for(int i=0;i<zeros[0];i++){
                value+=arr[i];
            }
            
            for(int zin = 0; zin < zeros.size(); zin++){
                int start = zeros[zin];
                int end = (zin == zeros.size() -1)?n : zeros[zin + 1];
                
                arr[start] = -1*change(arr, start, end, value);

                for(int i = start; i < end; i++){
                    value += arr[i];
                }
        }}
        long long int csum=arr[0],score=0;
        if(csum==0) score++;
        for(int i=1;i<n;i++){
            csum +=arr[i];
            if(csum==0) score++;
        }
        cout<<score<<endl;
    
}}
```
Omar and Alternating Sums
```
#include <bits/stdc++.h>
using namespace std;
long long int big=1e9+7;
long long int possible(int n){
    long long int ans=1;
    for(int i=1;i<n;i++){
        ans*=2;
        ans%=big;
    }
    return ans;
}
tuple<long long, long long, long long> extendedGCD(long long a, long long b) {
    if (b == 0)
        return {a, 1, 0};
    auto [g, x1, y1] = extendedGCD(b, a % b);
    return {g, y1, x1 - (a / b) * y1};
}

long long modInverse(long long a, long long m) {
    auto [g, x, y] = extendedGCD(a, m);
    return (x % m + m) % m;
}
int main(){
    int t;cin>>t;
    while(t--){
    int n;cin>>n;
    vector<int>v(n,0);
        for(int i=0;i<n;i++)cin>>v[i];
        vector<int> unique,el;
        int count=1;
        el.push_back(v[0]);
        for(int i=0;i<n-1;i++){
            if(v[i]==v[i+1])count++;
            else {unique.push_back(count);el.push_back(v[i+1]);
            count=1;}
        }
        unique.push_back(count);
        long long int seq=1;
        long long int factor=1;
        for(int i=0;i<unique.size();i++){
            factor*=possible(unique[i]);factor%=big;
        }
        seq=factor;
        if(v[0]==-1){
            vector<pair<int,int> > gap;
            for(int i=0;i<el.size()-1;i++){
                if(el[i+1]-el[i]==1) gap.push_back({i,el[i]});
            }
            int num=unique[0];
            for(int i=0;i<gap.size();i++){
                // long long int temp=num*unique[gap[i].first];
//                 temp%=big;temp*=unique[gap[i].first+1];temp%=big;
//                 long long int ye=factor;
//                 ye*=modInverse(num,big);ye%=big;ye*=modInverse(possible(unique[gap[i].first+1]),big);ye%=big;
//                 ye*=modInverse(possible(unique[gap[i].first]),big);ye%=big;
//                 ye*=possible(num-1);ye%=big;ye*=possible(unique[gap[i].first+1]-1);ye%=big;
//                 ye*=possible(unique[gap[i].first]-1);ye%=big;
                seq+=factor;seq%=big;
            }
        }
        cout<<seq<<endl;
}}
```
Friendly Gifts
```
#include <bits/stdc++.h>
using namespace std;

#define F(i, n) for(int i=0; i<n; i++)
#define read(a, n) for(int j=0; j<n; j++) {ll q; cin>>q; a.push_back(q);}
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
        vi a;
        read(a, n);
        vector<vi> left(n+2, vi(n/2 + 2, n+1));

        vector<vi> right(n+2, vi(n/2 +2, -1));

        F(i, n){
            vector<bool> visited(n+1, false);
            int mini=a[i], maxi=a[i];

            for (int j=i; j<n; j++) {
                if (visited[a[j]]) break;
                visited[a[j]]=true;

                mini=min(mini, a[j]);
                maxi=max(maxi, a[j]);

                int len=j-i+1;
                if (len>n/2) break;

                if (maxi-mini==len-1) {
                    left[mini][len] = min(left[mini][len], j);
                    right[mini][len] = max(right[mini][len], i);
                }
            }
        }

        int Lmax=0;

        for (int L=1; L<=n/2; L++) {
            for (int x=1; x+2*L-1<=n; x++) {

                if (left[x][L]<right[x+L][L]) Lmax=max(Lmax, L);
                if (left[x+L][L]<right[x][L]) Lmax=max(Lmax, L);
            }
        }

        cout<<Lmax<<"\n";
    }
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
Potions
```
#include <bits/stdc++.h>
using namespace std;
long long int big = 1e9 + 7;
int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    int n;cin>>n;
    int arr[n];
    for(int i=0;i<n;i++)cin>>arr[i];
    multiset <long long int> m;
    long long int sum=0,count=0;
    for(int i=0;i<n;i++){
        if(sum<0 && m.size()==0) break;
        sum+=arr[i];count++;
        if(arr[i]<0) m.insert(arr[i]);
        if(sum<0 && m.size()>0){
                int first = *(m.begin());
                sum-=first;count--;m.erase(m.begin());
        }
    }
    cout<<count<<endl;
}
```
Simons and Cakes for Success
```
#include <bits/stdc++.h>
using namespace std;
signed main(){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int t;
    cin>>t;
    while(t--){
        long long n;
        cin>>n;
        long long ans=1, a=n;
        for (long long i=2; i*i<=a; i++) {
            if (a%i==0) {
                ans=ans*i;
                while (a%i==0) a=a/i;
            }
        }
        if (a>1) ans=ans*a;
        cout<<ans<<endl;
    } 
}
```
