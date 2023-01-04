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
#Using a python dictionary to act as an adjacency list<br>
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
<b><i>OUTPUT:</i></br>
Following is the Depth-First-Search<br>
5<br>
3<br>
2<br>
1<br>
4<br>
8<br>
7<br>
6<br></b><br>
<b>3.Write a program to implement Best First Search using python</b><br>
from queue import PriorityQueue<br>
import matplotlib.pyplot as plt<br>
import networkx as nx<br>

#for implementing BFS|returns path having lowest cost<br>
def best_first_search(source,target,n):<br>
    visited=[0]*n<br>
    visited[source]=True<br>
    pq=PriorityQueue()<br>
    pq.put((0,source))<br>
    while pq.empty()==False:<br>
        u=pq.get()[1]<br>
        print(u,end="")#the path having lowest cost<br>
        if u==target:<br>
            break<br>
        for v,c in graph[u]:<br>
            if visited[v]==False:<br>
                visited[v]=True<br>
                pq.put((c,v))<br>
            #print()<br>
          #for adding edges to graph<br>
def addedge(x,y,cost):<br>
    graph[x].append((y,cost))<br>
    graph[y].append((x,cost))<br>
v=int(input("Enter the number of nodes:"))<br>
graph=[[]for i in range(v)]#undirected graph<br>
e=int(input("enter the number of edges:"))<br>
print("enter the edges along with their weights:")<br>
for i in range(e):<br>
    x,y,z=list(map(int,input().split()))<br>
    addedge(x,y,z)<br>
source=int(input("Enter te source node:"))<br>
target=int(input("Enter the target/destination node"))<br>
print("\nPath:",end="")<br>
best_first_search(source,target,v) <br> 
<b><i>OUTPUT:</i><br>
Enter the number of nodes:4<br>
enter the number of edges:5<br>
enter the edges along with their weights:<br>
0 1  1<br>
0 2 1<br>
0 3 2<br>
2 3 2<br>
1 3 3<br>
Enter te source node:2<br>
Enter the target/destination node1<br>
Path:201</b><br><br>

<b>4.Write a program to implement Water-Jug problem using python.</b><br>
from collections import defaultdict<br>
jug1 ,jug2,aim=4,3,2<br>
visited=defaultdict(lambda:False)<br>
def waterJugSolver(amt1, amt2):<br>
    if(amt1==aim and amt2==0)or(amt2==aim and amt1==0):<br>
        print(amt1,amt2)<br>
        return True<br>
    if visited[(amt1,amt2)]==False:<br>
      print(amt1,amt2)<br>
      visited[(amt1,amt2)]=True<br>
      return(waterJugSolver(0,amt2)or<br>
        waterJugSolver(amt1,0)or<br>
        waterJugSolver(jug1,amt2)or<br>
        waterJugSolver(amt1,jug2)or<br>
        waterJugSolver(amt1+min(amt2,(jug1-amt1)),<br>
        amt2-min(amt2,(jug1-amt1)))or<br>
        waterJugSolver(amt1-min(amt1,(jug2-amt2)),<br>
        amt2=min(amt1,(jug2-amt2))))<br>
    else:<br>
        return False<br>
    
print("Steps:")<br>
waterJugSolver(0,0)<br>
<b><i>OUTPUT:</i><br>
Steps:<br>
0 0<br>
4 0<br>
4 3<br>
0 3<br>
3 0<br>
3 3<br>
4 2<br>
0 2<br>
True</b><br><br>
<b>5.Write a program to implement Tower of Hanoi using python</b><br>
def TowerOfHanoi(n,source,destination,auxiliary):<br>
    if n==1:<br>
        print("Move disk1 from source",source,"to destination",destination)<br>
        return<br>
    TowerOfHanoi(n-1,source,auxiliary,destination)<br>
    print("Move disk",n,"from source",source,"to destination",destination)<br>
    TowerOfHanoi(n-1,auxiliary,destination,source)<br>
n=3<br>
TowerOfHanoi(n,'A','B','C')<br>
<b><i>OUTPUT:</i><br>
Move disk 1 from source A to destination B<br>
Move disk 2 from source A to destination C<br>
Move disk 1 from source B to destination C<br>
Move disk 3 from source A to destination B<br>
Move disk 1 from source C to destination A<br>
Move disk 2 from source C to destination B<br>
Move disk 1 from source A to destination B</b><br><BR>

