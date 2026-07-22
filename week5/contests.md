Apple Tree
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
 
bool dfs(int s, int c, vector<vector<int>>& adj, vector<int>& visited) {
    visited[s]=c;
    for (auto u: adj[s]) {
         if (visited[u]==0) {
             if (!dfs(u, 3-c, adj, visited)) return false;
         }
         else if (visited[u]==visited[s]) return false;
    }
    return true;
}
 
int count(int s, int p, vector<vector<int>>& adj, vector<ll>& leaves){
    if (adj[s].size()==1 && s!=1) {leaves[s]=1; return 1;}
    leaves[s]=0;
    for (auto u: adj[s]){
        if (u!=p) leaves[s]+=count(u, s, adj, leaves);
    }
    return leaves[s];
    
    
}
 
 
void bfs(int x, int y, int n, vector<vector<int>>& adj, vector<bool>& visited){
    vector<int> distance(n+1, INF);
    vector<int> last(n+1, 0);
    vector<int> path;
    queue<int> q;
    visited[x] = true;
    distance[x] = 0;
    q.push(x);
    while (!q.empty()) {
    int s=q.front(); q.pop();
    for (auto u : adj[s]) {
        if (visited[u]) continue;
        visited[u]=true;
        last[u]=s;
        distance[u]=distance[s]+1;
        q.push(u);
    }
    }
    if (distance[y]==INF) cout<<"IMPOSSIBLE\n";
    else {
        cout<<distance[y]<<"\n";
        int curr=y;
        while(curr!=0) {
            path.PB(curr);
            curr=last[curr];
        }
        reverse(path.begin(), path.end());
        for (auto s: path) cout<<s<<" ";
    }
}
 
 
void djs(int x, int n, int k, vector<vector<pair<int, ll>>>& adj){
    priority_queue<pair<ll, int>> q;
    vector<vector<ll>> distance(n+1);
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; 
        ll d=q.top().first;
        q.pop();
        if (distance[a].size()==k) continue;
        distance[a].PB(-d);
        for (auto u: adj[a]) {
            int b=u.first;
            ll w=u.second;
            if (distance[b].size()<k) {
                q.push({d-w, b});
            }
        }
    }
    for(int i=0; i<k; i++) cout<<distance[n][i]<<" ";
}
 
void fw(int n, vector<vector<ll>>& distance) {
    for (int k=1; k<=n; k++) {
        for (int i=1; i<=n; i++) {
            for (int j=1; j<=n; j++) {
                if (distance[i][k] < INF && distance[k][j] < INF) distance[i][j]=min(distance[i][j], distance[i][k]+distance[k][j]);
            }
        }
    }
}
 
void bell(int n, vector<tuple<int, int, ll>>& edges, vector<ll>& distance){
    distance[1]=0;
    for (int i=1; i<=n-1; i++){
        for(auto e:edges){
        int a,b;
        ll w;
        tie(a,b,w)=e;
        if (distance[a]!=-INF) distance[b]=max(distance[b],distance[a]+w);
        }
    }
    for (int i=1; i<=n; i++){
        for(auto e:edges){
            int a,b;
            ll w;
            tie(a,b,w)=e;
            if (distance[a]!=-INF){
                if (distance[a]==INF || distance[a]+w>distance[b]) distance[b]=INF;
            }
        }
    }
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--) {
        int n;
        cin>>n;
        vector<vi> adj(n+1);
        F(i, n-1){
            int u, v;
            cin>>u>>v;
            adj[u].PB(v);
            adj[v].PB(u);
        }
        vector<ll> leaves(n+1, 0);
        count(1, 0, adj, leaves);
        int q;
        cin>>q;
        while(q--){
            int x,y;
            cin>>x>>y;
            ll ans=leaves[x]*leaves[y];
            cout<<ans<<"\n";
            
        }
        
        
    }
} 
```
Forever Winter
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
 
bool dfs(int s, int c, vector<vector<int>>& adj, vector<int>& visited) {
    visited[s]=c;
    for (auto u: adj[s]) {
         if (visited[u]==0) {
             if (!dfs(u, 3-c, adj, visited)) return false;
         }
         else if (visited[u]==visited[s]) return false;
    }
    return true;
}
 
int count(int s, int p, vector<vector<int>>& adj, vector<ll>& leaves){
    if (adj[s].size()==1 && s!=1) {leaves[s]=1; return 1;}
    leaves[s]=0;
    for (auto u: adj[s]){
        if (u!=p) leaves[s]+=count(u, s, adj, leaves);
    }
    return leaves[s];
    
    
}
 
 
void bfs(int x, int y, int n, vector<vector<int>>& adj, vector<bool>& visited){
    vector<int> distance(n+1, INF);
    vector<int> last(n+1, 0);
    vector<int> path;
    queue<int> q;
    visited[x] = true;
    distance[x] = 0;
    q.push(x);
    while (!q.empty()) {
    int s=q.front(); q.pop();
    for (auto u : adj[s]) {
        if (visited[u]) continue;
        visited[u]=true;
        last[u]=s;
        distance[u]=distance[s]+1;
        q.push(u);
    }
    }
    if (distance[y]==INF) cout<<"IMPOSSIBLE\n";
    else {
        cout<<distance[y]<<"\n";
        int curr=y;
        while(curr!=0) {
            path.PB(curr);
            curr=last[curr];
        }
        reverse(path.begin(), path.end());
        for (auto s: path) cout<<s<<" ";
    }
}
 
 
void djs(int x, int n, int k, vector<vector<pair<int, ll>>>& adj){
    priority_queue<pair<ll, int>> q;
    vector<vector<ll>> distance(n+1);
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; 
        ll d=q.top().first;
        q.pop();
        if (distance[a].size()==k) continue;
        distance[a].PB(-d);
        for (auto u: adj[a]) {
            int b=u.first;
            ll w=u.second;
            if (distance[b].size()<k) {
                q.push({d-w, b});
            }
        }
    }
    for(int i=0; i<k; i++) cout<<distance[n][i]<<" ";
}
 
void fw(int n, vector<vector<ll>>& distance) {
    for (int k=1; k<=n; k++) {
        for (int i=1; i<=n; i++) {
            for (int j=1; j<=n; j++) {
                if (distance[i][k] < INF && distance[k][j] < INF) distance[i][j]=min(distance[i][j], distance[i][k]+distance[k][j]);
            }
        }
    }
}
 
void bell(int n, vector<tuple<int, int, ll>>& edges, vector<ll>& distance){
    distance[1]=0;
    for (int i=1; i<=n-1; i++){
        for(auto e:edges){
        int a,b;
        ll w;
        tie(a,b,w)=e;
        if (distance[a]!=-INF) distance[b]=max(distance[b],distance[a]+w);
        }
    }
    for (int i=1; i<=n; i++){
        for(auto e:edges){
            int a,b;
            ll w;
            tie(a,b,w)=e;
            if (distance[a]!=-INF){
                if (distance[a]==INF || distance[a]+w>distance[b]) distance[b]=INF;
            }
        }
    }
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--) {
        int n,m;
        cin>>n>>m;
        vector<int> d(n+1, 0);
        F(i, m){
            int u, v;
            cin>>u>>v;
            d[u]++;
            d[v]++;
        }
        int a=0;
        F(i, n+1){
            if (d[i]==1) a++;
        }
        int x=m-a;
        int y=a/x;
        cout<<x<<" "<<y<<"\n";
        
        
    }
} 
```
Searching for Graph
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
 
