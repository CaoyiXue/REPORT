# REPORT

```c++
if (tmp.compare(0, name.length(), name) == 0)
```

```shell
**************************************************************
* 1. Autocomplete                                             
**************************************************************

Please input a partial location:lo
*************************Results******************************
Los Angeles & 11th
Los Angeles (University of Southern California)
Los Angeles & Olympic 1
Los Angeles & 12th 1
Los Angeles & Olympic
Los Angeles Central City Seventh-day Adventist Church
Los Angeles & 12th
Los Angeles & 11th 1
Los Angeles (University of Southern California) 1
Lotus Temple
**************************************************************
Time taken by function: 6 ms

```
```c++
int EDHelper(std::string& a, std::string& b, int m, int n);
int CalculateEditDistance_noDP(std::string a, std::string b);
std::string FindClosestName_noDP(std::string name);
```

```c++
int CalculateEditDistance(std::string, std::string);
std::string FindClosestName(std::string name);
```

```c++
std::vector<std::string> TrojanMap::CalculateShortestPath_Dijkstra(
    std::string location1_name, std::string location2_name)
{
  std::vector<std::string> res;
  std::string source = GetID(location1_name);
  std::string target = GetID(location2_name);
  std::priority_queue<std::pair<double, std::string>,
                    std::vector<std::pair<double, std::string>>,
                    std::greater<std::pair<double, std::string>>> q;
  std::map<std::string, double> distances;
  std::map<std::string, int> marks;
  std::map<std::string, std::string> pre;
```
```c++
          double alt = distances[u] + CalculateDistance(u, child);
          if (distances[child] > alt)
          {
            distances[child] = alt;
            q.push(std::make_pair(alt, child));
            pre[child] = u;
          }
         ```
