# Hedging-Code
Code to reproduce the following issue:
My linear mixed model for agricultural data was created to account for unequal variance in groups (varieties) using the command ```weights = varIdent``` from  nlme. The command ```lsmeans``` is showing standard errors that do not align with significant differences. 
