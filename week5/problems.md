Shortest Routes I
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
 
void djs(int x, int n, vector<vector<pair<int, int>>>& adj, vector<bool>& visited){
    priority_queue<pair<ll, int>> q;
    vector<ll> distance(n+1, INF);
    distance[x]=0;
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; q.pop();
        if (visited[a]) continue;
        visited[a]=true;
        for (auto u: adj[a]) {
            int b=u.first, w=u.second;
            if (distance[a]+w<distance[b]) {
                distance[b]=distance[a]+w;
                q.push({-distance[b], b});
            }
        }
    }
    for(int i=1; i<=n; i++) cout<<distance[i]<<" ";
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vector<pair<int, int>>> adj(n+1);
    vector<bool> visited(n+1, false);
    F(i, m){
        int a,b,w;
        cin>>a>>b>>w;
        adj[a].PB({b, w});
    }
    djs(1, n, adj, visited);
}
```
Shortest Routes II
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
 
void djs(int x, int n, vector<vector<pair<int, int>>>& adj, vector<bool>& visited){
    priority_queue<pair<ll, int>> q;
    vector<ll> distance(n+1, INF);
    distance[x]=0;
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; q.pop();
        if (visited[a]) continue;
        visited[a]=true;
        for (auto u: adj[a]) {
            int b=u.first, w=u.second;
            if (distance[a]+w<distance[b]) {
                distance[b]=distance[a]+w;
                q.push({-distance[b], b});
            }
        }
    }
    for(int i=1; i<=n; i++) cout<<distance[i]<<" ";
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
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m, q;
    cin>>n>>m>>q;
    
    vector<vector<ll>> distance(n+1, vector<ll>(n+1, INF));
    for (int i=1; i<=n; i++) distance[i][i]=0;
 
    vector<bool> visited(n+1, false);
    F(i, m){
        int a,b;
        ll w;
        cin>>a>>b>>w;
        distance[a][b] = min(distance[a][b], w);
        distance[b][a] = min(distance[b][a], w);
    }
    fw(n, distance);
    while(q--){
        int a,b;
        cin>>a>>b;
        if (distance[a][b]!=INF) cout<<distance[a][b]<<"\n";
        else cout<<-1<<"\n";
    }
}
```
High Score
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
 
void djs(int x, int n, vector<vector<pair<int, int>>>& adj, vector<bool>& visited){
    priority_queue<pair<ll, int>> q;
    vector<ll> distance(n+1, INF);
    distance[x]=0;
    q.push({0, x});
    while (!q.empty()) {
        int a=q.top().second; q.pop();
        if (visited[a]) continue;
        visited[a]=true;
        for (auto u: adj[a]) {
            int b=u.first, w=u.second;
            if (distance[a]+w<distance[b]) {
                distance[b]=distance[a]+w;
                q.push({-distance[b], b});
            }
        }
    }
    for(int i=1; i<=n; i++) cout<<distance[i]<<" ";
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
    int n, m;
    cin>>n>>m;
    int a,b;
    ll w;
    vector<tuple<int, int, ll>> edges;
    while(m--){
        cin>>a>>b>>w;
        edges.PB({a, b, w});
    }
    vector<ll> distance(n+1, -INF);
    bell(n, edges, distance);
    if (distance[n]!=INF) cout<<distance[n];
    else cout<<-1;
}
```
Flight Discount
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
 
 
void djs(int x, int n, vector<vector<pair<int, ll>>>& adj, vector<vector<ll>>& distance){
    priority_queue<pair<ll, pair<int,int>>> q;
    vector<vector<bool>> visited(n+1, vector<bool>(2, false));
    distance[x][0]=0;
    q.push({0, {x, 0}});
    while (!q.empty()) {
        int a=q.top().second.first, used=q.top().second.second; q.pop();
        if (visited[a][used]) continue;
        visited[a][used]=true;
        for (auto u: adj[a]) {
            int b=u.first;
            ll w=u.second;
            if (used==0) {
                if (distance[a][0]+w<distance[b][0]) {
                    distance[b][0]=distance[a][0]+w;
                    q.push({-distance[b][0], {b, 0}});
                }
                if (distance[a][0]+(w/2)<distance[b][1]) {
                    distance[b][1]=distance[a][0]+(w/2);
                    q.push({-distance[b][1], {b, 1}});
                }
            }
            else {
                if (distance[a][1]+w<distance[b][1]) {
                    distance[b][1]=distance[a][1]+w;
                    q.push({-distance[b][1], {b, 1}});
                }
            }
        }
    }
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
    int n, m;
    cin>>n>>m;
    int a,b;
    ll w;
    vector<vector<pair<int, ll>>> adj(n+1);
    vector<vector<ll>> distance(n+1, vector<ll>(2, INF));
    while(m--){
        cin>>a>>b>>w;
        adj[a].PB({b, w});
    }
    djs(1, n, adj, distance);
    cout<<distance[n][1];
} 
```
Flight Routes
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
    int n, m, k;
    cin>>n>>m>>k;
    int a,b;
    ll w;
    vector<vector<pair<int, ll>>> adj(n+1);
    while(m--){
        cin>>a>>b>>w;
        adj[a].PB({b, w});
    }
    djs(1, n, k, adj);
} 
```