<b>6.Write a program to implement the FIND-S Algorithm for finding the  most specific hypothesis based on a given set of training data samples.  Read the training data from a .CSV file.</b><br>
import csv<br>
hypo=['%','%','%','%','%','%']<br>
with open('ws.csv') as csv_file:<br>
    readcsv=csv.reader(csv_file,delimiter=',')<br>
    data=[]<br>
    print("\n The given training examples are:")<br>
    for row in readcsv:<br>
        print(row)<br>
        if row[len(row)-1]=='Yes':<br><br>
            data.append(row)<br>
print("\n The positive examples are:")<br>
for x in data:<br>
    print(x)<br>
TotalExamples=len(data)<br>
i=0<br>
j=0<br>
k=0<br>
print("\n the steps of the find -s algorithm are\n",hypo)<br>
list=[]<br>
p=0<br>
d=len(data[p])-1<br>
for j in range(d):<br><br>
    list.append(data[i][j])<br>
hypo=list<br>
for i in range(1,TotalExamples):
    for k in range(d):<br>
        if hypo[k]!=data[i][k]:<br>
            hypo[k]='?'<br>
        else:<br>
             hypo[k]<br>
    print(hypo)<br>
print("\n The maximally specific Find-s hypothesis for the given training examples is");<br>
list=[]<br>
for i in range(d):<br>
    list.append(hypo[i])<br>
print(list)<br>
<b><i>OUTPUT:</i><BR>
 The given training examples are:<BR><br>
['Sunny', 'Warm', 'Normal', 'Strong', 'Warm', 'Same', 'Yes']<BR><br>
['Sunny', 'Warm', 'High', 'Strong', 'Warm', 'Same', 'Yes']<BR><br>
['Rainy', 'Cold', 'High', 'Strong', 'Warm', 'Change', 'No']<BR><br>
['Sunny', 'Warm', 'High', 'Strong', 'Cool', 'Change', 'Yes']<BR><br>

 The positive examples are:<BR><br>
['Sunny', 'Warm', 'Normal', 'Strong', 'Warm', 'Same', 'Yes']<BR><br>
['Sunny', 'Warm', 'High', 'Strong', 'Warm', 'Same', 'Yes']<BR><br>
['Sunny', 'Warm', 'High', 'Strong', 'Cool', 'Change', 'Yes']<BR><br>

 the steps of the find -s algorithm are<BR><br>
 ['%', '%', '%', '%', '%', '%']<br>
['Sunny', 'Warm', '?', 'Strong', 'Warm', 'Same']<br>
['Sunny', 'Warm', '?', 'Strong', '?', '?']<br>

 The maximally specific Find-s hypothesis for the given training examples is<br>
 ['Sunny', 'Warm', '?', 'Strong', '?', '?']</b><br><br>
<b>7. Write a Program to Implement N-Queens Problem using Python. </b><br>
global N<br>
N = 4<br>
def printSolution(board):<br>
    for i in range(N):<br>
        for j in range(N):<br>
            print (board[i][j], end = " ")<br>
        print()<br>

def isSafe(board, row, col):<br>
    for i in range(col):<br>
        if board[row][i] == 1:<br>
            return False<br>

    for i, j in zip(range(row, -1, -1),range(col, -1, -1)):<br>
        if board[i][j] == 1:<br>
            return False<br>

    for i, j in zip(range(row, N, 1),range(col, -1, -1)):<br>
        if board[i][j] == 1:<br>
            return False<br>
    return True<br>

def solveNQUtil(board, col):<br>
    if col >= N:<br>
        return True<br>
    for i in range(N):<br>
        if isSafe(board, i, col):<br>
            board[i][col] = 1<br>
            if solveNQUtil(board, col + 1) == True:<br>
                return True<br>
            board[i][col] = 0<br>
    return False<br>

def solveNQ():<br>
    board = [ [0, 0, 0, 0],<br>
             [0, 0, 0, 0],<br>
             [0, 0, 0, 0],<br>
             [0, 0, 0, 0] ]<br>
    if solveNQUtil(board, 0) == False:<br>
        print ("Solution does not exist")<br>
        return False<br>
    printSolution(board)<br>
    return True<br>
