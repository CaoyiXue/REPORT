```c++
    for (auto &node : predecessor)
    {
      for (auto &p : node.second)
      {
        if (distance[p] < infinite)
        {
          double asl = distance[p] + CalculateDistance(p, node.first);
          if (asl < distance[node.first])
          {
            distance[node.first] = asl;
            pre_path[node.first] = p;
          }
        }
      }
```
