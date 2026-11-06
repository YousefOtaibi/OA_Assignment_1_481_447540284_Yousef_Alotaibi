# My Answers - Assignment 1 (CFLP: VNS vs Gurobi)

**Student Information:**
- **Student ID:** 447540284
- **Student Name:** Yousef Alotaibi
- **Gurobi Version Used:** [x] Academic [ ] Free
- **Date Completed:** 6 Nov 2026

---

## Section A: Solution Quality Analysis (4 marks)

### A.1 (2 marks) - Gap Analysis by Categories

**Analysis of Plot 01:**

The gap is generally higher for large instances than for small and medium instances. Moderate instances have the highest gap values, while easy instances have the lowest. This shows that VNS has more difficulty finding high-quality solutions when the problem becomes more challenging.

**Specific Observations:**
- Highest median gap size: Large
- Median gap value: 14.65%
- Effect of difficulty on gap:  The gap increases from easy to moderate instances, then decreases for expensive instances.

**Outliers identified:**

Some instances have high gaps above 20%. The highest gap is 26.14% in instance 76 (Medium - Moderate)

**Interpretation:**

These results show that problem difficulty affects VNS performance. The algorithm can find better solutions for easy instances, but its solution quality decreases for moderate instances. This may happen because more difficult problems have a more challenging search space.

---

### A.2 (2 marks) - Overall Solution Quality Statistics

**From Excel File (Sheet "All Results"):**

- Total instances analyzed: 144
- Instances with gap < 5%: 4 ( 2.78% )
- Instances with gap < 10%: 28 (19.44% )
- Mean gap across all instances: 13.88%
- Standard deviation of gap: 4.85%

**Interpretation:**

The results show that VNS does not provide very high-quality solutions consistently. Only 2.78% of the instances have a gap below 5%, and 19.44% have a gap below 10%. The average gap is 13.88%, which means that VNS solutions are usually higher in cost than the optimal Gurobi solutions. The standard deviation of 4.85% shows some variation in solution quality between instances.

---

## Section B: Computational Efficiency Analysis (4 marks)

### B.1 (2 marks) - Time Comparison

**Analysis of Plot 02:**
VNS is faster than Gurobi across all three instance sizes. The average VNS time is about 1.15 seconds for small instances, 1.44 seconds for medium instances, and 1.40 seconds for large instances. In comparison, Gurobi takes 12.55, 12.36, and 5.62 seconds respectively. This shows that VNS requires less computational time in these experiments.

**Size at which VNS becomes significantly faster:**

VNS is already significantly faster for small instances. Its average time is 1.15 seconds compared to 12.55 seconds for Gurobi.

**Most challenging configurations:**
- For VNS: Medium - Moderate (Instance 66) with time: 5.88 seconds.
- For Gurobi: Small - Expensive (Instance 40) with time: 300.39 seconds.

**Detailed Comparison:**

Gurobi takes much longer than VNS in many instances, especially when the instances are difficult. For example, Gurobi takes 300.39 seconds for instance 40, while VNS takes only 2.16 seconds. Overall, VNS provides a faster solution, although Gurobi provides the optimal solution.

---

### B.2 (2 marks) - Speedup Analysis

**Analysis of Plot 03:**

The speedup results show that VNS is generally faster than Gurobi. The speedup factor is higher than 1 in most instances, which means VNS requires less time.

**Average speedup factors:**
- Small instances: 8.08x faster
- Medium instances: 8.01x faster
- Large instances: 6.34x faster

**Instances where Gurobi is faster (speedup < 1):**

There are 32 instances where Gurobi is faster than VNS. Most of these cases are easy instances, where Gurobi can solve the problem in a short time.

**Practical Implications:**

These results show that VNS can be useful when fast solutions are needed, especially for large or difficult problems. However, Gurobi is still important when an optimal solution is required. Therefore, the choice depends on the time available and the required solution quality.

---

## Section C: Scalability Analysis (3 marks)

### C.1 (1.5 marks) - Scalability Behavior

**Analysis of Plot 04:**

**VNS Scalability:**

VNS runtime remains almost stable as the problem size increases. The average time is about 1.15 seconds for small instances, 1.44 seconds for medium instances, and 1.40 seconds for large instances. This shows that VNS handles the tested problem sizes with similar computational time.

**Gurobi Scalability:**

Gurobi average runtime is 12.55 seconds for small instances, 12.36 seconds for medium instances, and 5.62 seconds for large instances. The runtime decreases in the large group. However, this does not necessarily mean that larger problems are easier, because the instances also have different difficulty levels.

**Comparison:**

Based on these experiments, VNS has more stable runtime across the three problem sizes. Gurobi runtime varies more between the groups. Therefore, VNS shows more consistent scalability in the tested instances.
---

### C.2 (1.5 marks) - Growth Rate and Predictions

**Observed Growth of Average Runtime (from your results):**

| | Small | Medium | Large | Small -> Medium (x) | Medium -> Large (x) |
|---|---|---|---|---|---|
| VNS avg time (s) 1.15 | 1.44 | 1.40 | 1.26x | 0.97x| 
| Gurobi avg time (s) 12.55 | 12.36 | 5.62 | 0.99x | 0.45x |

