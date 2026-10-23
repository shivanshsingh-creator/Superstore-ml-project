WHERE IS THE RETAILER LOSING MONEY?
===================================
Machine Learning on the Sample Superstore dataset
 
Submitted by: Goutam Singh Mandloi | Batch: 147 
 
Domain: Retail & E-commerce
Dataset: Sample Superstore (public, Kaggle): 9,994 order lines, 13 columns → 9,977 rows after cleaning
 
PROBLEM
-------
A US retailer makes $2.3M in sales but keeps only $286K as profit. About 1 in 5 orders loses money, and those orders wipe out roughly 35% of what the good orders earn. This project finds out why and uses three types of machine learning to stop the leak.
 
1. How much profit will this order make?
   ML type: Regression | Model: Linear Regression vs Random Forest
2. Will this order lose money, yes or no?
   ML type: Classification | Model: Logistic Regression vs Decision Tree
3. Which states behave alike?
   ML type: Clustering | Model: KMeans (K = 4)
 
WHAT THE DATA SHOWED
--------------------
- Orders with a discount above 20% are about 14% of all orders but cause about 89% of all losses ($138.5K of $156K).
- Furniture earns only a 2.5% margin; Tables alone lose $17.7K.
- Central is the weakest region (7.9% margin) and gives the highest average discount.
- Discount vs profit is not a straight line but a "cliff" after 20%, so tree-based models work best.
 
MODEL RESULTS (TEST DATA)
-------------------------
- Regression:
    Best model: Random Forest
    Result: R² 0.70, average error ≈ $19 per order (Linear Regression: R² 0.24)
- Classification:
    Best model: Logistic Regression
    Result: Accuracy 91%, catches 95% of loss orders
- Clustering:
    Best model: KMeans, K = 4
    Result: 10 "problem" states with ~32% average discount and negative profit
 
CURRENT LOSSES WITHOUT MACHINE LEARNING
---------------------------------------
- $156K lost on loss-making orders, which is 35% of all profit earned.
- 1,869 orders (18.7%) lose money, and the store only finds out after the sale.
- Discounts are given without checking the expected profit. Every order with 45% or more discount lost money.
- The same discount habits are used everywhere, so 10 states lose money overall.
- Industry picture: EY found about 70% of standard discounts and promotions lose money, and discounts above 20% perform worse. Bain reports retailers spending 20–50% of net sales on markdowns.
 
BEFORE VS AFTER MACHINE LEARNING
--------------------------------
- Approving a discount:
    Before ML: Based on gut feeling; no idea of profit until the sale is done
    After ML: Model predicts the profit first. Example: one $958 table order goes from +$231 profit at 0% discount to -$3 at 20% and -$451 at 50%
- Spotting loss orders:
    Before ML: Found only after the money is lost
    After ML: Flagged in advance: 95% of loss orders, covering 99% of the loss dollars
- Accuracy of profit estimates:
    Before ML: Guessing the average: off by ≈ $61 per order
    After ML: Random Forest: off by ≈ $19 per order (3× more accurate)
- Regional strategy:
    Before ML: Same rules for all 49 states
    After ML: 4 state groups; discount control starts in the 10 problem states
- Total losses:
    Before ML: $156K lost (35% of earnings wiped out)
    After ML: Up to $138.5K of that can be avoided by stopping discounts above 20%
- Profit margin:
    Before ML: 12.5%
    After ML: Up to ~18% if the high-discount losses are avoided
 
BENEFITS OF IMPLEMENTING MACHINE LEARNING
-----------------------------------------
- Higher profit: stopping the high-discount leak could lift profit from $286K towards $425K.
- Faster, safer decisions: salespeople see expected profit before giving a discount.
- Early warning: risky orders go to a manager for approval instead of losing money silently.
- Targeted action: effort goes to the 10 problem states and to Tables and Bookcases, not everywhere.
- Industry evidence: analytics-driven pricing and promotion raised gross profit by 8–12% (EY), and a Bain pilot raised net profit margin by 24% compared with control stores.
 
RECOMMENDATIONS
---------------
1. Cap discounts at 20%. Anything higher needs manager approval, backed by the risky-order model.
2. Review pricing for Tables and Bookcases.
3. Start discount control in the 10 problem states (Texas, Ohio, Pennsylvania, Illinois and others).
