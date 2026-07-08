ch1
- academia vs industry vary largely in different stakeholder requirements, computational priority, capital, data properties, and interpretability requirements
- studying algs is such a small piece of the puzzle relative to the big picture, which includes deployment, observability/monitoring, maintenance, infra, data stack, etc

ch2 
- hierarchical classification is useful for high cardinality problems (large number of classes)
- multilabel stuff, there is a section in [[ml fundamentals]] on this
- multi-objective ML can benefit from 1 model per loss and combine model results instead of combining loss first and then 1 model
	- ie. if you want to filter NSFW and bad quality posts, 1 model per each and combine results with coefficients instead of combine loss
	- maintain modularity essentially
- ML is only useful if it moves the needle on some business metric. everything is ultimately business, needs careful translation
- highly iterative process
- question of data vs mind (algorithms). i feel like data wins has to contain patterns to be picked up on and represent enough of everything that has to be learned yk