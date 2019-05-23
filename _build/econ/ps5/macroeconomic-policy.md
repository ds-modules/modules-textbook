---
interact_link: content/econ/ps5/macroeconomic-policy.ipynb
kernel_name: python3
title: 'Macroeconomic Policy (PS5)'
prev_page:
  url: /econ/ps3/flex_price
  title: 'Flex Price Economy (PS3)'
next_page:
  url: /english/english-intro
  title: 'English'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Problem Set 5: Macroeconomic Policy

_Due xx/xx/2018_

This assignment covers chapters 16-21 in the textbook, covering how policy decisions affect the economy.

## Chapter 16: Stabilization Policy
> This will likely be the bulk of the assignment. We can include all or most of the short-answer questions, and the computational monetary policy questions can be accomplished by just writing one or two functions to calculate inflation and unemployment.

#### Monetary vs. Fiscal Policy

$1.$ Why do economists today tend to believe that monetary policy is superior to discretionary fiscal policy as a stabilization policy tool? In what circumstances that you can imagine would this belief be reversed? (One paragraph only!)

$Answer: $ 


#### Raising Investment

$2.$ Suppose that the government and central bank together want to keep GDP constant but raise the rate of investment. What policies can they follow to achieve this? (One sentence only!)

$Answer: $

#### Credibility

$3.$ Former Federal Reserve Vice Chair Alan Blinder has remarked that Alan Greenspan’s policies at fighting unemployment have been much more aggressive in attempting to reduce unemployment than any Federal Reserve Chair with less of a reputation as an inflation hawk would dare attempt. Can you make sense of this remark?

$Answer: $

#### Reputation

$4.$ Suppose that you believe that investors, businesses, and workers in your economy have rational expectations of inflation. Suppose that you have a choice between two candidates to head your central bank—one of whom believes that the central bank must always do whatever is necessary to keep inflation low, and the other of whom believes that if the central bank were to push unemployment above the natural rate to try to reduce inflation it would be making a serious mistake. Which candidate would you prefer to run your central bank, and why?

$Answer: $

#### Sticky Price Output and  Interest Rates

$5.$ Describe how, if at all, each of the following developments affects the real interest rate and output in the short run (or whether it is not possible to tell). In parts (1) and (2), assume that the central bank is following an interest rate rule; in parts (3) and (4), use the information in the question to decide what assumption to make about how monetary policy is being conducted:

> 1. The government cuts taxes.
2. The government cuts taxes and government purchases by equal amounts.
3. The government cuts taxes and, at the same time, the central bank changes its monetary policy rule so that it sets a lower real interest rate at a given level of output than before.
4. The central bank lowers its target for the money stock.

$Answer: $

#### Monetary Policy Rules

$6.$ Suppose the central bank changes its policy rule to respond more to changes in output. Specifically, it decides not to change the real interest rate at the current level of output, but that it will increase it by more than before if output rises, and cut it by more than before if output falls:

>1. Would you use the IS–MP or IS–LM model to analyze the effects of this development? Why?
2. How, if at all, would this development affect the two curves (IS and MP, or IS and LM)? Explain your reasoning.
3. Suppose that after this change in the monetary policy rule, firms become more optimistic about the profitability of investment projects, so investment demand at a given real interest rate is higher than before. How, if at all, does this change affect the real interest rate and output in the short run? For each variable (r and Y), is the effect larger than before the change in the rule, smaller, the same, or is it impossible to tell?

$Answer: $

#### Shocks Requiring Stabilization

$7.$ Describe how, if at all, each of the following developments affects real output, the exchange rate, and net exports in the short run. Assume the central bank is following an interest rate rule.

>1. The discovery of new investment opportunities causes investment demand to be higher at a given interest rate than before.
2. The central bank changes its monetary policy rule so that it sets a lower real interest rate at a given level of output than before.
3. The demand for money increases (that is, consumers’ preferences change so that at a given level of i and Y they want to hold more real balances than before).

$Answer: $

#### Real Business Cycles

$8.$ Consider our usual IS-MP-IA model, starting in long-run equilibrium. Suppose that potential output falls because of reduced productivity.
>1. How, if at all, would this change show up in the IS-MP diagram in the short run?
2. What will be the impact of the fall in   on output and inflation in the long run?

$Answer: $

#### Econometrics

$9.$ Explain in a few sentences, without using any math, what is wrong with the following argument: “I obtained annual data on money growth and output growth, and then estimated the OLS regression Δ ln Y = a + b Δ ln M + u. After running the regression, I computed the correlation between money growth and the regression residual. It was exactly zero. Thus, since there is no correlation between the right-hand side variable and the residual, I know that my regression does not suffer from omitted-variable bias.

$Answer: $

