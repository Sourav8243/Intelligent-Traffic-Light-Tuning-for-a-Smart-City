# Intelligent-Traffic-Light-Tuning-for-a-Smart-City
A metro city with 12 interconnected junctions wants a self-optimizing traffic controller.  
Objectives: 
• Reduce waiting time 
• Maintain green-wave flow 
• Prioritize emergency vehicles 
• Minimize stops per vehicle 
• Adapt to dynamic congestion

What I implemented (quick summary)

Read your dataset intelligent_streetlight_dataset.csv and aggregated traffic per Street ID (the file you uploaded).
Built a lightweight traffic-delay model (uniform arrivals approximation) to estimate:
average delay (s/vehicle) ≈ red_time / 2,
stops per vehicle ≈ red_time / cycle,
emergency/“special event” penalty if a junction with Special Event==1 had insufficient green.
Designed a Genetic Algorithm (GA) to minimize a weighted objective combining delay, stops, and emergency penalty (weights chosen to balance units).
Baseline used: fixed cycle 90 s, green 45 s (for all junctions).
GA optimized per-junction: cycle time (60–120 s) and green for main movement (≥10 s, ≤cycle−10 s).
Outputs produced: optimized signal timings (per junction), before-vs-after metrics, and GA convergence plot.

Results (key numbers)
Before vs After (aggregated over junctions)
Average delay (s/vehicle): Before = 22.50 s/veh, After = 5.00 s/veh
Stops per vehicle: Before = 0.50, After = 0.0833
Objective score: Before = 46.50, After = 7.50
Optimized timings (per junction — summary)

For the junctions present in your dataset (Street ID 1..10), the GA converged on:
Cycle Time ≈ 120.0 s, Green Main ≈ 110.0 s, Red = 10.0 s for each junction in the current model.
