Project C: Support Vector Machine for Cost-effective Feature
Selection
(TA: Yuhao YAN yuhao.yan@connect.ust.hk)
In the era of big data, feature selection is indispensable as a dimensional reduction technique to lower data complexity and enhance machine learning performances.
However, there are only a few studies on cost-based feature selection. Most conventional feature selection methods only focus on classification performances, while they exclude the impact of associated feature costs. 
In real applications, selected features without cost consideration may lead to impractical solutions regardless of their high classification performances due to excessive expenses and resource usage limits. Support Vector Machine (SVM) is a commonly used tool for feature selection, andL1-norm SVM can be written as a MILP problem.

So, a natural idea is to solve the cost-effective feature selection by extending L1-norm SVM.
In this project, you have the below tasks:
(1) You are expected to build a MILP model for L1-SVM and extend the model to solve the cost-effective feature selection problem.
(2) Considering the cost variance commonly exists, you need to build a robust model to address the feature cost uncertainty.
(3) There are some data attached in the project. You need to use your model to process this data and compare your model with other models. You can also use more data mentioned in the reference paper.
(4) The real-world data usually has a group structure, so you can try to build a MILP model for the Group Feature Selection. (Optional)
References:
- Lee I G, Zhang Q, Yoon S W, et al. A mixed integer linear programming support vector
machine for cost-effective feature selection[J]. Knowledge-based systems, 2020,
203:106145.
- Lee I G, Yoon S W, Won D. A mixed integer linear programming support vector machine
for cost-effective group feature selection: branch-cut-and-price approach[J]. European
Journal of Operational Research, 2022, 299(3): 1055-1068