solveNQ()<br>
<b><i>OUTPUT:</i><br>
    0 0 1 0 <br>
1 0 0 0 <br>
0 0 0 1 <br>
0 1 0 0 <br>
True<b><br><br>
 <b>8.</b>
     def aStarAlgo(start_node, stop_node):<br>
    open_set = set(start_node)<br>
    closed_set = set()<br>
    g = {}     <br>          #store distance from starting node<br>
    parents = {}  <br>       # parents contains an adjacency map of all nodes<br>
    #distance of starting node from itself is zero<br>
    g[start_node] = 0<br>
    #start_node is root node i.e it has no parent nodes<br>
    #so start_node is set to its own parent node<br>
    parents[start_node] = start_node<br>
    while len(open_set) > 0:<br>
        n = None
        #node with lowest f() is found<br>
        for v in open_set:<br><br>
            if n == None or g[v] + heuristic(v) < g[n] + heuristic(n):<br>
                n = v<br>
        if n == stop_node or Graph_nodes[n] == None:<br>
            pass<br>
        else:<br>
            for (m, weight) in get_neighbors(n):<br>
                #nodes 'm' not in first and last set are added to first<br>
                #n is set its parent<br>
                if m not in open_set and m not in closed_set:<br>
                    open_set.add(m)<br>
                    parents[m] = n<br>
                    g[m] = g[n] + weight<br><br>
                #for each node m,compare its distance from start i.e g(m) to the<br>
                #from start through n node<br>
                else:<br>
                    if g[m] > g[n] + weight:<br>
                        #update g(m)<br>
                        g[m] = g[n] + weight<br>
                        #change parent of m to n<br>
                        parents[m] = n<br>
                        #if m in closed set,remove and add to open<br>
                        if m in closed_set:<br>
                            closed_set.remove(m)<br>
                            open_set.add(m)<br>
        if n == None:<br>
            print('Path does not exist!')<br>
            return None<br>
        
        # if the current node is the stop_node<br>
        # then we begin reconstructin the path from it to the start_node<br>
        if n == stop_node:<br>
            path = []<br>
            while parents[n] != n:<br>
                path.append(n)<br>
                n = parents[n]<br>
            path.append(start_node)<br>
            path.reverse()<br>
            print('Path found: {}'.format(path))<br>
            return path<br>
        # remove n from the open_list, and add it to closed_list<br>
        # because all of his neighbors were inspected<br>
        open_set.remove(n)<br>
        closed_set.add(n)<br>
    print('Path does not exist!')<br>
    return None<br>

#define fuction to return neighbor and its distance<br>
#from the passed node<br>
def get_neighbors(v):<br>
    if v in Graph_nodes:<br>
        return Graph_nodes[v]<br>
    else:<br>
        return None<br>
#for simplicity we ll consider heuristic distances given<br>
#and this function returns heuristic distance for all nodes<br>
def heuristic(n):<br>
    H_dist = {<br>
        'A': 11,<br>
        'B': 6,<br><br>
        'C': 5,<br>
        'D': 7,<br>
        'E': 3,<br>
        'F': 6,<br>
        'G': 5,<br>
        'H': 3,<br>
        'I': 1,<br>
        'J': 0<br>
    }<br>
    return H_dist[n]<br>

#Describe your graph here<br>
Graph_nodes = {<br>
    'A': [('B', 6), ('F', 3)],<br>
    'B': [('A', 6), ('C', 3), ('D', 2)],<br>
    'C': [('B', 3), ('D', 1), ('E', 5)],<br>
    'D': [('B', 2), ('C', 1), ('E', 8)],<br>
    'E': [('C', 5), ('D', 8), ('I', 5), ('J', 5)],<br>
    'F': [('A', 3), ('G', 1), ('H', 7)],<br>
    'G': [('F', 1), ('I', 3)],<br>
    'H': [('F', 7), ('I', 2)],<br>
    'I': [('E', 5), ('G', 3), ('H', 2), ('J', 3)],<br>
}

aStarAlgo('A', 'J')<br>
<b><i>OUTPUT:</i><br>
Path found: ['A', 'F', 'G', 'I', 'J']<br>
['A', 'F', 'G', 'I', 'J']<br><br>


 
  