**Shape of growth in Plot 04:**
- VNS: [x] Roughly steady [ ] Steadily increasing [ ] Sharply increasing
- Gurobi: [x] Roughly steady [ ] Steadily increasing [ ] Sharply increasing

**Justification:**

VNS runtime is roughly steady because its growth ratios are 1.26x and 0.97x. Gurobi runtime decreases across the groups, with ratios of 0.99x and 0.45x. This may be affected by differences in instance difficulty, so the results should not be interpreted as proof that larger problems are easier for Gurobi.

**Rough Prediction for Extra Large Instance (n=50, m=20):**
- Predicted VNS time: 1.36 seconds
- Predicted Gurobi time: 2.56 seconds
- How I computed it (e.g., applying the Medium -> Large ratio again): I multiplied the average Large runtime by the Medium-to-Large ratio again to estimate the Extra Large runtime.

**Suitability for Very Large Instances:**

I would recommend VNS for very large problems when a fast solution is needed. In these experiments, VNS runtime remains almost stable across the tested sizes. However, its solution may not be optimal, so Gurobi may still be preferred when optimality is important.

---

## Section D: Quality-Time Tradeoff Analysis (3 marks)

### D.1 (1.5 marks) - Sweet Spot Identification

**Analysis of Plot 05:**

**Sweet Spot:**

The sweet spot depends on the balance between solution quality and computational time. VNS is generally faster, but it does not always provide a gap below 5%. In the four instances with a gap below 5%, Gurobi was faster on average. This shows that the best method depends on the required solution quality and available time.

**Time Savings for High-Quality Solutions (gap < 5%):**
- Average VNS time: 0.620 seconds
- Average Gurobi time: 0.305 seconds
- Absolute savings: -0.315 seconds
- Relative savings: -103.12% 

**Interpretation:**

For practitioners, this means that a faster algorithm is not always the best choice when very high solution quality is required. Gurobi is a better choice for these high-quality cases because it achieved a lower average runtime. VNS is still useful when a good solution is acceptable and time is limited.


---

### D.2 (1.5 marks) - Practical Decision Making

**Scenarios Justifying 10-15% Gap:**

1. Emergency delivery planning: When a company needs to make delivery decisions quickly, a solution with a 10-15% gap may be acceptable because saving time is more important.


2. Daily warehouse operations: When the company needs to solve scheduling and facility allocation problems frequently, VNS can provide good solutions in less time.

3. Temporary or short-term planning: When decisions will be updated soon, spending a long time finding an optimal solution may not be necessary. A solution with a 10-15% gap can be sufficient.

**Recommendation for Real-World Logistics Company:**

I would recommend using VNS for situations where fast decisions are important and a near-optimal solution is acceptable. However, Gurobi should be used when the company needs the best possible solution and has enough time. A combination of both methods can also be useful: VNS can provide a quick solution, while Gurobi can be used for important planning decisions.

---

## Section E: Algorithm Understanding (3 marks)

### E.1 (1.5 marks) - VNS Neighborhood Structures

**Role of Each Neighborhood:**

**N1 (Open Facility):**
- Purpose: Open a closed facility and reassign clients to the nearest open facilities.
- Contribution: [ ] Intensification [x] Diversification
- Explanation: It explores new solutions by adding a facility that was previously closed. This can provide new assignment possibilities.

**N2 (Close Facility):**
- Purpose: Close an open facility and open a different closed facility.
- Contribution: [ ] Intensification [x] Diversification
- Explanation: It tries replacing an open facility with a closed one. This can reduce fixed costs or improve the solution by exploring different facility combinations.

**N3 (Swap Facilities):**
- Purpose: Swap one open facility with one closed facility.
- Contribution: [ ] Intensification [x] Diversification
- Explanation: It explores different combinations of open facilities. It checks possible swaps until the maximum number of neighbors is reached.

**N4 (Reassign Clients):**
- Purpose: Move a client from its current facility to another open facility.
- Contribution: [x] Intensification [ ] Diversification
- Explanation: It improves the current solution by trying different client assignments without changing the open facilities.

**How They Complement Each Other:**

The four neighborhoods work together to improve the solution. N1, N2, and N3 change the open facilities to explore different solutions. N4 improves the current solution by changing client assignments. This allows VNS to explore new areas and improve existing solutions.

---

### E.2 (1.5 marks) - Convergence Behavior Analysis

**Selected Convergence Plots:**

**Plot 1:** [Instance name:Medium – Moderate]
- Pattern: [x] Smooth [ ] Multiple jumps
- Description: The convergence curves are mostly flat, with very little improvement during the iterations.
- What it reveals: VNS does not make significant improvements in most of these instances and keeps similar solution quality.

**Plot 2:** [Instance name:Medium – Expensive]
- Pattern: [ ] Smooth [x] Multiple jumps
- Description: Some curves show sudden downward steps during the iterations, while others remain almost flat.
- What it reveals: VNS can sometimes find better solutions after several iterations, but the improvement does not happen consistently in all instances.