bool dfs(int s, int c, vector<vector<int>>& adj, vector<int>& visited) {
    visited[s]=c;
    for (auto u: adj[s]) {
         if (visited[u]==0) {
             if (!dfs(u, 3-c, adj, visited)) return false;
         }
         else if (visited[u]==visited[s]) return false;
    }
    return true;
}
 
int count(int s, int p, vector<vector<int>>& adj, vector<ll>& leaves){
    if (adj[s].size()==1 && s!=1) {leaves[s]=1; return 1;}
    leaves[s]=0;
    for (auto u: adj[s]){
        if (u!=p) leaves[s]+=count(u, s, adj, leaves);
    }
    return leaves[s];
    
    
}
 
 
void bfs(int x, int y, int n, vector<vector<int>>& adj, vector<bool>& visited){
    vector<int> distance(n+1, INF);
    vector<int> last(n+1, 0);
    vector<int> path;
    queue<int> q;
    visited[x] = true;
    distance[x] = 0;
    q.push(x);
    while (!q.empty()) {
    int s=q.front(); q.pop();
    for (auto u : adj[s]) {
        if (visited[u]) continue;
        visited[u]=true;
        last[u]=s;
        distance[u]=distance[s]+1;
        q.push(u);
    }
    }
    if (distance[y]==INF) cout<<"IMPOSSIBLE\n";
    else {
        cout<<distance[y]<<"\n";
        int curr=y;
        while(curr!=0) {
            path.PB(curr);
            curr=last[curr];
        }
        reverse(path.begin(), path.end());
        for (auto s: path) cout<<s<<" ";
    }
}
 
 
void djs(int x, int n, int k, vector<vector<pair<int, ll>>>& adj){
    priority_queue<pair<ll, int>> q;
    vector<vector<ll>> distance(n+1);
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; 
        ll d=q.top().first;
        q.pop();
        if (distance[a].size()==k) continue;
        distance[a].PB(-d);
        for (auto u: adj[a]) {
            int b=u.first;
            ll w=u.second;
            if (distance[b].size()<k) {
                q.push({d-w, b});
            }
        }
    }
    for(int i=0; i<k; i++) cout<<distance[n][i]<<" ";
}
 
void fw(int n, vector<vector<ll>>& distance) {
    for (int k=1; k<=n; k++) {
        for (int i=1; i<=n; i++) {
            for (int j=1; j<=n; j++) {
                if (distance[i][k] < INF && distance[k][j] < INF) distance[i][j]=min(distance[i][j], distance[i][k]+distance[k][j]);
            }
        }
    }
}
 
