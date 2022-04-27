```c++
void TrojanMap::TravellingTrojan_helper(
    int cur_node, double cur_cost, std::vector<std::string> &cur_path,
    std::pair<double, std::vector<std::vector<std::string>>> &records,
    std::vector<std::string> &location_ids, bool &isBacktracking)
```
```c++
cur_path.push_back(location_ids[i]);
TravellingTrojan_helper(i, cur_cost + CalculateDistance(location_ids[cur_node], 
                        location_ids[i]), cur_path, records, 
                        location_ids, isBacktracking);
cur_path.pop_back();
```