**Plot 3:** [Instance name:Large – Expensive]
- Pattern: [ ] Smooth [x] Multiple jumps
- Description: Several curves show sudden improvements at different iterations, followed by periods with no improvement.
- What it reveals: The algorithm can improve large and difficult instances through occasional jumps, although some instances remain unchanged.

**Role of Shaking Mechanism:**

The shaking mechanism helps VNS escape from local optima by moving the search to a different solution. The convergence plots show sudden improvements in some medium and large expensive instances. These jumps suggest that the algorithm can find better solutions after exploring different neighborhoods. Without shaking, the search may remain stuck at the same solution.

---

    ## Section F: Critical Reflection (3 marks)

    ### F.1 (1 mark) - Limitations and Improvements
    **Main Limitations of Current VNS Implementation:**

    1. Limited number of neighbors: The algorithm checks only a limited number of neighboring solutions, so it may miss better solutions.
    2. Random selection: Facilities and clients are selected randomly, which can make the results different between runs.
    3. Limited client reassignment: N4 moves one client at a time and may not find better assignments that require moving several clients together.

    **Suggested Improvements:**

    1. Increase the number of neighbors: This allows VNS to explore more possible solutions and may improve solution quality, but it can increase runtime.
    2. Use smarter selection methods: Select facilities and clients based on their costs and capacity instead of relying only on random selection. This may help find better solutions.
    3. Improve the reassignment neighborhood: Allow moving more than one client when needed. This can explore more assignment possibilities and improve the final solution.
    ---

    ### F.2 (1 mark) - Real-World Deployment Considerations

    **Additional Constraints for Real Logistics Company:**

    1. Delivery time windows: Some customers require deliveries at specific times, so the company must respect their schedules.
    2. Maximum delivery distance: Facilities should serve customers within an acceptable distance to reduce delivery time and transportation costs.
    3. Facility operating hours: Each facility may have limited working hours, which must be considered when planning operations.

    **Additional Objectives:**

    In real logistics companies, minimizing cost is not the only objective. The company may also want to reduce delivery time, reduce fuel consumption and emissions, improve customer satisfaction, and balance the workload between facilities. These objectives can help the company make better practical decisions.
    ---

    ### F.3 (1 mark) - Exact Method vs Heuristic in Practice

    **Gurobi Optimality Status (from the `gurobi_status` column):**
    - Instances solved to proven optimality: 144 out of 144
    - Instances stopped at the time limit: 0 out of 144
    - Do the time-limit instances share a size/difficulty? No. All 144 instances were solved to proven optimality by Gurobi, and none stopped at the time limit.

    **What VNS Gives Up and What It Gains:**

    VNS gives up some solution quality because its average optimality gap is 13.88%. However, it saves computational time. The average VNS runtime is 1.33 seconds, while Gurobi takes 10.18 seconds. This means VNS saves approximately 8.85 seconds per instance, or 86.94% of the average Gurobi runtime. Therefore, VNS is much faster, but its solutions are not always optimal.

    **Practical Value of Heuristics:**

    Heuristics such as VNS are useful in real applications because they can provide good solutions in a short time. In our experiments, VNS was much faster than Gurobi, although its average gap was 13.88%. This makes it useful when quick decisions are more important than finding the exact optimal solution. However, Gurobi is still valuable when solution optimality is required.
    ---

## Section G: BONUS - VNS Improvement Challenge (+3 marks, optional)

*Leave this section empty if you do not attempt the bonus. See Section 8 of the guide. Your improved notebook (`StudentID_FirstName_LastName_Assignment1_IMPROVED.ipynb`) must be pushed to your repository.*

### G.1 (1 mark) - Bug Identification

**Where is the bug?** (cell / function / line numbers in `Assignment_1.ipynb`):

[Paste the faulty line(s) of code]

**What does the bug do?**

[Describe the specific issue]

**Why does it degrade VNS performance?**

[Explain the effect on the search and link it to the high gaps (>20%) in your results]

---

### G.2 (1 mark) - The Fix

**Corrected code:**

```python
# paste your fixed line(s) here
```

**Why does the fix work and why does it not break the rest of the algorithm?**

[Explanation]

---

### G.3 (1 mark) - Demonstrated Improvement

**Before vs After (same instances):**

| Metric | Original VNS | Improved VNS |
|---|---|---|
| Mean gap (%) | | |
| Std of gap (%) | | |
| Instances with gap < 5% | | |
| Instances with gap > 20% | | |
| Mean VNS time (s) | | |

**Analysis:**

[Discuss the improvement, and any change in running time]

**Improved results files (names in your repository):** ___________

---

## Additional Comments (Optional)

[Any additional observations, challenges faced, or insights gained]

---

## Declaration

I hereby declare that:
- I have completed this assignment independently
- All numerical results are from MY experiments using MY student ID
- All analysis and interpretations are MY own work
- I have not copied results or answers from other students
- I understand the consequences of academic dishonesty

**Signature:** Yousef Alotaibi

**Date:** 6 Nov 2026

---

**END OF MY ANSWERS**
