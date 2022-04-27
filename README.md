```c++
std::vector<std::string> TrojanMap::TwoOptSwap(int i, int k, std::vector<std::string> location_ids)
{
  std::reverse(location_ids.begin() + i, location_ids.begin() + k + 1);
  return location_ids;
}
```
```c++
cur_path.push_back(location_ids[i]);
TravellingTrojan_helper(i, cur_cost + CalculateDistance(location_ids[cur_node], 
                        location_ids[i]), cur_path, records, 
                        location_ids, isBacktracking);
cur_path.pop_back();
```
