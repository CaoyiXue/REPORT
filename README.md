## Step 1: Autocomplete the location name

```c++
std::vector<std::string> Autocomplete(std::string name);
```
### Description:
1. Traverse all nodes on the map.
2. If the size of input is greater than the size of node’s name, we skip this node.
3. Otherwise, convert input name and node's name to lower cases. 
4. Then, compare input name and substring of node name from the beginning which have same length.
5. If they are equal, push the node name into result vector.

### Examples:
1. chi ==> Chinese Street Food, Chick-fil-A, Chipotle.\
Time taken by function: 4 ms

2. w ==> Washington & Broadway 1, Washington & Hope, Washington & Union 2, Washington & Hoover, Washington & Bonnie Brae, Washington & Union, Washington & Cherry, Washington & Figueroa 1,Washington & Figueroa, Washington & Vermont, Washington & Budlong, Washington & Normandie, Washington & Harvard, Washington & Westmoreland, Washington & Mariposa, Western & Exposition, Western & 36th, Western & Adams 3, Western & Adams 2, Western & Adams, Western & 24th 1, Western & 10 Off-ramp 1, Western & Washington, Western & 10 Off-ramp, Washington & Western, Washington & Arlington, Workshop Salon & Boutique, Warning Skate Shop, Western & 24th, Western & Jefferson 1, Washington & Olive, Western & Adams 1, Western & 29th 1, Wadsworth Elementary School, Western & Exposition 1, West Vernon Elementary School, Washington & Gramercy, Western & 29th, Which Wich?
, Washington 1, Washington & Flower, Washington, Washington Boulevard School, Western & 36th 1, Western Avenue Christian Church, West Adams Presbyterian Church, Ward African Methodist Episcopal Church, Westvern Station Los Angeles Post Office, Westminster Presbyterian Church, Washington & Union 1, Washington & Oak, Washington & Grand 1, Walker Temple African Methodist Episcopal Church, Washington & Grand, Washington & Oak 1, Washington & New England, West Side Church of God, Washington & Broadway, Western & Jefferson, Washington & Bonsallo\
Time taken by function: 5 ms

3. s ==> Stimson House, Saint Cecilia School, Smoke Shop, Stout Burger, St Agnes Church, Security Checkpoint, Shall Gas, Social Security Administration, SunLife Organics, Student Union (STU),Starbucks 3, San Pedro Street 2, Starbucks 2, Safety Pole, San Julian & 12th, Starbucks 1, Spiritual Fellowship Church, Studio 423, Soles Bicycles, San Pedro Street 1, Starbucks, St. Philips Episcopal Church, St. Johns Cathedral-Hope Net, Saint Lukes Missionary Baptist Church, San Pedro Street, Subway, Saint Agnes Elementary School, Saint James Park, Shell, Subway 1, Saint Marks Lutheran Church, Santa Barbara Avenue School, Sonny Astani School of Civil Engineering, Strangers Rest Baptist Church, Saint Patrick School, Sweet illusion, Second Baptist Church, Senshin Buddhist Church, Saint Patricks Catholic Church, Servants of Mary Convent, Saint John Baptist Church, Saint Phillips Episcopal Church, Schoenfeld Symphonic Hall, Safety Pole 1, St. Francis Center - Food Bank\
Time taken by function: 5 ms

### Observation:
Different size of inputs need roughly the same time because we need to traverse all nodes in the data. Time complexity is O(n), n is number of nodes. When we type in longer name, running time will decrease a little because we can skip more nodes with shorter name.

## Step 2-1: Find the place's Coordinates in the Map

```c++
std::pair<double, double> GetPosition(std::string name);
```

### Description:
1. Traverse all nodes on the map.
2. If the name of input is equal to one node’s name, return this node latitude and longitude.

### Examples:
1. 
```shell
Please input a location:Hill & Adams
*************************Results******************************
Latitude: 34.0262 Longitude: -118.27
**************************************************************
Time taken by function: 5 ms
```
2. 
```shell
Please input a location:Central Adult Senior High
*************************Results******************************
Latitude: 34.0338 Longitude: -118.267
**************************************************************
Time taken by function: 5 ms
```
3. 
```shell
Please input a location:Expo/Western 1
*************************Results******************************
Latitude: 34.0184 Longitude: -118.31
**************************************************************
Time taken by function: 3 ms
```

### Observation:
Time complexity in worst case should be O(n) in which n is number of nodes. 

## Step 2-2: Check edit distance between two location names

```c++
int CalculateEditDistance(std::string a, std::string b);
```
### Description:
1. Create vector "res" with shape (a.length+1, b.length+1). Initialize the base case, for example:\
a.length = 3, b.length = 2;\
    [0,1,2,3,4]\
    [1,0,0,0,0]\
    [2,0,0,0,0]
2. From i = 1, j = 1, using following equation to update:\
    if the i-1th character of a == the j-1th character of b, res[i][j] = min(res[i-1][j], res[i][j-1], res[i-1][j-1])\
    if the i-1th character of a != the j-1th character of b, res[i][j] = min(res[i-1][j], res[i][j-1], res[i-1][j-1])+1
