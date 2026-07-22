Production of Snowmen
```
#include <bits/stdc++.h>
using namespace std;
 
bool vibe(vector<int> v1, vector<int> v2, int q) {
        int n=v1.size();
        for (int i=0; i<n; i++) {
                if (v1[i]>=v2[(q+i)%n]) return false;
        }
        return true;
}
 
signed main(){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int t;
    cin>>t;
    while(t--){
            long long n;
            cin>>n;
            vector<int> v1(n), v2(n), v3(n);
            for (int i=0; i<n; i++) cin>>v1[i];
            for (int i=0; i<n; i++) cin>>v2[i];
            for (int i=0; i<n; i++) cin>>v3[i];
            long long p=0, q=0;
            for (int i=0; i<n; i++) if (vibe(v1, v2, i)) p++;
            for (int i=0; i<n; i++) if (vibe(v2, v3, i)) q++;
            cout<<p*q*n<<endl;
 
    }
}
```
New Year Cake
```
#include <bits/stdc++.h>
using namespace std;
 
signed main(){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int t;
    cin>>t;
    while(t--){
        int a, b;
        cin>>a>>b;
        int ao=floor(log2(3*a+1)/2), bo=floor(log2(3*b+1)/2), ae=floor(log2(3*a/2+1)/2), be=floor(log2(3*b/2+1)/2); 
        int o, e;
        if (ao==be) o=2*ao;
        else if (ao>be) o=2*be+1;
        else o=2*ao;
        if (ae==bo) e=2*ae;
        else if (ae>bo) e=2*bo;
        else e=2*ae+1;
        cout<<max(o, e)<<endl;
    }
}
```
Optimal Shifts
```
#include <bits/stdc++.h>
using namespace std;
 
signed main(){
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    int t;
    cin>>t;
    while(t--){
        int n;
        cin>>n;
        string s;
        cin>>s;
        int a=-1, maxi=INT_MIN, c=0, last;
        for (int i=n-1; i>=0; i--) {
                if (s[i]=='1') {last=i; break;}
        }
        for (int i=0; i<n; i++) {
                if (s[i]=='1') {
 
                        if (a==-1) c=i+n-1-last;
                        else c=i-1-a;
                        a=i;
 
                maxi=max(maxi,c);
                }
        }
        cout<<maxi<<endl;
    }
}
```
Spotlights
```
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n,m;cin>>n>>m;
    vector<vector<int> > stage(n,vector<int>(m,0));
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            cin>>stage[i][j];
        }
    }
    vector<vector<int> > rowcsum(n,vector<int>(m,0)),colcsum(m,vector<int>(n,0));
    for(int i=0;i<n;i++){
        rowcsum[i][0]=stage[i][0];
        for(int j=1;j<m;j++){
            rowcsum[i][j]=rowcsum[i][j-1]+stage[i][j];
        }
    }
    for(int i=0;i<m;i++){
        colcsum[i][0]=stage[0][i];
        for(int j=1;j<n;j++){
            colcsum[i][j]=colcsum[i][j-1]+stage[j][i];
        }
    }
    long long int pos=0;
    for(int i=0;i<n;i++){
        for(int j=0;j<m;j++){
            int temp=0;
            if(stage[i][j]==0){
                if(rowcsum[i][j]>0) temp++;
                if(rowcsum[i][m-1]-rowcsum[i][j]>0)temp++;
                if(colcsum[j][i]>0) temp++;
                if(colcsum[j][n-1]-colcsum[j][i]>0)temp++;
                pos+=temp;
            }
        }
    }
    cout<<pos<<endl;
}
```
Watchpig
```
#include <bits/stdc++.h>
using namespace std;
int main() {
    int t;cin>>t;
    while(t--){
        int n,k;cin>>n>>k;
        string s;cin>>s;
        vector<int>r(n,0),l(n,0);
        int cl=0,cr=0;
        if(s[0]=='R')r[0]==1;
        if(s[n-1]=='L') l[n-1]==1;
        for(int i=0;i<n;i++){
            if(s[i]=='R') cr++;
            else cl++;
        }
        if(k>n/2) cout<<-1<<endl;
        else{
            int count=0;
            for(int i=0;i<k;i++){
                if(s[i] == 'L') count++;
                if(s[n-1-i]=='R')count++;
            }
            cout<<count<<endl;
        }
    }
}
```
2 Movies
```
#include <bits/stdc++.h>
using namespace std;
int main(){
    int t;cin>>t;
    while(t--){
        int n;cin>>n;
        vector<int> m1(n,0),m2(n,0);
        for(int i=0;i<n;i++) cin>>m1[i];
        for(int i=0;i<n;i++) cin>>m2[i];
        int both=0,none=0,a=0,b=0;
        for(int i=0;i<n;i++){
            if(m1[i] == m2[i] && m1[i]==1) both++;
            else if(m1[i] == m2[i] && m1[i]==-1) none++;
            else if (m1[i]==1) a++;
            else if(m2[i]==1) b++;
        }
        int better=max(a,b),worse=a+b-better;
        int ans=0;
        while(both>0 && better!=worse){
            worse++;both--;
        }
        if(both>0){
            if(both>=none){
                both-=none;
                ans=better+both/2;
            }
            else{
                none=none-both;
                ans=better-max(none/2,(none+1)/2);
            }
        }
        else{
            while(none>0 && better!=worse){
                none--;better--;
            }
            if(none>0) ans=better-max(none/2,(none+1)/2);
            else ans=worse;
        }
        cout<<ans<<endl;
    }
}
```
Mexor
```

#include <bits/stdc++.h>
using namespace std;

int main() {
    int t;cin>>t;
    while(t--){
        int n, k;
    cin >> n >> k;

    if (k == n) {
        cout<<"YES"<<endl;
        for (int i = 1; i < n; i++) {
            cout << i << " ";
        }
        cout << 0 << endl;
        continue;
    }

    int ta = k ^ n;
    if (ta >= 1 && ta <= n - 1) {
        vector<int> a(n, 0);
        a[0] = 1;
        a[ta] = 1;
        cout<<"YES"<<endl;
        for (int i = 0; i < n; i++) {
            if (!a[i]) cout << i << " ";
        }
        cout << 0 << " " << ta << endl;
        continue;
    }
    int n1= -1, n2 = -1;
    for (int i = 1; i < n; i++) {
        int num = i ^ ta;
        if (num >= 1 && num <= n - 1 && num != i) {
            n1 = max(i, num);
            n2 = min(i, num);
        }
    }
    if(n1>0 && n2>0){
        vector<int> a(n, 0);
        a[0] = 1;
        a[n1] = 1;
        a[n2]=1;
        cout<<"YES"<<endl;
        for (int i = 0; i < n; i++) {
            if (!a[i]) cout << i << " ";
        }
        cout << 0 << " " << n2 <<" "<<n1<< endl;
        continue;
    }   
    cout<<"NO"<<endl;
    }
}
```
