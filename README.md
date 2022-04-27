```c++
  while (unchanged < 10)
  {
    unchanged++;
    ....
    if(new path is small)
    {
        unchanged = 0
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