3. Finally, return bottom-right corner element of res, which is res[a.length()][b.length()]

### Observation:
Time complexity is O((a.length+1) * (b.length+1)) and Memory size is (a.length+1) * (b.length+1)

```c++
std::string FindClosestName(std::string name);
```
### Description:
1. Initilize "min" as INT_MAX, "tmp" as empty string. Traverse all nodes on the map. 
2. If EditDistance between input name and node's name is less than "min", update min to current EditDistance and update tmp to current node's name.
3. Finally, return the ClosestName "tmp"

### Examples:
1. 
```shell
Please input a location:Hill & 11
*************************Results******************************
No matched locations.
Did you mean Hill & 11th instead of Hill & 11? [y/n]y
Latitude: 34.04 Longitude: -118.26
**************************************************************
Time taken by function: 5 ms
```
2. 
```shell
Please input a location:KF
*************************Results******************************
No matched locations.
Did you mean KFC instead of KF? [y/n]y
Latitude: 34.0261 Longitude: -118.278
**************************************************************
Time taken by function: 3 ms
```
3. 
```shell
Please input a location:Rolphs
*************************Results******************************
No matched locations.
Did you mean Ralphs instead of Rolphs? [y/n]y
Latitude: 34.0318 Longitude: -118.291
**************************************************************
Time taken by function: 5 ms
```

### Observation:
Assume maximum length of node's name is L, the number of nodes is n. In worst case, the running time is L*n, so the time complexity is O(n). Therefore, the function time when we type in wrong name is roughtly same as the function time when we type in right name.

## Step 3: CalculateShortestPath between two places

```c++
std::vector<std::string> CalculateShortestPath_Dijkstra(std::string &location1_name,
                                               std::string &location2_name);
```
### Description:
```c++
std::vector<std::string> res; // store result of IDs
std::string source = GetID(location1_name); // get start node ID
std::string target = GetID(location2_name); // get end node ID
/* priority queue to update the minimum of distance, in the queue
std::pair<double, std::string> make sure it will compare double variable first
*/
std::priority_queue<std::pair<double, std::string>,
    std::vector<std::pair<double, std::string>>,
    std::greater<std::pair<double, std::string>>>q;
// mark being visited node as 1, mark already visited node as 2
std::map<std::string, int> marks;
// update previous node
std::map<std::string, std::string> pre;
```
```c++
// create the distance unordered_map for initial case when none node is visited 
double infinite = std::numeric_limits<double>::max();
std::unordered_map<std::string, double> distances;
for (auto &node : data)
{
    distances[node.first] = infinite;
}
distances[source] = 0.0;
```
```c++
q.push(std::make_pair(0.0, source));
while (!q.empty())
{
  std::string u = q.top().second;
  q.pop();//pop out the minimum of distance in the queue
  while (marks[u] == 2)
  {
 // let already visited nodes in the queue pop out if they are minimum
    u = q.top().second;
    q.pop();
  }
 // mark being visited node as 1
  marks[u] = 1;
  if (u == target)
  {
 //when end node is being visited stop loop
    break;
  }
  for (auto &child : data[u].neighbors)
  {// traverse neighbors of being visited node 
    if (marks[child] != 1 && marks[child] != 2)
    {// if neighbor node is unvisited, 
    // calculate new distance from being visited node to this neighbor node
      double alt = distances[u] + CalculateDistance(u, child);
      if (distances[child] > alt)
      {//compare the already stored distance with new distance
      // if new distance smaller, update distance and previous node of this neighbor node 
        distances[child] = alt;
        q.push(std::make_pair(alt, child));
        pre[child] = u;
      }
    }
  }
  //change being visited node to already visited node
  marks[u] = 2;
}
```
```c++
if (marks[target] == 1)
{//use pre map to backtrack the path from end node to start node
  res.push_back(target);
  while (target != source)
  {
    target = pre[target];
    res.push_back(target);
  }
  //reverse the result of IDs 
  std::reverse(res.begin(), res.end());
}
```
```c++
std::vector<std::string> CalculateShortestPath_Bellman_Ford(std::string &location1_name,
                                               std::string &location2_name);
```

**************************************************************
* 5. Cycle Detection                                          
**************************************************************

Please input the left bound longitude(between -118.320 and -118.250):-118.26
Please input the right bound longitude(between -118.320 and -118.250):-118.275
Please input the upper bound latitude(between 34.000 and 34.040):34.023
Please input the lower bound latitude(between 34.000 and 34.040):34.011
*************************Results******************************
there exist no cycle in the subgraph 
**************************************************************
Time taken by function: 0 ms

**************************************************************
* 5. Cycle Detection                                          
**************************************************************

Please input the left bound longitude(between -118.320 and -118.250):-118.275
Please input the right bound longitude(between -118.320 and -118.250):-118.26
Please input the upper bound latitude(between 34.000 and 34.040):34.023
Please input the lower bound latitude(between 34.000 and 34.040):34.011
*************************Results******************************
there exists a cycle in the subgraph 
**************************************************************
Time taken by function: 0 ms
