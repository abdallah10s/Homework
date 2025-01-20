// # Homework


	bool CheckNodeisConnected(int index)
	{
		Depth_first_Search_init();

		if (_NumberVertics <= 1) return true;

		dfs(index);
		if (dfs_counter - 1 != _NumberVertics)
			return false;

		LG=ReversEdge();

		Depth_first_Search_init();
		dfs(index);
		if (dfs_counter - 1 != _NumberVertics)
			return false;

		return true;


	}

	ListGraph ReversEdge() 
    {
		
	   ListGraph reversedGraph(_NumberVertics);

	 	for (int w = 0; w < _NumberVertics; ++w) {
			for (int s : LG[w])
			{
				reversedGraph[s].push_back(w); 
			}
		}
		return reversedGraph;
	}
       void dfs(int indexNode)
	{
		state[indexNode] = 1; // 1 -> active
		dfs_number[indexNode] = dfs_counter;
		dfs_counter++;

		for (int i = 0; i < _NumberVertics; i++)
		{
			if (LG[indexNode].at(i))
			{
				if (state[i] == 0)
					dfs(i);
			}
			state[indexNode] = 2;// 2 -> finiched
			finish_number[indexNode] = finish_counter;
			finish_counter++;

		}


  void dfs2(int indexNode)
  {
    state[indexNode] = 1; // 1 -> active
    dfs_number[indexNode] = dfs_counter;
    dfs_counter++;

    for (int i = 0; i < _NumberVertics; i++)
    {
      if (LG[indexNode].at(i))
      {
        if (state[i] == 0)
          dfs(i);
      }
      state[indexNode] = 2;// 2 -> finiched
      finish_number[indexNode] = finish_counter;
      finish_counter++;

    }
  }
	
