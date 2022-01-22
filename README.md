# Hedging-Code
Code to reproduce the following issue:
My linear mixed model for agricultural data was created to account for unequal variance in groups (varieties) using the command ```weights = varIdent``` from  nlme. The command ```lsmeans``` is showing standard errors that do not align with significant differences. 
Example of my code below:

```library(nlme)```

```library(multcomp)```

```library(emmeans)```

```model <- lme(variable ~ cultivar*year, random = ~1|block, weights = varIdent(form = ~1|cultivar),  method = "REML", na.action=na.omit, data = ag.data)```

```Leastsquare <- lsmeans(model,"cultivar")```

```cld(Leastsquare, Letters = letters)```

output:
```
 cultivar  lsmean     SE df lower.CL upper.CL .group
 Golden      6.92  3.841  1    -41.9     55.7  a    
 Campfield  10.33  4.330  1    -44.7     65.4  a    
 Tom        17.50  0.167  1     15.4     19.6  a    
 Harrison   25.67 12.649  1   -135.1    186.4  ab   
 Puget      30.58 20.502  1   -229.9    291.1  ab   
 HVC        37.08  5.331  1    -30.7    104.8   b   
 COL        38.08  0.433  1     32.6     43.6   b   
 Brown      62.67 20.207  1   -194.1    319.4  ab   
```

How can it be that the the cultivar "brown" is not significantly different from "golden"? Is this acceptable / has anyone seen results similar to this?
