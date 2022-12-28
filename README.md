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
Move disk 1 from source A to destination B</b><br>
<b>6.
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



   
