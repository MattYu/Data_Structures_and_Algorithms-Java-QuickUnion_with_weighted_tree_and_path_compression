# Data_Structures_and_Algorithms-Java-QuickUnion_with_weighted_tree_and_path_compression

Creates mathematical sets of N integers with M unions where M is a nonnegative integer <=N-1
	Used for modeling and solving scalable Percolation problems (electric conductivity, path flow, social media connections, etc.) in the most efficient mathematically optimized way.
	
	Has the following methods  
	- CreateSets(int N): create a set of N integers that are initially not linked. 
	  Runtime: O(M + Nlg*N) time (where lg* < 5 in practice; thus near linear)
	- Root(int a): determine the root of a. An element b and an element c are in the same set (joined by some union) iff Root(b) == Root(c)
	  Runtime: ~O(1)
	- Union(int a, int b): joins element a in set with element b
	  Runtime: O(logN) 
	Detail descriptions of the data structure and approach: 
	
	Weighted tree approach with path compression as described in Sedgewick and Al. Princeton University Press: 
	
	- Each object contains 2 arrays: id[] and size[]. 
	- Abstractly, id[] is used to represent the roots and children of a tree. If id[i] = i, then id[i] is a root. If id[i] is a children, id[i] = the index of its root in id[].
	- size[] keeps track of the number of elements a tree/set contains. 
	- When an object of class is initialized, all elements are initially unlinked. Thus id[i] is set initially to = i for all i in N. Likewise, size[i] = 1.
	- When Union is performed, the root of the smallest tree is linked to the root of the largest tree (larger = container more elements)
	- When Root(a) is performed, method returns the root of a AND compressed the tree if the height of the tree is greater than 2. This further improves runtime. 
	- More specialized methods (not included here) could be added to solve specific tailored percolation problems
	
	@ MTYU. COEN, Concordia University. 2017
