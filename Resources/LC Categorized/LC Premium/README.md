# LeetCode Premium Problems - Categorized by Topic

> **Total Problems**: 300+  
> **Last Updated**: 2025-01-27

---

## Table of Contents

- [Dynamic Programming](#dynamic-programming)
- [Graph](#graph)
- [Tree](#tree)
- [String](#string)
- [Array & Matrix](#array--matrix)
- [Design](#design)
- [Two Pointers & Sliding Window](#two-pointers--sliding-window)
- [Binary Search](#binary-search)
- [Greedy](#greedy)
- [Backtracking](#backtracking)
- [Math & Geometry](#math--geometry)
- [Database](#database)
- [Other](#other)

---

## Dynamic Programming

### Basic DP
- **256. Paint House** (64.0% | Med.) - Classic DP with 3 states
- **265. Paint House II** (56.7% | Hard) - DP with k colors, optimization
- **276. Paint Fence** (48.1% | Med.) - DP with constraints

### Interval DP
- **471. Encode String with Shortest Length** (50.5% | Hard) - String compression with DP

### Tree DP
- **250. Count Univalue Subtrees** (57.4% | Med.) - Count subtrees with same value
- **298. Binary Tree Longest Consecutive Sequence** (54.3% | Med.) - Longest consecutive path in tree
- **333. Largest BST Subtree** (45.7% | Med.) - Find largest BST in tree
- **549. Binary Tree Longest Consecutive Sequence II** (49.6% | Med.) - Extension with up/down paths
- **1973. Count Nodes Equal to Sum of Descendants** (77.2% | Med.) - Tree DP with sum calculation

### Grid DP
- **562. Longest Line of Consecutive One in Matrix** (50.5% | Med.) - DP in 4 directions
- **568. Maximum Vacation Days** (46.6% | Hard) - DP with state transitions
- **1102. Path With Maximum Minimum Value** (54.4% | Med.) - Path optimization DP
- **2371. Minimize Maximum Value in a Grid** (70.4% | Hard) - Grid DP optimization

### State DP / Bitmask
- **351. Android Unlock Patterns** (53.5% | Med.) - Pattern counting with constraints
- **465. Optimal Account Balancing** (50.1% | Hard) - State DP for balancing

### Linear DP
- **259. 3Sum Smaller** (51.2% | Med.) - DP-like counting
- **325. Maximum Size Subarray Sum Equals k** (50.7% | Med.) - Subarray DP
- **487. Max Consecutive Ones II** (51.8% | Med.) - DP with one flip
- **651. 4 Keys Keyboard** (55.9% | Med.) - DP optimization problem
- **656. Coin Path** (34.1% | Hard) - DP with path reconstruction
- **644. Maximum Average Subarray II** (37.6% | Hard) - DP with binary search
- **1918. Kth Smallest Subarray Sum** (52.8% | Med.) - DP with binary search
- **2702. Minimum Operations to Make Numbers Non-positive** (43.2% | Hard) - DP optimization

### String DP
- **1216. Valid Palindrome III** (49.1% | Hard) - DP on strings
- **1062. Longest Repeating Substring** (63.3% | Med.) - DP/LCS variant
- **1153. String Transforms Into Another String** (34.7% | Hard) - String transformation DP
- **1554. Strings Differ by One Character** (40.6% | Med.) - String comparison DP
- **1698. Number of Distinct Substrings in a String** (64.6% | Med.) - DP with trie
- **1858. Longest Word With All Prefixes** (71.9% | Med.) - DP with trie
- **1794. Count Pairs of Equal Substrings With Minimum Difference** (64.0% | Med.) - String DP
- **2955. Number of Same-End Substrings** (61.5% | Med.) - String DP

### Game Theory DP
- **294. Flip Game II** (52.2% | Med.) - Game theory with DP

---

## Graph

### Graph Traversal (DFS/BFS)
- **261. Graph Valid Tree** (49.6% | Med.) - Validate tree structure
- **286. Walls and Gates** (63.4% | Med.) - BFS from multiple sources
- **305. Number of Islands II** (40.3% | Hard) - Dynamic connectivity with BFS
- **317. Shortest Distance from All Buildings** (44.7% | Hard) - Multi-source BFS
- **323. Number of Connected Components in an Undirected Graph** (64.6% | Med.) - DFS/BFS traversal
- **490. The Maze** (59.9% | Med.) - BFS in grid with obstacles
- **505. The Maze II** (54.5% | Med.) - BFS with shortest path
- **499. The Maze III** (51.1% | Hard) - BFS with path reconstruction
- **489. Robot Room Cleaner** (77.8% | Hard) - DFS with backtracking
- **694. Number of Distinct Islands** (62.6% | Med.) - DFS with shape encoding
- **711. Number of Distinct Islands II** (55.2% | Hard) - DFS with rotation/reflection
- **742. Closest Leaf in a Binary Tree** (47.3% | Med.) - BFS from node to leaf
- **1059. All Paths from Source Lead to Destination** (37.0% | Med.) - DFS path validation
- **1101. The Earliest Moment When Everyone Become Friends** (65.7% | Med.) - Union-Find/BFS
- **1136. Parallel Courses** (61.9% | Med.) - Topological sort / BFS
- **1197. Minimum Knight Moves** (41.6% | Med.) - BFS on chessboard
- **1241. Number of Comments per Post** (65.8% | Easy) - Tree traversal
- **1242. Web Crawler Multithreaded** (50.6% | Med.) - Concurrent BFS
- **1245. Tree Diameter** (61.2% | Med.) - BFS/DFS for diameter
- **1257. Smallest Common Region** (68.2% | Med.) - LCA in tree
- **1258. Synonymous Sentences** (56.9% | Med.) - Graph with DFS
- **1522. Diameter of N-Ary Tree** (75.4% | Med.) - Tree diameter
- **1548. The Most Similar Path in a Graph** (59.3% | Hard) - Graph path matching
- **1644. Lowest Common Ancestor of a Binary Tree II** (69.2% | Med.) - LCA variant
- **1650. Lowest Common Ancestor of a Binary Tree III** (82.8% | Med.) - LCA with parent pointers
- **1676. Lowest Common Ancestor of a Binary Tree IV** (79.4% | Med.) - LCA for multiple nodes
- **1724. Checking Existence of Edge Length Limited Paths II** (51.7% | Hard) - Graph connectivity
- **1730. Shortest Path to Get Food** (57.0% | Med.) - BFS shortest path
- **1778. Shortest Path in a Hidden Grid** (44.3% | Med.) - BFS with exploration
- **1810. Minimum Path Cost in a Hidden Grid** (58.5% | Med.) - BFS with costs
- **1820. Maximum Number of Accepted Invitations** (51.9% | Med.) - Bipartite matching
- **2077. Paths in Maze That Lead to Same Room** (56.2% | Med.) - Graph paths
- **2277. Closest Node to Path in Tree** (62.2% | Hard) - Tree path queries
- **2307. Check for Contradictions in Equations** (43.7% | Hard) - Graph with contradictions
- **2510. Check if There is a Path With Equal Number of 0's And 1's** (51.6% | Med.) - Graph with constraints

### Topological Sort
- **269. Alien Dictionary** (36.9% | Hard) - Topological sort for ordering
- **444. Sequence Reconstruction** (29.9% | Med.) - Topological sort validation

### Union-Find / DSU
- **1101. The Earliest Moment When Everyone Become Friends** (65.7% | Med.) - Union-Find application
- **1168. Optimize Water Distribution in a Village** (65.3% | Hard) - MST with Union-Find

### Minimum Spanning Tree
- **1168. Optimize Water Distribution in a Village** (65.3% | Hard) - MST problem

### Shortest Path
- **317. Shortest Distance from All Buildings** (44.7% | Hard) - Multi-source shortest path
- **505. The Maze II** (54.5% | Med.) - Shortest path in grid
- **499. The Maze III** (51.1% | Hard) - Shortest path with lexicographic order
- **1197. Minimum Knight Moves** (41.6% | Med.) - Shortest path on chessboard
- **1730. Shortest Path to Get Food** (57.0% | Med.) - BFS shortest path

---

## Tree

### Binary Tree
- **156. Binary Tree Upside Down** (65.0% | Med.) - Tree transformation
- **250. Count Univalue Subtrees** (57.4% | Med.) - Tree traversal with counting
- **270. Closest Binary Search Tree Value** (49.4% | Easy) - BST search
- **272. Closest Binary Search Tree Value II** (60.9% | Hard) - BST k closest values
- **285. Inorder Successor in BST** (51.0% | Med.) - BST successor
- **298. Binary Tree Longest Consecutive Sequence** (54.3% | Med.) - Tree path tracking
- **314. Binary Tree Vertical Order Traversal** (57.6% | Med.) - Tree with column tracking
- **333. Largest BST Subtree** (45.7% | Med.) - BST validation in tree
- **366. Find Leaves of Binary Tree** (81.2% | Med.) - Tree level extraction
- **426. Convert Binary Search Tree to Sorted Doubly Linked List** (65.6% | Med.) - Tree to list conversion
- **510. Inorder Successor in BST II** (61.1% | Med.) - BST successor with parent
- **536. Construct Binary Tree from String** (58.6% | Med.) - Tree construction
- **545. Boundary of Binary Tree** (47.6% | Med.) - Tree boundary traversal
- **549. Binary Tree Longest Consecutive Sequence II** (49.6% | Med.) - Tree path with up/down
- **742. Closest Leaf in a Binary Tree** (47.3% | Med.) - Tree leaf finding
- **776. Split BST** (82.3% | Med.) - BST splitting
- **1586. Binary Search Tree Iterator II** (63.4% | Med.) - BST iterator with prev/next
- **1602. Find Nearest Right Node in Binary Tree** (75.0% | Med.) - Tree level traversal
- **1612. Check If Two Expression Trees are Equivalent** (71.5% | Med.) - Tree comparison
- **1644. Lowest Common Ancestor of a Binary Tree II** (69.2% | Med.) - LCA variant
- **1650. Lowest Common Ancestor of a Binary Tree III** (82.8% | Med.) - LCA with parent
- **1660. Correct a Binary Tree** (74.2% | Med.) - Tree correction
- **1666. Change the Root of a Binary Tree** (75.0% | Med.) - Tree root change
- **1676. Lowest Common Ancestor of a Binary Tree IV** (79.4% | Med.) - LCA for multiple nodes
- **1973. Count Nodes Equal to Sum of Descendants** (77.2% | Med.) - Tree sum calculation
- **2313. Minimum Flips in Binary Tree to Get Result** (56.5% | Hard) - Tree with operations
- **2689. Extract Kth Character From The Rope Tree** (73.8% | Easy) - Rope tree structure
- **3054. Binary Tree Nodes** (78.6% | Med.) - Tree node queries

### N-ary Tree
- **428. Serialize and Deserialize N-ary Tree** (68.4% | Hard) - N-ary tree serialization
- **1506. Find Root of N-Ary Tree** (78.5% | Med.) - Find root in N-ary tree
- **1516. Move Sub-Tree of N-Ary Tree** (59.5% | Hard) - N-ary tree manipulation
- **1522. Diameter of N-Ary Tree** (75.4% | Med.) - N-ary tree diameter
- **1485. Clone Binary Tree With Random Pointer** (80.9% | Med.) - Tree cloning

### Tree Construction
- **536. Construct Binary Tree from String** (58.6% | Med.) - String to tree

---

## String

### String Processing
- **157. Read N Characters Given Read4** (42.4% | Easy) - String reading
- **158. Read N Characters Given read4 II - Call Multiple Times** (43.1% | Hard) - String reading with state
- **159. Longest Substring with At Most Two Distinct Characters** (56.8% | Med.) - Sliding window
- **186. Reverse Words in a String II** (56.4% | Med.) - String reversal
- **243. Shortest Word Distance** (66.1% | Easy) - String distance
- **244. Shortest Word Distance II** (62.5% | Med.) - String distance with caching
- **245. Shortest Word Distance III** (59.3% | Med.) - String distance variant
- **246. Strobogrammatic Number** (47.6% | Easy) - Number pattern matching
- **247. Strobogrammatic Number II** (53.4% | Med.) - Generate strobogrammatic numbers
- **249. Group Shifted Strings** (67.6% | Med.) - String grouping
- **266. Palindrome Permutation** (68.6% | Easy) - Palindrome check
- **267. Palindrome Permutation II** (42.2% | Med.) - Generate palindrome permutations
- **271. Encode and Decode Strings** (50.6% | Med.) - String encoding
- **288. Unique Word Abbreviation** (27.3% | Med.) - String abbreviation
- **291. Word Pattern II** (48.7% | Med.) - Pattern matching
- **293. Flip Game** (65.0% | Easy) - String manipulation
- **340. Longest Substring with At Most K Distinct Characters** (49.7% | Med.) - Sliding window
- **408. Valid Word Abbreviation** (37.0% | Easy) - Abbreviation validation
- **411. Minimum Unique Word Abbreviation** (40.3% | Hard) - Abbreviation optimization
- **418. Sentence Screen Fitting** (36.4% | Med.) - String fitting
- **422. Valid Word Square** (42.2% | Easy) - String matrix validation
- **425. Word Squares** (54.5% | Hard) - String matrix construction
- **484. Find Permutation** (66.9% | Med.) - String to permutation
- **527. Word Abbreviation** (62.5% | Hard) - Abbreviation generation
- **616. Add Bold Tag in String** (51.3% | Med.) - String formatting
- **734. Sentence Similarity** (44.7% | Easy) - Sentence comparison
- **737. Sentence Similarity II** (50.9% | Med.) - Sentence similarity with transitivity
- **758. Bold Words in String** (52.4% | Med.) - String formatting
- **800. Similar RGB Color** (67.9% | Easy) - Color string matching
- **1055. Shortest Way to Form String** (61.4% | Med.) - String subsequence
- **1056. Confusing Number** (49.3% | Easy) - Number string validation
- **1062. Longest Repeating Substring** (63.3% | Med.) - Longest repeating substring
- **1087. Brace Expansion** (66.7% | Med.) - String expansion
- **1088. Confusing Number II** (47.1% | Hard) - Number generation with constraints
- **1153. String Transforms Into Another String** (34.7% | Hard) - String transformation
- **1165. Single-Row Keyboard** (87.7% | Easy) - Keyboard string distance
- **1554. Strings Differ by One Character** (40.6% | Med.) - String comparison
- **1698. Number of Distinct Substrings in a String** (64.6% | Med.) - Distinct substrings
- **1858. Longest Word With All Prefixes** (71.9% | Med.) - String with prefixes
- **1794. Count Pairs of Equal Substrings With Minimum Difference** (64.0% | Med.) - Substring pairs
- **2955. Number of Same-End Substrings** (61.5% | Med.) - Substring counting

### String Matching / Pattern
- **291. Word Pattern II** (48.7% | Med.) - Pattern matching with backtracking
- **3022. Find Pattern in Infinite Stream I** (56.7% | Med.) - Pattern matching in stream
- **3037. Find Pattern in Infinite Stream II** (66.9% | Hard) - Advanced pattern matching

---

## Array & Matrix

### Array Manipulation
- **163. Missing Ranges** (35.5% | Easy) - Range finding
- **280. Wiggle Sort** (68.4% | Med.) - Array sorting variant
- **360. Sort Transformed Array** (57.5% | Med.) - Array transformation and sort
- **370. Range Addition** (72.6% | Med.) - Range updates
- **487. Max Consecutive Ones II** (51.8% | Med.) - Array with one flip
- **1060. Missing Element in Sorted Array** (59.5% | Med.) - Binary search in array
- **1213. Intersection of Three Sorted Arrays** (80.0% | Easy) - Array intersection
- **1229. Meeting Scheduler** (55.2% | Med.) - Interval scheduling
- **1272. Remove Interval** (67.0% | Med.) - Interval removal
- **1708. Largest Subarray Length K** (65.5% | Easy) - Subarray finding
- **1874. Minimize Product Sum of Two Arrays** (89.1% | Med.) - Array optimization
- **1966. Binary Searchable Numbers in an Unsorted Array** (62.5% | Med.) - Array property
- **2031. Count Subarrays With More Ones Than Zeros** (49.2% | Med.) - Subarray counting
- **2128. Remove All Ones With Row and Column Flips** (76.2% | Med.) - Matrix manipulation
- **2174. Remove All Ones With Row and Column Flips II** (67.1% | Med.) - Matrix variant
- **2237. Count Positions on Street With Required Brightness** (62.6% | Med.) - Array with ranges
- **2263. Make Array Non-decreasing or Non-increasing** (65.5% | Hard) - Array transformation
- **2459. Sort Array by Moving Items to Empty Space** (45.3% | Hard) - Array sorting with constraints
- **2863. Maximum Length of Semi-Decreasing Subarrays** (70.0% | Med.) - Subarray property
- **2936. Number of Equal Numbers Blocks** (62.3% | Med.) - Array blocks
- **2964. Number of Divisible Triplet Sums** (67.5% | Med.) - Array combinatorics

### Matrix Problems
- **302. Smallest Rectangle Enclosing Black Pixels** (60.7% | Hard) - Matrix search
- **308. Range Sum Query 2D - Mutable** (45.2% | Med.) - 2D range queries
- **311. Sparse Matrix Multiplication** (69.1% | Med.) - Matrix multiplication
- **361. Bomb Enemy** (52.7% | Med.) - Matrix traversal
- **531. Lonely Pixel I** (62.6% | Med.) - Matrix pattern finding
- **533. Lonely Pixel II** (48.8% | Med.) - Matrix pattern variant
- **562. Longest Line of Consecutive One in Matrix** (50.5% | Med.) - Matrix DP
- **568. Maximum Vacation Days** (46.6% | Hard) - Matrix DP
- **750. Number Of Corner Rectangles** (67.9% | Med.) - Matrix counting
- **1102. Path With Maximum Minimum Value** (54.4% | Med.) - Matrix path
- **1428. Leftmost Column with at Least a One** (55.0% | Med.) - Matrix search
- **2282. Number of People That Can Be Seen in a Grid** (47.5% | Med.) - Matrix visibility
- **2371. Minimize Maximum Value in a Grid** (70.4% | Hard) - Matrix optimization

### Sliding Window / Two Pointers
- **159. Longest Substring with At Most Two Distinct Characters** (56.8% | Med.) - Sliding window
- **340. Longest Substring with At Most K Distinct Characters** (49.7% | Med.) - Sliding window
- **487. Max Consecutive Ones II** (51.8% | Med.) - Sliding window with flip

---

## Design

### Data Structure Design
- **170. Two Sum III - Data structure design** (39.0% | Easy) - Hash table design
- **251. Flatten 2D Vector** (50.4% | Med.) - Iterator design
- **281. Zigzag Iterator** (66.3% | Med.) - Iterator design
- **346. Moving Average from Data Stream** (80.1% | Easy) - Stream processing
- **348. Design Tic-Tac-Toe** (58.7% | Med.) - Game design
- **353. Design Snake Game** (39.9% | Med.) - Game design
- **359. Logger Rate Limiter** (76.7% | Easy) - Rate limiter design
- **362. Design Hit Counter** (69.4% | Med.) - Counter design
- **379. Design Phone Directory** (52.6% | Med.) - Directory design
- **604. Design Compressed String Iterator** (40.2% | Easy) - Iterator design
- **631. Design Excel Sum Formula** (40.4% | Hard) - Spreadsheet design
- **635. Design Log Storage System** (59.2% | Med.) - Log system design
- **642. Design Search Autocomplete System** (49.6% | Hard) - Autocomplete design
- **716. Max Stack** (45.7% | Hard) - Stack design
- **1166. Design File System** (65.0% | Med.) - File system design
- **1188. Design Bounded Blocking Queue** (73.3% | Med.) - Thread-safe queue
- **1586. Binary Search Tree Iterator II** (63.4% | Med.) - BST iterator
- **1756. Design Most Recently Used Queue** (77.7% | Med.) - MRU queue design
- **2254. Design Video Sharing Platform** (63.7% | Hard) - Platform design
- **2633. Convert Object to JSON String** (77.9% | Med.) - JSON serialization
- **2636. Promise Pool** (79.5% | Med.) - Promise concurrency control

### System Design
- **642. Design Search Autocomplete System** (49.6% | Hard) - Autocomplete system
- **2254. Design Video Sharing Platform** (63.7% | Hard) - Video platform

---

## Two Pointers & Sliding Window

- **159. Longest Substring with At Most Two Distinct Characters** (56.8% | Med.) - Sliding window
- **340. Longest Substring with At Most K Distinct Characters** (49.7% | Med.) - Sliding window
- **487. Max Consecutive Ones II** (51.8% | Med.) - Sliding window with flip
- **1055. Shortest Way to Form String** (61.4% | Med.) - Two pointers

---

## Binary Search

- **270. Closest Binary Search Tree Value** (49.4% | Easy) - BST search
- **272. Closest Binary Search Tree Value II** (60.9% | Hard) - BST k closest
- **302. Smallest Rectangle Enclosing Black Pixels** (60.7% | Hard) - Binary search in matrix
- **644. Maximum Average Subarray II** (37.6% | Hard) - Binary search on answer
- **702. Search in a Sorted Array of Unknown Size** (73.0% | Med.) - Binary search with unknown bounds
- **1060. Missing Element in Sorted Array** (59.5% | Med.) - Binary search
- **1064. Fixed Point** (63.8% | Easy) - Binary search
- **1231. Divide Chocolate** (60.3% | Hard) - Binary search on answer
- **1891. Cutting Ribbons** (52.9% | Med.) - Binary search on answer
- **1918. Kth Smallest Subarray Sum** (52.8% | Med.) - Binary search with prefix sums

---

## Greedy

- **252. Meeting Rooms** (59.2% | Easy) - Interval scheduling
- **253. Meeting Rooms II** (52.4% | Med.) - Interval scheduling with rooms
- **759. Employee Free Time** (72.6% | Hard) - Interval merging
- **1057. Campus Bikes** (59.1% | Med.) - Assignment problem
- **1058. Minimize Rounding Error to Meet Target** (45.7% | Med.) - Rounding optimization
- **1066. Campus Bikes II** (55.9% | Med.) - Assignment with constraints
- **1167. Minimum Cost to Connect Sticks** (71.6% | Med.) - Greedy with heap
- **1229. Meeting Scheduler** (55.2% | Med.) - Interval scheduling
- **1564. Put Boxes Into the Warehouse I** (67.3% | Med.) - Greedy placement
- **1580. Put Boxes Into the Warehouse II** (65.7% | Med.) - Greedy variant
- **1762. Buildings With an Ocean View** (80.9% | Med.) - Greedy traversal
- **2431. Maximize Total Tastiness of Purchased Fruits** (64.7% | Med.) - Greedy selection

---

## Backtracking

- **254. Factor Combinations** (50.4% | Med.) - Backtracking combinations
- **291. Word Pattern II** (48.7% | Med.) - Backtracking pattern matching
- **320. Generalized Abbreviation** (60.2% | Med.) - Backtracking abbreviations
- **351. Android Unlock Patterns** (53.5% | Med.) - Backtracking patterns
- **425. Word Squares** (54.5% | Hard) - Backtracking construction
- **1087. Brace Expansion** (66.7% | Med.) - Backtracking expansion
- **1258. Synonymous Sentences** (56.9% | Med.) - Backtracking sentences

---

## Math & Geometry

### Math
- **246. Strobogrammatic Number** (47.6% | Easy) - Number properties
- **247. Strobogrammatic Number II** (53.4% | Med.) - Number generation
- **266. Palindrome Permutation** (68.6% | Easy) - Permutation math
- **267. Palindrome Permutation II** (42.2% | Med.) - Permutation generation
- **296. Best Meeting Point** (61.3% | Hard) - Median in 2D
- **469. Convex Polygon** (40.1% | Med.) - Geometry validation
- **751. IP to CIDR** (53.4% | Med.) - IP address math
- **800. Similar RGB Color** (67.9% | Easy) - Color math
- **1056. Confusing Number** (49.3% | Easy) - Number validation
- **1088. Confusing Number II** (47.1% | Hard) - Number generation
- **1692. Count Ways to Distribute Candies** (63.6% | Hard) - Combinatorics
- **2184. Number of Ways to Build Sturdy Brick Wall** (49.4% | Med.) - Combinatorics
- **2189. Number of Ways to Build House of Cards** (62.5% | Med.) - Combinatorics
- **2964. Number of Divisible Triplet Sums** (67.5% | Med.) - Number theory

### Geometry
- **356. Line Reflection** (36.1% | Med.) - Line geometry
- **469. Convex Polygon** (40.1% | Med.) - Polygon geometry
- **1924. Erect the Fence II** (50.8% | Hard) - Computational geometry
- **2345. Finding the Number of Visible Mountains** (36.7% | Med.) - Geometry visibility

---

## Database

- **578. Get Highest Answer Rate Question** (40.1% | Med.) - SQL query
- **597. Friend Requests I: Overall Acceptance Rate** (41.2% | Easy) - SQL aggregation
- **614. Second Degree Follower** (40.5% | Med.) - SQL join
- **1076. Project Employees II** (50.3% | Easy) - SQL aggregation
- **1077. Project Employees III** (77.1% | Med.) - SQL window function
- **1107. New Users Daily Count** (45.0% | Med.) - SQL date aggregation
- **1112. Highest Grade For Each Student** (71.2% | Med.) - SQL window function
- **1113. Reported Posts** (64.9% | Easy) - SQL filtering
- **1127. User Purchase Platform** (46.6% | Hard) - SQL complex query
- **1132. Reported Posts II** (32.1% | Med.) - SQL aggregation
- **1142. User Activity for the Past 30 Days II** (35.6% | Easy) - SQL date filtering
- **1149. Article Views II** (47.2% | Med.) - SQL aggregation
- **1152. Analyze User Website Visit Pattern** (44.2% | Med.) - SQL pattern analysis
- **1173. Immediate Food Delivery I** (80.7% | Easy) - SQL date comparison
- **1225. Report Contiguous Dates** (57.3% | Hard) - SQL date ranges
- **1241. Number of Comments per Post** (65.8% | Easy) - SQL join
- **1264. Page Recommendations** (65.4% | Med.) - SQL recommendation
- **1270. All People Report to the Given Manager** (84.2% | Med.) - SQL hierarchical
- **1322. Ads Performance** (58.8% | Easy) - SQL performance metrics
- **1398. Customers Who Bought Products A and B but Not C** (71.7% | Med.) - SQL set operations
- **1607. Sellers With No Sales** (54.3% | Easy) - SQL left join
- **1699. Number of Calls Between Two Persons** (80.8% | Med.) - SQL call analysis
- **1821. Find Customers With Positive Revenue this Year** (87.6% | Easy) - SQL filtering
- **1826. Faulty Sensor** (50.3% | Easy) - SQL data validation
- **1892. Page Recommendations II** (45.3% | Hard) - SQL recommendation system
- **1949. Strong Friendship** (54.2% | Med.) - SQL friendship analysis
- **2199. Finding the Topic of Each Post** (50.1% | Hard) - SQL topic extraction
- **2985. Calculate Compressed Mean** (86.8% | Easy) - SQL aggregation
- **2987. Find Expensive Cities** (77.1% | Easy) - SQL city analysis
- **2989. Class Performance** (88.7% | Med.) - SQL performance analysis
- **2990. Loan Types** (63.6% | Easy) - SQL loan analysis
- **2991. Top Three Wineries** (55.0% | Hard) - SQL ranking
- **2995. Viewers Turned Streamers** (42.7% | Hard) - SQL user analysis
- **3054. Binary Tree Nodes** (78.6% | Med.) - SQL tree structure

---

## Other

### Simulation
- **293. Flip Game** (65.0% | Easy) - Game simulation
- **723. Candy Crush** (77.4% | Med.) - Game simulation
- **755. Pour Water** (48.4% | Med.) - Water simulation

### Hash Table / Set
- **249. Group Shifted Strings** (67.6% | Med.) - String grouping
- **288. Unique Word Abbreviation** (27.3% | Med.) - Abbreviation mapping
- **734. Sentence Similarity** (44.7% | Easy) - Similarity mapping
- **737. Sentence Similarity II** (50.9% | Med.) - Similarity with transitivity
- **760. Find Anagram Mappings** (84.0% | Easy) - Anagram mapping

### Heap / Priority Queue
- **253. Meeting Rooms II** (52.4% | Med.) - Heap for scheduling
- **358. Rearrange String k Distance Apart** (39.5% | Hard) - Heap for rearrangement
- **1167. Minimum Cost to Connect Sticks** (71.6% | Med.) - Heap for greedy

### Trie
- **1858. Longest Word With All Prefixes** (71.9% | Med.) - Trie for prefixes
- **642. Design Search Autocomplete System** (49.6% | Hard) - Trie for autocomplete

### Segment Tree / Fenwick Tree
- **308. Range Sum Query 2D - Mutable** (45.2% | Med.) - 2D segment tree

### Stack
- **716. Max Stack** (45.7% | Hard) - Stack with max
- **772. Basic Calculator III** (52.9% | Hard) - Stack for calculator

### Linked List
- **369. Plus One Linked List** (61.2% | Med.) - Linked list manipulation
- **708. Insert into a Sorted Circular Linked List** (38.4% | Med.) - Circular list

### Bit Manipulation
- **293. Flip Game** (65.0% | Easy) - Bit manipulation

### Interval Problems
- **252. Meeting Rooms** (59.2% | Easy) - Interval overlap
- **253. Meeting Rooms II** (52.4% | Med.) - Interval scheduling
- **370. Range Addition** (72.6% | Med.) - Range updates
- **759. Employee Free Time** (72.6% | Hard) - Interval merging
- **1229. Meeting Scheduler** (55.2% | Med.) - Interval scheduling
- **1272. Remove Interval** (67.0% | Med.) - Interval removal
- **2021. Brightest Position on Street** (60.5% | Med.) - Interval brightness
- **2158. Amount of New Area Painted Each Day** (55.5% | Hard) - Interval painting
- **2237. Count Positions on Street With Required Brightness** (62.6% | Med.) - Interval brightness
- **2655. Find Maximal Uncovered Ranges** (49.7% | Med.) - Range coverage

### Concurrency
- **1188. Design Bounded Blocking Queue** (73.3% | Med.) - Thread-safe queue
- **1242. Web Crawler Multithreaded** (50.6% | Med.) - Concurrent crawling
- **2636. Promise Pool** (79.5% | Med.) - Promise concurrency

### Miscellaneous
- **161. One Edit Distance** (34.5% | Med.) - Edit distance variant
- **280. Wiggle Sort** (68.4% | Med.) - Sorting variant
- **296. Best Meeting Point** (61.3% | Hard) - Manhattan distance
- **339. Nested List Weight Sum** (85.8% | Med.) - Nested structure
- **364. Nested List Weight Sum II** (66.1% | Med.) - Nested structure variant
- **544. Output Contest Matches** (77.4% | Med.) - Tournament bracket
- **681. Next Closest Time** (46.9% | Med.) - Time manipulation
- **683. K Empty Slots** (37.9% | Hard) - Sliding window variant
- **1121. Divide Array Into Increasing Sequences** (65.2% | Hard) - Array division
- **1199. Minimum Time to Build Blocks** (46.3% | Hard) - Optimization
- **1538. Guess the Majority in a Hidden Array** (69.3% | Med.) - Interactive problem
- **1618. Maximum Font to Fit a Sentence in a Screen** (61.7% | Med.) - Font fitting
- **1635. Hopper Company Queries I** (48.4% | Hard) - Complex query
- **1645. Hopper Company Queries II** (39.8% | Hard) - Query variant
- **1651. Hopper Company Queries III** (65.5% | Hard) - Query variant
- **1692. Count Ways to Distribute Candies** (63.6% | Hard) - Distribution counting
- **1868. Product of Two Run-Length Encoded Arrays** (59.5% | Med.) - Run-length encoding
- **1940. Longest Common Subsequence Between Sorted Arrays** (81.3% | Med.) - LCS variant
- **2021. Brightest Position on Street** (60.5% | Med.) - Position optimization
- **3009. Maximum Number of Intersections on the Chart** (45.0% | Hard) - Intersection counting
- **3073. Maximum Increasing Triplet Value** (35.7% | Med.) - Triplet finding
- **3078. Match Alphanumerical Pattern in Matrix I** (64.4% | Med.) - Pattern matching
- **3155. Maximum Number of Upgradable Servers** (42.3% | Med.) - Server optimization
- **3466. Maximum Coin Collection** (52.7% | Med.) - Coin collection
- **3481. Apply Substitutions** (77.6% | Med.) - String substitution

---

## Statistics

- **Total Problems**: 300+
- **Easy**: ~50 problems
- **Medium**: ~180 problems  
- **Hard**: ~70 problems

---

## Notes

- Problems are categorized by their primary algorithmic approach
- Some problems may fit multiple categories but are listed under the most relevant one
- Difficulty percentages and ratings are from LeetCode
- Premium problems require LeetCode Premium subscription to access

---

**Last Updated**: 2025-01-27

