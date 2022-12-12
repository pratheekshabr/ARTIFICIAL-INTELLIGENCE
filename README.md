# ARTIFICIAL-INTELLIGENCE
<h1><b>PART-A</b></h1><br>
<b>1.Write a program to implement Breadt First Search using Python</b><br>
graph ={<br>
    '1':['2','10'],<br>
    '2':['3','8'],<br>
    '3':['4'],<br>
    '4':['5','6','7'],<br>
    '5':[],<br>
    '6':[],<br>
    '7':[],<br>
    '8':['9'],<br>
    '9':[],<br>
    '10':[]<br>
}<br>
visited=[]<br>
queue=[]<br>
def bfs(visited,graph,node):<br>
    visited.append(node)<br>
    queue.append(node)<br>
    while queue:<br>
        m=queue.pop(0)<br>
        print(m,end=" ")<br>
        for neighbour in graph[m]:<br>
            if neighbour not in visited:<br>
                visited.append(neighbour)<br>
                queue.append(neighbour)<br>
print("Followig is the Breadth-First-Search")<br>
bfs(visited,graph,'1')<br>
<b><i>OUTPUT:</i><br>
Followig is the Breadth-First-Search<br>
1 2 10 3 8 4 9 5 6 7 </b><br><br>


<b>2.Write a program to implement Depth First Search using Python</b><br>
#Using a python ddictionary to act as an adjacency list<br>
graph={<br>
    '5':['3','7'],<br>
    '3':['2','4'],<br>
    '7':['6'],<br>
    '6':[],<br>
    '2':['1'],<br>
    '1':[],<br>
    '4':['8'],<br>
    '8':[]<br>
}<br>
visited=set()#Set to keep track of visited nodes of graph.<br>
def dfs(visited,graph,node):#function for dfs<br>
    if node not in visited:<br>
        print(node)<br>
        visited.add(node)<br>
        for neighbour in graph[node]:<br>
            dfs(visited,graph,neighbour)<br>
            
#Driver code<br>
print("Following is the Depth-First-Search")  <br> 
dfs(visited,graph,'5')<br>
<b><i>OUTPUT:</i></b>
   
