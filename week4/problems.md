Counting Rooms
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
 
void dfs(int s, int m, vector<vector<int>>& adj, vector<vector<bool>>& visited) {
    if (visited[s/m][s%m]) return;
    visited[s/m][s%m]=true;
    for (auto u: adj[s]) dfs(u, m, adj, visited);
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vector<char>> a(n, vector<char>(m));
    vector<vi> adj(n*m);
    vector<vector<bool>> visited(n, vector<bool>(m, false));
    int ans=0;
    F(i, n){
        F(j, m){
            cin>>a[i][j];
            if (a[i][j]=='.') {
                if (i>0) if (a[i-1][j]=='.') {adj[m*i+j].PB(m*(i-1)+j); adj[m*(i-1)+j].PB(m*i+j);}
                if (j>0) if (a[i][j-1]=='.') {adj[m*i+j].PB(m*i+j-1); adj[m*(i)+j-1].PB(m*i+j);}
 
            }
        }
    }
    F(i, n*m) {
        if (a[i/m][i%m]=='.' && !(visited[i/m][i%m])) {
            ans++;
            dfs(i, m ,adj, visited);
        } 
    }
    cout<<ans;
    
}
```
Labyrinth
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
 
void dfs(int s, int m, vector<vector<int>>& adj, vector<vector<bool>>& visited) {
    if (visited[s/m][s%m]) return;
    visited[s/m][s%m]=true;
    for (auto u: adj[s]) dfs(u, m, adj, visited);
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vector<char>> a(n, vector<char>(m));
    vector<vi> p(n, vi(m));
    vector<vector<bool>> visited(n, vector<bool>(m, false));
    queue<pair<int ,int>> q;
    pair<int, int> A, B;
    string ans="";
    F(i, n){
        F(j, m){
            cin>>a[i][j];
            if (a[i][j]=='A') A={i, j};
            if (a[i][j]=='B') B={i, j};
        }
    }
    q.push(A);
    visited[A.first][A.second]=true;
    bool found=false;
    pair<int, int> moves[]={{-1, 0}, {1, 0}, {0, 1}, {0, -1}};
    char dir[]={'U', 'D', 'R', 'L'};
    while(!q.empty()){
        auto [c, d]=q.front();
        q.pop();
        if (c==B.first && d==B.second) {found=true; break;}
        F(i, 4){
            int e=c+moves[i].first, f=d+moves[i].second;
            if (e>=0 && e<n && f>=0 && f<m) {
                if (a[e][f]!='#' && !visited[e][f]) {
                    visited[e][f]=true;
                    p[e][f]=i;
                    q.push({e, f});
                }
                
            }
        }
    }
    if (!found) cout<<"NO\n";
    else {
        cout<<"YES\n";
        pair<int, int> curr=B;
        while(curr!=A){
            int d=p[curr.first][curr.second];
            ans+=dir[d];
            curr.first-=moves[d].first;
            curr.second-=moves[d].second;
        }
        reverse(ans.begin(), ans.end());
        cout<<ans.length()<<"\n"<<ans;
    }
    
}
```
Building Roads
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
 
void dfs(int s, vector<vector<int>>& adj, vector<bool>& visited) {
    if (visited[s]) return;
    visited[s]=true;
    for (auto u: adj[s]) dfs(u, adj, visited);
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vi> adj(n+1);
    F(i, m){
        int a,b;
        cin>>a>>b;
        adj[a].PB(b);
        adj[b].PB(a);
    }
    vector<bool> visited(n+1, false);
    int c=0;
    vector<int> f;
    for(int i=1; i<=n; i++){
        if (!visited[i]) {
            f.PB(i);
            dfs(i, adj, visited);
        }
    }
cout<<f.size()-1<<"\n";
    for(int i=0; i<f.size()-1; i++) {
        cout<<f[i]<<" "<<f[i+1]<<"\n";
    }
}
```
Message Route
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
const int INF=1e9;
 
void dfs(int s, vector<vector<int>>& adj, vector<bool>& visited) {
    if (visited[s]) return;
    visited[s]=true;
    for (auto u: adj[s]) dfs(u, adj, visited);
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
        cout<<distance[y]+1<<"\n";
        int curr=y;
        while(curr!=0) {
            path.PB(curr);
            curr=last[curr];
        }
        reverse(path.begin(), path.end());
        for (auto s: path) cout<<s<<" ";
    }
}
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vi> adj(n+1);
    vector<bool> visited(n+1, false);
    F(i, m){
        int a,b;
        cin>>a>>b;
        adj[a].PB(b);
        adj[b].PB(a);
    }
    bfs(1, n, n, adj, visited);
}
```
Building Roads
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
const int INF=1e9;
 
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
 
int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);
    int n, m;
    cin>>n>>m;
    vector<vi> adj(n+1);
    vector<int> visited(n+1, 0);
    F(i, m){
        int a,b;
        cin>>a>>b;
        adj[a].PB(b);
        adj[b].PB(a);
    }
    bool ans=true;
    for (int i=1; i<=n; i++) {
        if (visited[i]==0) {
            if (!dfs(i, 1, adj, visited)) {
                ans=false;
                break;
            }
        }
    }
    if (!ans) cout<<"IMPOSSIBLE\n";
    else {
        for (int i=1; i<=n; i++) {
            cout<<visited[i]<<" ";
        }
    }
}
```