## Note
> The next few sections (we can shorten them since they're pretty repetitive) would be a good place to incorporate sliders like in problem set 3 

#### Monetary Policy
$10.$ Write a function `inflation()` that takes as parameters natural unemployment rate, current expected inflation, years passsed `t`, and a Phillips Curve slope parameter. Your function should return inflation based on the parameters. Suppose that the Federal Reserve has a target $\mu_0$ for the unemployment rate and a target $\pi*t$ for the inflation rate. Suppose the economy's Phillips Curve is given by:
<h5><center>$\pi = E(\pi) + \beta (\mu^* − \mu)$</center></h5>



{:.input_area}
```python
def inflation(u_rate, exp_inf, pc, t):
    return ...
```


#### Monetary Policy
1. If the target for the inflation rate is 4% and the target for the unemployment rate is 6%, what will inflation and unemployment be this year?
2. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra two percentage points?
3. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra half a percentage point?
4. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra percentage point?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 10%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.

1. Suppose that from this year forward the Federal Reserve sets its target for the inflation rate at 3% and its target for the unemployment rate at 5%, what will inflation and unemployment be this year?
2. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be next year?
3. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be two years from now?
4. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be five years from now?
5. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be ten years from now?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra two percentage points above its target level.

1. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
2. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 6%, what will the long run rate of inflation be?
3. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
4. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 8%, what will the long run rate of inflation be?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 2%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target ut for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.
1. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be?
2. If the target for the inflation rate is 3% and the target for the unemployment rate is 4%, what will inflation and unemployment be? 
3. If the target for the inflation rate is 6% and the target for the unemployment rate is 8%, what will inflation and unemployment be? 4. If the target for the inflation rate is 4% and the target for the unemployment rate is 4%, what will inflation and unemployment be?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 10%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target ut for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.

1. Suppose that from this year forward the Federal Reserve sets its target for the inflation rate at 2% and its target for the unemployment rate at 4%, what will inflation and unemployment be this year?
2. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be next year?
3. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be two years from now?
4. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be five years from now?
5. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be ten years from now?

## Chapter 17: The Liquidity Trap
> Keep as is

#### DeLong and Summers (1992)

$1.$ The fact that the central bank cannot push the short-term nominal interest rate below zero raises the possibility of a liquidity trap—an inability of the central bank to push the long-term real interest rate down to a level that produces enough investment to get full employment. Back in 1992 Brad DeLong and Larry Summers argued that this made it desirable for the Federal Reserve to have an inflation target of 4-5% per year rather than 1-2% per year: the higher inflation target, you see, would give the Federal Reserve more ability to reduce the long-term real interest rate when necessary. The Fed didn’t think much of this argument. What do you think of it?

$Answer: $

## Chapter 18: The Government Debt
> Go into textbook to find a topic or two we could test them on, or even just a diagram to include for educational purposes

## Chapter 19: Secular Stagnation
> Probably keep as is.

#### Secular Stagnation

$1.$ The three “coping mechanisms” that Reich argues middle class families used to deal with stagnating incomes included all of the following except:

1. Women move into paid work.
2. Everyone works longer hours.
3. Families stop investing in their children’s education. d. We draw down savings and borrow to the hilt.

$Answer: $

## Chapter 20: The Short Run Shapes the Long Run: "Hysteresis"

#### A Fluctuating Natural Rate of Unemployment

Begin with our very simple Phillips Curve: 

> $\pi = E(\pi) + \beta (\mu^* − \mu)$

with simple adaptive expectations:

> $E(\pi) = \pi − 1$

But add a difference: the natural rate of unemployment depends on what unemployment was last year:

> $\mu^* = (1−\theta)\mu^*−1 +\theta\mu−1$

for some parameter θ between zero and one. 

Suppose that the central bank induces a recession and raises the unemployment rate one percentage point above its natural rate for one year, and then lets unemployment fall back to its natural rate:

1. What is the time path of inflation as a result of this one-year shift in policy? 
2. What is the time path of unemployment?
3. How does the Sacrifice Ratio—the amount of excess point-years of unemployment that must be run in order to permanently reduce the inflation rate by one percent—depend on the parameter θ? 
4. What actions can you think of that the central bank might take that could reduce the value of θ?

#### Supply Shocks

Suppose that a supply shock hits the economy—that is, that for one year the Phillips curve is not:

> $\pi = E(\pi) + \beta(\mu^*− \mu)$

But is instead:

> $\pi = E(\pi) + \beta(\mu^*− \mu)+ s$

where st is some positive shock to inflation caused by, say, a spike in oil prices. And
suppose that inflation expectations are adaptive:

> $E(\pi) = \pi−1$

1. What happens to inflation over time if the central bank keeps unemployment at its natural rate always? 
2. What happens to the unemployment rate over time if the central bank adjusts unemployment to keep inflation at its initial value π0 always?

#### Permanent Unemployment Shocks

Suppose we have our standard Phillips curve: 

> $\pi = E(\pi) + \beta(\mu^*− \mu)$

with our standard adaptive inflation expectations: 

> $E(\pi) = \pi−1$

But that the natural rate of unemployment u' is subject to hysteresis: 

> $\mu^* = \mu − 1$

How is this situation is different from that of a constant natural rate of unemployment combined with static inflation expectations?

#### The Computer Revolution and the Natural Rate of Unemployment

In the late 1990s Alan Greenspan argued that the natural rate of unemployment in the U.S. had temporarily fallen because of the acceleration of productivity growth. Briefly, outline a model of worker behavior in which this claim of Alan Greenspan’s is true, and outline a model of worker behavior in which this claim of Alan Greenspan’s would have been false. Keep your answer to whatever equations you find necessary and to less than 300 words (and a couple of figures).

#### European Unemployment

Explain—to somebody who has never taken an economics course—the reasons you think that western European unemployment today is so much higher than western European unemployment was back in the 1960s.

#### The Japanese Slowdown

Explain—to somebody who has never taken an economics course—the reasons that you think economic growth in Japan slowed from 4.5% over 1973-1991 to less than 1.5% over 1991-present. Keep your answer to less than 300 words (and a couple of figures).

#### Hysteresis

When economists speak of hysteresis, they refer to the fact that:

1. Once a recession starts, it is likely to last for a while.
2. High unemployment tends to be followed by low unemployment.
3. Prolonged high unemployment can cause the natural rate of unemployment to rise.
4. Prolonged high unemployment will eventually reduce inflation.

## Chapter 21: International Economic Policy

#### Speculative Attacks

Explain—to somebody who has never taken an economics course—why a loss of confidence in the value of a country’s currency on the part of foreign exchange speculators is highly likely to lead to a fall in the rate of investment even if no financial crisis is created. Keep your answer to less than 150 words (and a figure or two).

#### Foreign Monetary Policy

Suppose that many foreign central banks tighten their monetary policies, so that real interest rates abroad rise.

1. How would you expect this change to affect the CF(r) function in the United States? Why?
2. How would the change affect output and the real interest rate in the short run? Explain.
3. How would the change affect net exports, and the real exchange rate in the short run? Explain. 

#### Flexible Price World Foreign Exchange Crises

Start out with our consensus flexible-price model in “difference” form, the relevant parts of which are:

>ΔY = ΔC + ΔI + ΔG + ΔX − ΔIM    
ΔC = Cy x (1−t)(ΔY)  
ΔI = ΔI0 − Ir(Δr)   
ΔX = Xε(Δε)   
Δε = Δε0 − εr(Δr)

and let’s consider the effect of a collapse of confidence in the currency—a large sudden € rise in the Δε0 parameter that governs long-term expectations of the price of foreign currency. 

Suppose that there are no effects on the supply side—ΔY=0—no effects on investor confidence—ΔI0=0—no effects on imports—ΔIM=0—and that government spending is unchanged as well—ΔG=0.

1. In the flexible price model, solve for the equilibrium changes in the exchange rate ε, in the interest rate r, in investment I, and in exports X as a result of the rise in
Δε0.
2. Suppose that the cause of the crisis is that government spending is rising rapidly and that investors have no confidence that the budget will ever be balanced, and thus that the government bonds they own will ever be repaid without inflation. Thus there is a relationship between government spending and the change in expectations of the exchange rate: Δε0 = θΔG for some value of the parameter θ. Now solve for the equilibrium changes in the exchange rate ε, in the interest rate r, in investment I, and in exports X as a result of the rise government spending G.
€
ΔY =ΔC+ΔI+ΔG+ΔX −ΔIM ΔC = Cy (1− t)ΔY
ΔI=ΔI0 −IrΔr−Iε(Δε)2 ΔX = XεΔε
ΔIM = −IMyΔY Δε=Δε0 −εrΔr

#### Sticky Price  Price World Foreign Exchange Crises

Now let’s turn to the consensus sticky-price model, the relevant parts of which are:

>ΔY = ΔC + ΔI + ΔG + ΔX − ΔIM    
ΔC = Cy x (1−t)(ΔY)  
ΔI = ΔI0 − Ir(Δr) - Iε(Δε)^2   
ΔX = Xε(Δε)   
ΔIM = −IMy(ΔY)   
Δε = Δε0 − εr(Δr)

and once again consider the effect of a collapse of confidence in the currency—a large sudden rise in the Δε0 parameter that governs long-term expectations of the price of foreign currency—this time in the short run in which full employment is not guaranteed, and in which the real interest rate r is chosen by the central bank. And not the extra term in the investment equation: a large shift in the exchange rate causes massive bankruptcies, destabilizes the financial system, and causes investment I to collapse and output Y to fall.

1. Solve for the change in the exchange rate as a function of the change in the interest rate r, and then turn that around: if the change in the exchange rate is going to take on a certain value Δε, what must the change in the interest rate Δr be?
2. Now let’s view the central bank as choosing not the interest rate but the exchange rate. In this model, solve for the change in output ΔY as a function of the change in the exchange rate Δε (taking account of the fact that the central bank must choose the change in the interest rate Δr to make the change in the exchange rate equal to the chosen value.
3. What is the best that the central bank can do in the short run. Where should it choose to set the exchange rate and the interest rate (bearing in mind that they are linked) to make the effects of the crisis as small as possible?
4. Suppose that the IMF is on hand to help, and to give the central bank extra foreign exchange R that it can then spend to affect the exchange rate: Δε = Δε0 −εr(Δr) −εr(ΔR). Solve for how the best the central bank can do is affected by the addition of more help from the IMF.
