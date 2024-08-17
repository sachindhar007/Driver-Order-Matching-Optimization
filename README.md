# Optimizing Driver-Order Matching Using Greedy and Hungarian Algorithms
# 1. Introduction
In logistics and delivery systems, efficiently matching drivers to orders is critical for minimizing delays and optimizing resource utilization. This project focuses on implementing and comparing two approaches—Greedy and Hungarian algorithms—for driver-order matching. We aim to minimize the Estimated Time of Arrival (ETA) while considering assignment efficiency across multiple order bulks.

# 2. Problem Statement

The goal is to assign drivers to orders in a way that reduces the total ETA while optimizing the overall assignment process. The dataset contains 20 orders placed within a narrow time window and 25 available drivers, resulting in 500 driver-order pairs. The orders are grouped into four bulks, each covering a 5-second interval.

# 3. Dataset Overview
Order Information: 20 unique orders placed on 2023-08-20 between 13:30:01 and 13:30:18.
Driver Information: 25 drivers available for assignment.
Order Bulk Grouping: Orders are divided into four bulks, each lasting 5 seconds.
ETA: The dataset includes the estimated time of arrival (ETA) for each driver to the pickup location of an order.

# 4. Approach
# 4.1 Greedy Matching Algorithm
The Greedy algorithm selects the driver with the shortest ETA for each order sequentially, without considering the overall optimization of the assignment.
## Steps:
Sort orders by timestamp.
For each order, select the driver with the shortest ETA.
Assign the selected driver and remove them from the pool for subsequent assignments.
Repeat until all orders are matched.

# Outcome: 
The Greedy algorithm provided an initial ETA total of 4760 across the driver-order pairs.
4.2 Bulk Matching Using Hungarian Algorithm

To achieve better global optimization, we applied the Hungarian algorithm using the linear sum assignment method from the scipy.optimize library. Orders within each bulk were grouped and optimized collectively.

# Steps:
Group orders by their respective bulks.
Construct a cost matrix representing ETAs between orders and drivers.
Solve the assignment problem using the Hungarian algorithm to find the optimal driver-order pairs.
Remove assigned drivers from the available pool and repeat for the next bulk.

# Outcome: The Hungarian algorithm improved the total ETA, reducing it to 4430—a 6.93% improvement compared to the Greedy approach.

# 5. Results and Analysis
Greedy Matching Total ETA: 4760
Bulk Matching Total ETA (Hungarian): 4430
Percentage Improvement: 6.93%

The results demonstrate that the Hungarian algorithm offers better global optimization, reducing the total ETA by approximately 6.93% compared to the Greedy method. The bulk approach allowed for more strategic assignments, leading to a more efficient matching process.

# 6. Conclusion
This project successfully implemented and compared Greedy and Hungarian algorithms for driver-order matching. The Hungarian algorithm, combined with bulk processing, yielded superior results by optimizing resource allocation and minimizing total ETA. This approach can be scaled and applied to similar real-world logistics and delivery systems where efficient assignment is crucial.
