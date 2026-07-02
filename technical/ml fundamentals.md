it's funny that I'm writing this but I'm finding that as I read, I'm having to stop to look up many terms that I should have better understandings of by this point but don't. so i'll write them down here to better remember them and review when needed

**regularization**
- strategies used to prevent a model from overfitting to training data by adding a penalty term in the loss 
- main ones are L1 (lasso) and L2 (ridge)
- L1 = drop some weights fully to 0, eliminating some features. this makes models sparser and more interpretable 
- L2 = drop ALL weights to near 0, preventing any single feature from dominating

**logistic regression**
- a model using the sigmoid function for classification
- works by taking a probability (0-1), calculating odds using P / 1-P, (0-inf), taking the natural log of the odds, which makes the bounds of the value (-inf,inf)
- this means we can fit a line to it, so ln(P/1-P) = B0 + B1x1 + B2x2 + ...
- solving for P (since that is what is useful to someone) yields the sigmoid equation
- **the predictor variables and log-odds must be linearly related**, or in other words the predictor variables and outcome odds must NOT be linear, they must follow the sigmoid shape. ie. middle range changes to predictor changes outcome the most
- example: marketing spend vs likelihood to buy. first $0-10 spend, not much increase in chance. middle $10-40, large impact, customer is convinced. final $40-50 doesn't change much again.
- **if this relationship between predictors and outcome is not present, using logistic regression makes no sense**. i think understandings like these are why stats fluency is so important