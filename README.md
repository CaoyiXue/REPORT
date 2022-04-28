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
    for (int i = 0; i < size - 2; i++)
    {
      for (int k = i + 1; k < size - 1; k++)
      {
        std::vector<std::string> cur_ids = records.second.back();
        cur_ids.pop_back();
        std::vector<std::string> new_ids = TwoOptSwap(i, k, cur_ids);
        new_ids = correct_order(new_ids, source);
        new_ids.push_back(source);
        double new_distance = CalculatePathLength(new_ids);
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
