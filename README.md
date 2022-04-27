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
