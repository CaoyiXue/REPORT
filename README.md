```c++
double tmp = distance[target];
if (tmp != infinite && node.first == target && tmp == distance[target])
{
  count++;
}
}
if (count > 9)
{
  break;
}
```
```c++
cur_path.push_back(location_ids[i]);
TravellingTrojan_helper(i, cur_cost + CalculateDistance(location_ids[cur_node], 
                        location_ids[i]), cur_path, records, 
                        location_ids, isBacktracking);
cur_path.pop_back();
```
