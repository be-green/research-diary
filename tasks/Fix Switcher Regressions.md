We need model regressions where the outcome is an indicator for whether you switched jobs at any time in the years following a shock. 

I can't remember if this is just the 1 period exit probability, or the probability of exit over the next 5 years is the problem...

In addition, I don't think I can just compute things the same way I do with wage growth. It's possible following some of these shocks that the indicator switches from 1 under no shock to 0 under the shock, so the outcome variable would be -1. I don't know if that reasonably corresponds to a regression outcome. Maybe it does? Consider

$$E(switch_0 - switch_1)$$
where $switch_0$ corresponds to whether or not you switch given the shock and $switch_1$ corresponds to whether you switch given no shock. Then actually I think this is kind of fine...so yeah maybe I need to do this.