void bell(int n, vector<tuple<int, int, ll>>& edges, vector<ll>& distance){
    distance[1]=0;
    for (int i=1; i<=n-1; i++){
        for(auto e:edges){
        int a,b;
        ll w;
        tie(a,b,w)=e;
        if (distance[a]!=-INF) distance[b]=max(distance[b],distance[a]+w);
        }
    }
    for (int i=1; i<=n; i++){
        for(auto e:edges){
            int a,b;
            ll w;
            tie(a,b,w)=e;
            if (distance[a]!=-INF){
                if (distance[a]==INF || distance[a]+w>distance[b]) distance[b]=INF;
            }
        }
    }
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int t;
    cin>>t;
    while(t--) {
        int n,p;
        cin>>n>>p;
        vector<vector<bool>> e(n+1, vector<bool>(n+1, false));
        for(int i=1; i<=n; i++) {
            int a=i%n +1, b=(i+1)%n +1;
            cout<<i<<" "<<a<<"\n";
            cout<<i<<" "<<b<<"\n";
 
            e[i][a]=true;
            e[i][b]=true;
            e[a][i]=true;
            e[b][i]=true;
        }
        int a=0;
        for (int i=1; i<=n && a<p; i++) {
            for (int j=i+3; j<=n && a<p; j++) {
                if (!e[i][j]) {
                    cout<<i<<" "<<j<<"\n";
                    e[i][j]=true;
                    e[j][i]=true;
                    a++;
                }
            }
        }
    }
} 
```
Substring
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
 
void dfs(int x, vector<vi>& adj, vector<vi>& dp, vector<int>& visited, bool& cycle, string& s){
    visited[x]=1;
    for (auto u: adj[x]){
        if (visited[u]==1) {cycle=true; return;}
        if (visited[u]==0) {
            dfs(u, adj, dp, visited, cycle, s);
            if (cycle) return;
        }
        F(i, 26) dp[x][i]=max(dp[x][i], dp[u][i]);
    }
    dp[x][s[x-1]-'a']++;
    visited[x]=2;
}
 
void bfs(int x, int y, int n, vector<vector<int>>& adj, vector<bool>& visited){
    vector<int> distance(n+1, INF);
    vector<int> last(n+1, 0);
    vector<int> path;
    queue<int> q;
    visited[x] = true;
    distance[x] = 0;
    q.push(x);
    while (!q.empty()) {
    int s=q.front(); q.pop();
    for (auto u : adj[s]) {
        if (visited[u]) continue;
        visited[u]=true;
        last[u]=s;
        distance[u]=distance[s]+1;
        q.push(u);
    }
    }
    if (distance[y]==INF) cout<<"IMPOSSIBLE\n";
    else {
        cout<<distance[y]<<"\n";
        int curr=y;
        while(curr!=0) {
            path.PB(curr);
            curr=last[curr];
        }
        reverse(path.begin(), path.end());
        for (auto s: path) cout<<s<<" ";
    }
}
 
 
void djs(int x, int n, int k, vector<vector<pair<int, ll>>>& adj){
    priority_queue<pair<ll, int>> q;
    vector<vector<ll>> distance(n+1);
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; 
        ll d=q.top().first;
        q.pop();
        if (distance[a].size()==k) continue;
        distance[a].PB(-d);
        for (auto u: adj[a]) {
            int b=u.first;
            ll w=u.second;
            if (distance[b].size()<k) {
                q.push({d-w, b});
            }
        }
    }
    for(int i=0; i<k; i++) cout<<distance[n][i]<<" ";
}
 
void fw(int n, vector<vector<ll>>& distance) {
    for (int k=1; k<=n; k++) {
        for (int i=1; i<=n; i++) {
            for (int j=1; j<=n; j++) {
                if (distance[i][k] < INF && distance[k][j] < INF) distance[i][j]=min(distance[i][j], distance[i][k]+distance[k][j]);
            }
        }
    }
}
 
void bell(int n, vector<tuple<int, int, ll>>& edges, vector<ll>& distance){
    distance[1]=0;
    for (int i=1; i<=n-1; i++){
        for(auto e:edges){
        int a,b;
        ll w;
        tie(a,b,w)=e;
        if (distance[a]!=-INF) distance[b]=max(distance[b],distance[a]+w);
        }
    }
    for (int i=1; i<=n; i++){
        for(auto e:edges){
            int a,b;
            ll w;
            tie(a,b,w)=e;
            if (distance[a]!=-INF){
                if (distance[a]==INF || distance[a]+w>distance[b]) distance[b]=INF;
            }
        }
    }
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n,m;
    cin>>n>>m;
    string s;
    cin>>s;
    vector<vi> adj(n+1);
    while(m--){
        int a, b;
        cin>>a>>b;
        adj[a].PB(b);
    }
    vector<vi> dp(n+1, vi(26));
    vector<int> visited(n+1, 0);
    bool cycle=false;
    for(int i=1; i<=n; i++){
        if (visited[i]==0) {
            dfs(i, adj, dp, visited, cycle, s);
            if (cycle) {
                cout<<-1;
                return 0;
            }
        }
    }
    
    int ans=0;
    for (int i=1; i<=n; i++) {
        F(j, 26) ans=max(ans, dp[i][j]);
    }
    cout<<ans;
} 
```
