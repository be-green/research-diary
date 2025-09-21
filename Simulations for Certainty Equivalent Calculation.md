---
tags:
  - kb-note
  - innovation-paper
---
We need to measure the certainty equivalent associated with a willingness to pay for a single innovation shock. The proposal is that we want the willingness to pay for hedging a single year of shocks based on their impact over 5 years. I told Larry I wasn't sure that was the easiest to explain but I think it's ok to implement.

We have that

$$u(w, z, e^*) = u(wz^{1 + \frac{1}{\rho}}- c(e^*)^{\frac{1}{\rho}}) = u\left(\frac{\rho}{1 + \rho} [wz]^{1 + \frac{1}{\rho}}\right)$$
evaluating this expression, we get

$u(w, z) = \frac{1}{1 - \gamma}\left(\frac{\rho}{1 + \rho} [wz]^{1 + \frac{1}{\rho}}\right)^{1 - \gamma} = \frac{1}{\beta (1 - \gamma)} wz^{\beta (1 - \gamma)}$

Note that marginal utility is then

$u^\prime (w, z) = (wz)^{\beta(1- \gamma) - 1}$

which is still a CRRA utility function, but scaled for effort. We want to find a scalar, proportional wage adjustment factor, a, such that

$$u(a \times w_0, z_0) = E\left[\int_0^1 u(w_t , z_t)\right]$$

the LHS has a constant, which we can factor out, giving us

$$ \int_0^5 e^{-rt} u(a \times w_0, z_0)dt = u(a \times w_0, z_0) \int_0^5 e^{-rt}dt = u(a \times w_0, z_0) \frac{1 - e^{-5r}}{r} $$

When we evaluate the RHS expression, and get some constant $U$ which we have solved for numerically, we can re-arrange so that

$EU = u(a \times w_0, z_0) = \frac{1}{1 - \gamma}\left(\frac{\rho}{1 + \rho} [aw_0z_0]^{1 + \frac{1}{\rho}}\right)^{1 - \gamma} = \frac{1}{(1 - \gamma) \beta} (a w_0 z_0)^{\beta (1 - \gamma)}$

