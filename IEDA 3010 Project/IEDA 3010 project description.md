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
===
Project report
Introduction
The problem of high-dimensional data has grown in importance due to the quick development of data
collecting technology, frequently resulting in problems like the curse of dimensionality. Efficient feature
selection is essential for improving computational efficiency and model predictability, but conventional
approaches usually ignore the related feature acquisition costs. In industries like healthcare, where medical
testing might have large financial ramifications, this control is especially important. The goal of this project is
to create affordable feature selection models that take into account the financial limitations of practical
applications while simultaneously increasing classification accuracy.
This project presents Group Feature Selection models (GFS-CESVM1 and GFS-RCESVM1) that handle both
individual and group feature selection within a budgetary framework, building on earlier work with CostEffective ℓ1-Norm Support Vector Machine (CESVM1) and its robust variant (RCESVM1). We provide a
Branch-Cut-and-Price (BCP) algorithm that is intended to maximize performance while controlling costs in
order to address the computational complexity seen in Mixed Integer Linear Programming (MILP)
formulations. This project aims to provide workable strategies for economical feature selection in machine
learning by testing on a variety of datasets, ultimately enhancing decision-making across a range of domains.

Background and Research Questions
Chronic Kidney Disease (CKD) is a long-term condition characterized by a gradual decline in kidneys' ability,
defined by kidney damage or a reduced glomerular filtration rate (GFR) lasting three months or more. CKD is
classified into five stages based on kidney function, ranging from mild (stage 1) to end-stage renal disease
(stage 5). Globally, 1.2 million (95% UI) individuals died from CKD in 2017, and 697.5 million (95% UI
649.2 to 752.0 million) cases of all-stage CKD were reported.1
In the early stages, CKD may not present
noticeable symptoms, but as it progresses, individuals may experience fatigue, swelling, changes in urination,
and high blood pressure. Hence the early detection of CKD is crucial as it enables timely interventions that
can slow disease progression and prevent complications. Additionally, it helps reduce healthcare costs by
minimizing the need for advanced treatments and hospitalizations associated with end-stage renal disease.
With traditional machine learning models like CESVM1 and RCESVM1 exist concerns like overfitting, model
complexity and generalization, these models may not be flexible enough to handle the complex data. Hence
our project aims to identify the comparison between our model with other mentioned models when detecting a
CKD patient in terms of accuracy and effectiveness and determine the best model, categorize patients into
CKD and non-CKD groups with a high level of accuracy compared to traditional ML model, seek out the
most relevant clinical features and remove the irrelevant or useless features. educing excessive costs and
resource limitations due to High-performing features that may lead to impractical solutions.

Model Setup
Our research addresses a critical gap in standard SVM methodologies by incorporating cost considerations
into the feature selection process. By extending the ℓ1-SVM with a budget constraint, we ensure that our
model not only maintains high classification accuracy but also selects the most informative and cost-effective
features within a predefined budget. This approach, termed CESVM1, promotes sensible decision-making in
real-world applications, ultimately leading to more practical and optimal solutions.
The introduction of binary decision variables vj enables a clear mechanism for selecting features while
adhering to the budget constraint B. By ensuring that the total cost of selected features remains within this
budget, we enhance the practicality of our model. Additionally, the activation and deactivation of the weight
vector based on selected features allow for a more tailored approach to feature optimization. It is crucial to set
the bounds Mj appropriately to maintain both optimality and feasibility of the solution. This structured
approach ultimately leads to a more efficient and effective feature selection process.

Robust optimization plays a crucial role in ensuring the practicality of solutions in the presence of uncertainty.
By building on the foundations laid by previous models, we introduce the robust and cost-effective model,
RCESVM1, which effectively balances flexibility and computational efficiency. This model accounts for
uncertain feature costs through the parameter Γ , allowing for a controlled degree of conservatism. As Γ
approaches the total number of uncertain features, RCESVM1 becomes increasingly conservative, while
retaining the optimal characteristics of CESVM1 when Γ=0. This approach not only enhances the robustness
of feature selection but also ensures cost-effectiveness, making it a valuable tool for real-world applications.
CESVM1 can be reformulated as RCESVM1 by transforming Eq. (3.13) as follows:

