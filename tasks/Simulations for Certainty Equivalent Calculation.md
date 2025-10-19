---
tags:
  - kb-note
  - innovation-paper
---
We need to measure the certainty equivalent associated with a willingness to pay for a single innovation shock. The proposal is that we want the willingness to pay for hedging a single year of shocks based on their impact over 5 years.

We have that

$$u(w, z, e^*) = u(wz^{1 + \frac{1}{\rho}}- c(e^*)^{\frac{1}{\rho}}) = u\left(\frac{\rho}{1 + \rho} [wz]^{1 + \frac{1}{\rho}}\right)$$
evaluating this expression, we get

$u(w, z) = \frac{1}{1 - \gamma}\left(\frac{\rho}{1 + \rho} [wz]^{1 + \frac{1}{\rho}}\right)^{1 - \gamma} = \frac{1}{\beta (1 - \gamma)} (wz)^{\beta (1 - \gamma)}$

Note that marginal utility is then

$u^\prime (w, z) = (wz)^{\beta(1- \gamma) - 1}$

which is still a CRRA utility function, but scaled for effort. We want to find a scalar, proportional wage adjustment factor, a, such that

$$\int_0^1 e^{-rt}u(a \times w_0, z_0)dt + E_1\left[\int_1^5  e^{-rt}u(a \times w_t, z_t) dt\right] = E_0\left[\int_0^5 e^{-rs} u(w_s , z_s) ds\right]$$
Since $a$ only shows up for the first year, we can factor it out without considering the expectation. Note that the expectation on the LHS is going to depend on the starting state at $t = 1$, starting at the state $(w_0, z_0, \hat{q}_0)$ while the other takes the same expectation at time $0$. 

> [!NOTE] Taking the stupid road
> Maybe there's some clever math to get those to cancel given a memoryless process, for now I'm just going to simulate both because I'm not sure how to deal with the fact that we have an unknown distribution of states that would start at year 4 for the second term without simulating them. Maybe there's a trick where we can approximate everything with some kind of discrete Markov chain. Putting it aside for now.

We can pull $a$ out of the integral up front, since it is a constant and 

$$\int_0^T e^{-rt}u(a \times w_t, z_t) dt = \int_0^T e^{-rt} \frac{1}{\beta (1 - \gamma)} (aw_tz_t)^{\beta (1 - \gamma)} dt$$
so we can pull out $a^{\beta (1 - \gamma)}$ and get 

$$\int_0^T e^{-rt}u(a \times w_0, z_0) dt = a^{\beta (1 - \gamma)} \int_0^T e^{-rt}u(w_0, z_0) dt$$ so the certainty equivalent we need is just going to come from re-arranging that expression given a starting grid of wages (which are determined by the $\hat{q}$ grid), and $z_0$, which is going to be determined by the Frechet distribution 

$$z_{i, 0} \sim Frechet(T_{\tau(i)}, \theta_{\tau(i)})$$
I'm a bit concerned that the $z_0$ distribution is pretty fat-tailed but it is what it is... In any case, to wrap it all up: 

$$\boxed{a = \left(\frac{E_0\left[\int_0^5 e^{-rt} u(w_t, z_t) dt\right] }{\int_0^1 e^{-rt }u(w_0, z_t)dt + E_1\left[\int_1^5 e^{-rt} u(w_t, z_t) dt\right]}\right)^{\frac{1}{\beta(1 - \gamma)}}}$$

where we are going to evaluate the numerator by simulation.

> [!NOTE] A _slightly_ smarter path!
> Since we have a path that only depends on the state variables at time $0$, we know that the expectation of the first four years of $E_0$ are going to be the same as the first four years of $E_1$, so we can only consider years 0-4. This means that we can simulate a single set of 5-year path, use them to calculate both the 5-year and 4-year expectations, and compute the relevant ratio.

Now we want to compare two scenarios:
1. We want to see how much people would be WTP to double the innovation rate
2. We want to see the same thing, but where they end up sharing the additional growth without risk instead of with risk

The first one is exactly the same as our hedging calculation, but where people get an additional burst of innovation for a single year. The second is a little different, but we can think about it as every person getting a proportional increase in their wages 