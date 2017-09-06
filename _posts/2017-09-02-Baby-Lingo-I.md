---
layout: post
title: Baby Lingo I
excerpt_separator:  <!--more-->
---
<h1>Baby Lingo I</h1>

*I'm preparing for the CUMCM (a math modeling contest) and learning lingo software for solving optimization and graphic problem. So I  write down this series blog as my notes.*

After reading this article, maybe you will know what's lingo and be able to solve  some simplest problem with lingo. 

<!--more-->

## 1. Introduction

Following content is from *[www.lindo.com](http://www.lindo.com)*, Lindo System's website.

> Lingo is an optimization modeling software for linear, nonlinear, and integer programming.

> LINGO is a comprehensive tool designed to make building and solving Linear, Nonlinear (convex & nonconvex/Global), Quadratic, Quadratically Constrained, Second Order Cone, Semi-Definite, Stochastic, and Integer optimization models faster, easier and more efficient.

For more information, you can visit its website or wiki.

Using lingo to solve praticular problem, you first transfer the problem to mathematical form. Then transfer it to lingo code (lingo 'reads' problem by loading codes inputted). Just click the 'Solve' button, the results will be shown in a new tab. Following is a typical look of lingo.

![](http://ovlm69ca3.bkt.clouddn.com/tripical_interface.png)

Codes, report and status panel are divided into different windows. And you can find that it is a total English software. '3' in the title 'LINGO3' means currently more than one lingo models exist, and this one is the third one, other two windows are of this model. In the 'Model' window, you edit your codes. In the 'Solver Status' window, some basic information of this model is shown. And the results are shown in the 'Report' window.

## 2. Basic Basic Grammar

- `model:  ......  end` is the outtermost frame, all the work are done in this frame. Actually, it can be omitted.
- Almost all sentences are ended with a semicolon `;`.
- `!COMMENT;` ! starts a comment, which can be in one or mutiple lines. And remember comment also ends with a semicolon `;`.
- You can put `[NAME]` at the start of constraints'line to give it a readable name.
- To solve a simple typical optimization problem, put your objective function in a front position followed by the constraints. If you want the max or min value of the objective function, you can write your function in such formats `max = obj_func`  `min = obj_func`. Notice that there are asterisk `*` between coefficients and variables.

## 3. Read the Status Panel
An example of Status Panel is shown in the previous figure, which is to simple to satisfy this section, so I put another figure below.

 ![](http://ovlm69ca3.bkt.clouddn.com/example01.png)
 
Solver Status part briefly shows the type of the model and solution, result and some information of the process solving the problem. Probable display of State are 'Global Optimum', 'Local Optimum', 'Feasible', 'Infeasible', 'Unbounded', 'Undetermined' and 'Interrupted'. Objective row gives the value of resulting objective function.  Next row 'Infeasibility' is the amount of constraints not satisfied. Iterations is the times of iterations, which is not interested by us in simple problems.

Extented Solver Status part shows more information. First row Solver Type is the special program used in solving this model, there are B-and-B(branch and bound), Global(global solver), Multistart. Best Obj is the best result till now. Steps is current number of steps of the special program. If you concentrate your eyes on the screen, you can find the value of Steps and Best Obj changes during the process of solving problem.

In the right side, there are amounts of variables and constraints including total numbers, nonlinear numbers and integer numbers. In the right bottom, there are memory used and running time.

## 4. Practice & Read the Report

In this part, we solve a simple real problem and read the Lingo Report.

The problem is: 
> A milk products factory procuce A1 and A2 two kinds products, 3kg A1 can be produced by a pail of milk on equipmentI in 12h, 4kg A2 can be produced by a pial of milk by equipmentII in 8h. Suppose the products can be sold out. And the profit is $24/1kgA1, $16/1kgA2. Everyday the factory only has 50 pails of milk. And the total labour hours is 480h. EquipmentI can produce 100kg A1 at most one day, while equipmentII is not limited. Please design a produceing plan to get the most of the profit. (from. Shuxue Moxing, Qiyuan Jiang)

Actually the obj func and constraints are obvious. You can easily write down the mathamatical form. And transfer it to the lingo code.

![](http://ovlm69ca3.bkt.clouddn.com/Report1.png)

Compared with the Status Panel, the report has more economical or financial meanings. First paragraph shows that a global optimal solution is found. And the objective value is 3360 (i.e. the factory can earn $3360 per day). And no constraint is not satisfied. In the lower part, there are the values of variables to get such good obj value. 

Reduced cost is the loss on profit(obj value) when producing one more unit of the corresponding product(incresing one unit corresponding variable). Normally, when the reduced cost is positive, the corresponding variable is zero. 

Slack or Surplus is the remaining amount of each constraints(i.e. how much milk, labour time, efficient time of E1 are remained,  or the difference between two sides of the constraints while substituting variables to the inequalities). We can test the [CAPT], `100 - 3 * x1 = 100 - 3 * 20 = 40`.

Dual Price is the increment of profit when incresing one unit of the 'resource'. (i.e. incresing one on the right side of the constraint'inequality). You can test it on your lingo, changing the 50 on line [MILK] to 51, you can see the obj value will changing to 3408.000. In economic field, it is called 'shadow price' as well.

## 5. Brief Summary

Here is the most basic lingo. The core concept is transfer the problem to mathamatical form and transfer the math to the codes. What's more,  add `[NAME]` and `!COMMENT` in your code to meke it more readable. Using `x^2` **`^`** to represent power, you can solve problems more complex.
