```c++
std::vector<std::vector<int>> all_segments(int N)
{
  int end;
  std::vector<std::vector<int>> res;
  for (int i = 1; i < N - 1; i++)
  {
    for (int j = i + 2; j < N - 3; j++)
    {
      if (i==1) end = N - 2;
      else end = N - 1;
      
      for (int k = j + 2; k < end; k++)
      {
        res.push_back({i,j,k});
      }
    }
  }
  return res;
}
```
```c++
cur_path.push_back(location_ids[i]);
TravellingTrojan_helper(i, cur_cost + CalculateDistance(location_ids[cur_node], 
                        location_ids[i]), cur_path, records, 
                        location_ids, isBacktracking);
cur_path.pop_back();
```
```c++
  while (unchanged < 60)
  {
    unchanged++;
    breakflag = false;
    for ....
    {
      for ....
      {
        ....
        if (new_distance < records.first)
        {
          unchanged = 0;
          records.first = new_distance;
          records.second.push_back(new_ids);
          breakflag = true;
          break;
        }
      }
      if (breakflag)
        break;
    }
  }
```
```c++
  while (unchanged < 60)
  {
    unchanged++;
    for (auto& s : all_seg)
    {
```

```c++
      if (marks[child_id] == 1 && child_id != parent_id)
      {
        end = current_id;
        start = child_id;
        return true;
      }
```
```c++
bool TrojanMap::CycleHelper(std::string current_id, std::map<std::string, int> &marks,
                            std::string parent_id, std::vector<double> &square,
                            std::map<std::string, std::string> &pre,
                            std::string &end, std::string &start)
```
```c++
  for (auto &loc : locations)
  {
    std::vector<std::string> tmp;
    AdjListDeliver[loc] = tmp;
  }
  for (auto &dep : dependencies)
  {
    AdjListDeliver[dep[0]].push_back(dep[1]);
  }
  // If has cycle in this map, return empty vector
  if (IsCycleDeliver())
  {
    return result;
  }

  for (auto &loc : locations)
  {
    if (marks[loc] != 1)
    {
      DeliverHelper(loc, marks, result);
    }
  }
```
