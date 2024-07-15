The sort-merge algorithm is an efficient way to merge 2 large datasets over a common key that is sortaable, unique, and can be assigned to or stored in the same partition. This means All rows within each dataset with the same key are hashed on the same partiton on the same executor.

This join type has 2 phases: a sort phase followed by a merge phase. The sort phase sorts each dataset by its desired join key; the merge phase iterates over each key in the row from each dataset and merges the rows if the 2 keys match.

By default, the _SortMergeJoin_ is enabled in parameter ==spark.sql.join.preferSortMergeJoin== . 

![[Shuffle Sort Merge Join.png]]