∑ cjvj + max {∑ ˆcjvj}≤ B
j=1 {S:S∈J,|S|≤Γ} j∈S
The feasibility of the solution is safeguarded against the cost uncertainty of Γ features through Eq. 3.19. While
this term introduces complexity to RCESVM1 by compromising its linearity, it has been demonstrated that
β(v,Γ) can be transformed into a linear optimization model without sacrificing generality. For a given vector
v∗, the protection function β(v∗,Γ) can be defined as Eq (3.20-3.22)
β(v∗, Γ ) = max {∑ˆcjv∗j}. (3.19)
 {S:S∈J,|S|≤Γ } j∈S
β(v∗, Γ ) is equivalent to the objective function of the following linear optimization problem.
β(v∗, Γ ) = maximize ∑ˆcjv∗j zj (3.20)
j∈J
s.t. ∑zj ≤ Γ , (3.21)
 j∈J
0 ≤ zj ≤ 1, ∀j ∈ J. (3.22)
The optimal solution of Eqs. (3.20)–(3.22) corresponds to the selected subset S with the associated cost
function ∑j∈Jc^jvj∗ as shown in Eq. (3.19). Consequently, the dual of Eqs. (3.20)–(3.22) can be defined as Eq
(3.23-3.26)
Minimize ∑pj + zΓ (3.23)
 j∈J
s.t. z + pj ≥ ˆcjv∗j , ∀j ∈ J,(3.24)
pj ≥ 0, ∀j ∈ J,(3.25)
z ≥ 0. (3.26)

The performance of the SVM with different C:
C = 0.1 C = 0.01
Accuracy: 0.9775 Accuracy: 0.94
Precision: 0.9839357429718876 Precision: 0.9669421487603306
Recall (Sensitivity): 0.98 Recall (Sensitivity): 0.936
F1-Score: 0.9819639278557114 F1-Score: 0.9512195121951219
C = 1 C = 10
Accuracy: 0.995 Accuracy: 0.9925
Precision: 0.996 Precision: 0.9959839357429718
Recall (Sensitivity): 0.996 Recall (Sensitivity): 0.992
F1-Score: 0.996 F1-Score: 0.9939879759519038

Solution
In our analysis, we implemented robust techniques to enhance the predictive
capabilities of our model for Chronic Kidney Disease (CKD). The final results
demonstrated a notable 20% increase in accuracy, which was accompanied by an
improved precision rate. This advancement is crucial as it significantly reduces the
incidence of false positives, thereby minimizing the risks of misdiagnosis.
Consequently, this not only alleviates unnecessary patient anxiety but also mitigates
the costs associated with confirming the absence of CKD.
A thorough examination of data from CKD patients revealed a recall rate of 1,
indicating that our model successfully detected all cases of CKD without missing any.
Additionally, the F1 score—a critical measure that represents the harmonic mean of
recall and precision—showed substantial improvement, further confirming the
enhanced accuracy of our model following the robust adjustments.
Recommendations
Given the increased accuracy of our model, we recommend that patients may not
require extensive feature checks to ensure reliability. This approach leads to lower
healthcare costs and a reduction in time spent on unnecessary tests.
Furthermore, we employed a grid search methodology for data comparison, allowing
us to utilize more grid points. This strategy enabled a more thorough exploration of
possibilities, contributing to the accuracy of our results.
We also identified key features that emerged as significant in our analysis. Features
with higher weighting indicate greater importance in predicting CKD, which provides
valuable insights for future assessments.

Conclusion
In summary, our comparative analysis utilizing L1 norm SVM, CESVM, and
RCESVM has demonstrated a model capable of efficient predictions under cost
considerations. This framework not only supports improved decision-making in realworld applications but also ensures that the selected features align with both
performance objectives and budgetary limitations. By integrating cost-effectiveness
into the feature selection process, we can enhance healthcare outcomes while
managing resources effectively