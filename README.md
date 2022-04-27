```c++
    for (int i = 1; i < size - 2; i++)
    {
      for (int k = i + 1; k < size - 1; k++)
      {
        .....
      }
    }
```
```c++
cur_path.push_back(location_ids[i]);
TravellingTrojan_helper(i, cur_cost + CalculateDistance(location_ids[cur_node], 
                        location_ids[i]), cur_path, records, 
                        location_ids, isBacktracking);
cur_path.pop_back();
```
