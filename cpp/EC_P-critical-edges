#include<bits/stdc++.h>
using namespace std;
#define pb push_back
 
int n; // number of nodes
vector<vector<int>> adj; // adjacency list of graph
 
vector<bool> visited;
vector<int> tin, low;
int timer;
vector<pair<int, int>> bridges;
 
void dfs(int v, int p = -1) {
    visited[v] = true;
    tin[v] = low[v] = timer++;
    for (int to : adj[v]) {
        if (to == p) continue;
        if (visited[to]) {
            low[v] = min(low[v], tin[to]);
        } else {
            dfs(to, v);
            low[v] = min(low[v], low[to]);
            if (low[to] > tin[v])
                bridges.push_back({v, to});
        }
    }
}
 
void find_bridges() {
    timer = 0;
    bridges.clear();
    visited.assign(n, false);
    tin.assign(n, -1);
    low.assign(n, -1);
    for (int i = 0; i < n; ++i) {
        if (!visited[i])
            dfs(i);
    }
}

bool cmp(pair<int, int> a, pair<int, int> b) {
	if(a.first == b.first) return a.second < b.second;
	return a.first < b.first;
}
 
 
void solve() {
	int m;
	cin >> n >> m;
	adj.resize(n+5);
	for(int i = 0; i < n+5; i += 1) adj[i].clear();
	for(int i = 0; i < m; i += 1) {
		int x, y;
		cin >> x >> y;
		x --, y --;
		if(x == y) continue;
		adj[x].pb(y), adj[y].pb(x);
	}
	find_bridges();
	
	int sz = bridges.size() ; 
	if(sz == 0) {cout << "Sin bloqueos\n"; return;}
	cout << sz << "\n";
	
	for(int i = 0; i < sz; i += 1) {
		if(bridges[i].first > bridges[i].second) {
			int temp = bridges[i].first;
			bridges[i].first = bridges[i].second, bridges[i].second = temp;
		}
	}
	sort(bridges.begin(), bridges.end(), cmp);
	for(int i = 0; i < sz; i += 1) {
		cout << bridges[i].first +1 << " " << bridges[i].second +1 << "\n";
	}
}
 
int main() {
	int t;
	cin >> t;
	for(int i = 1; i <= t; i += 1) 
		cout << "Caso #" << i << "\n", 
		solve();
	
	return 0;
} 
