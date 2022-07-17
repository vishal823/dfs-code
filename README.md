# dfs-code
void dfs(int node, unordered_map<int,bool> &visit, unordered_map<int,list<int>> &adj , vector<int>  &element){
    //ans store
    element.push_back(node);
    //marking thats visited
    visit[node]=true;
    
    // recurcive call for every connected node
    for(auto i:adj[node]){
        if(!visit[i]){
          dfs(i,visit,adj ,element);
        }
}
}

vector<vector<int>> depthFirstSearch(int V, int E, vector<vector<int>> &edges)
{
    unordered_map<int,list<int> > adj;
    for(int i=0; i<edges.size(); i++){
        int u =edges[i][0];
        int v = edges[i][1];
         adj[u].push_back(v);
        adj[v].push_back(u);
        
    }
     vector<vector<int>> ans;
     unordered_map<int,bool> visit;
    // FOR ALL NODES DFS if not visited 
    for(int i=0;i<V;i++) {
        if(!visit[i]){
             vector<int> element;
             dfs(i,visit,adj,element);
             ans.push_back(element);
        }
       
    
    }
    return ans;
}
