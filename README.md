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
std::vector<std::vector<int>> TrojanMap::all_segments(int N)
{
  int end;
  std::vector<std::vector<int>> res;
  for (int i = 0; i < N; i++)
  {
    for (int j = i + 2; j < N; j++)
    {
      if (i==0) end = N - 1;
      else end = N;
      
      for (int k = j + 2; k < end; k++)
      {
        res.push_back({i,j,k});
      }
    }
  }
  return res;
}

std::vector<std::string> TrojanMap::ThreeOptSwap(std::vector<int> segment, std::vector<std::string>& ids)
{
  int A = segment[0]; int B = segment[0]+1; int C = segment[1];
  int D = segment[1]+1; int E = segment[2]; int F = (segment[2]+1)%(ids.size());
  std::vector<double> dis(8);
  std::vector<std::string> res;
  dis[0] = CalculateDistance(ids[A],ids[B])+CalculateDistance(ids[C],ids[D])+CalculateDistance(ids[E],ids[F]);
  dis[1] = CalculateDistance(ids[E],ids[A])+CalculateDistance(ids[C],ids[D])+CalculateDistance(ids[F],ids[B]);
  dis[2] = CalculateDistance(ids[A],ids[C])+CalculateDistance(ids[D],ids[B])+CalculateDistance(ids[E],ids[F]);
  dis[3] = CalculateDistance(ids[A],ids[B])+CalculateDistance(ids[C],ids[E])+CalculateDistance(ids[D],ids[F]);
  dis[4] = CalculateDistance(ids[D],ids[A])+CalculateDistance(ids[C],ids[E])+CalculateDistance(ids[F],ids[B]);
  dis[5] = CalculateDistance(ids[A],ids[C])+CalculateDistance(ids[B],ids[E])+CalculateDistance(ids[D],ids[F]);
  dis[6] = CalculateDistance(ids[E],ids[A])+CalculateDistance(ids[B],ids[D])+CalculateDistance(ids[F],ids[C]);
  dis[7] = CalculateDistance(ids[D],ids[A])+CalculateDistance(ids[B],ids[E])+CalculateDistance(ids[F],ids[C]);

  auto min = std::min_element(dis.begin(), dis.end());
  int argmin = std::distance(dis.begin(), min);
  if (argmin == 0)
  {
    return res;
  }

  std::vector<std::string> firstsegment;
  if (F==0)
  {
    firstsegment.insert(firstsegment.end(),ids.begin(), ids.begin()+A+1);
  }
  else{
    firstsegment.insert(firstsegment.end(), ids.begin()+F,ids.end());
    firstsegment.insert(firstsegment.end(), ids.begin(),ids.begin()+A+1);
  }
  std::vector<std::string> secondsegment(ids.begin()+B,ids.begin()+C+1);
  std::vector<std::string> thirdsegment(ids.begin()+D,ids.begin()+E+1);
  switch (argmin)
  {
  case 1:
  {  
    std::reverse(firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 2:
  {
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    std::reverse(secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 3:
  {
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    std::reverse(thirdsegment.begin(), thirdsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 4:
  {
    std::reverse(firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    std::reverse(thirdsegment.begin(), thirdsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 5:
  {
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    std::reverse(secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    std::reverse(thirdsegment.begin(), thirdsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 6:
  {
    std::reverse(firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    std::reverse(secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  case 7:
  {
    std::reverse(firstsegment.begin(), firstsegment.end());
    res.insert(res.end(), firstsegment.begin(), firstsegment.end());
    std::reverse(secondsegment.begin(), secondsegment.end());
    res.insert(res.end(), secondsegment.begin(), secondsegment.end());
    std::reverse(thirdsegment.begin(), thirdsegment.end());
    res.insert(res.end(), thirdsegment.begin(), thirdsegment.end());
    return res;
  }
  }
}

std::vector<std::string> TrojanMap::correct_order(std::vector<std::string> ids, std::string source)
{
  auto it = std::find(ids.begin(), ids.end(), source);
  std::vector<std::string> res(it, ids.end());
  res.insert(res.end(), ids.begin(), it);
  return res;
}

std::pair<double, std::vector<std::vector<std::string>>> TrojanMap::TravellingTrojan_3opt(
    std::vector<std::string> location_ids)
{
  std::pair<double, std::vector<std::vector<std::string>>> records;
  if (location_ids.empty())
    return records;
  
  std::string source = location_ids[0];
  location_ids.push_back(source);
  records.first = CalculatePathLength(location_ids);
  records.second.push_back(location_ids);
  int unchanged = 0;

  std::vector<std::vector<int>> all_seg= all_segments(location_ids.size());

  while (unchanged < 5)
  {
    unchanged++;
    for (auto& s : all_seg)
    {
      std::vector<std::string> cur_ids = records.second.back();
      cur_ids.pop_back();
      std::vector<std::string> new_ids = ThreeOptSwap(s, cur_ids);
      if (new_ids.empty())
      {
        continue;
      }
      new_ids = correct_order(new_ids, source);
      new_ids.push_back(source);
      double new_distance = CalculatePathLength(new_ids);
      if (new_distance < records.first)
      {
        unchanged = 0;
        records.first = new_distance;
        records.second.push_back(new_ids);
        break;
      }
    }
  }
  return records;
}
```
