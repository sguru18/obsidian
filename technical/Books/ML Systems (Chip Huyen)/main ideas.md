ch4
- sampling (simple random vs. nonprobability = anything not random and instead based on some criteria ie. stratified, convenience, expert, reservoir sampling is very cool)
	- reservoir samplling is for streaming data: ensure equal probability of choosing the new item without knowing how many items you will see. keep a reservoir of the first k elements, and then generate a random number x from 1 thru n with a running total n. if 1 <= x <= k, replace item x. provably every element has a k/n chance of being in the reservoir
	- importance sampling lets you sample from an unknown/expensive distribution via a known/cheap distribution using the relation b/w the two. ie reward policy output from a new action without going all the way to end of time horizon after new action OR ie. correcting for sample bias using relative populations if you surveyed all younger but know how younger relate to older
- labeling (hand labeling = SLOW and not private, natural labels are convenient and are good to start from)
- data lineage is important, ie. to distinguish quality old data vs less good new data, or see biases
- turning software features ie. reactions into feedback is cool and implicit labels ie. not reacting to a rec and user actions in general as feedback on ML. very easy now to see how facebook can optimize for reactivity lmao so straightforward
- window length refers to how quickly you get user feedback to make a label. ie very quick for a youtube rec or longer for fraud detection. but you probably want some labels quickly to iterate model (stopped on p.126)

ch3
- many data types (user input, user behavior, system logs, internal data like inventory or sales, third party data ie. web habits for a certain demographic group) that can be used
- many formats (CSV, Parquet for column-major to read features easily and binary (smaller and faster to unload bc utilizes cache well without jumping around memory))
- ludwig and h2o autoML are declarative ml systems, declare the inputs and the task and it comes up with a model to use... cool but seems kinda counter, removes all role of a domain expert's intuition and judgement, also does not help with anything else like monitoring or maintenance
- data warehouse = storing structured data, data lake = storing unstructured data
- ACID = atomicity, consistency, isolation, durability
- data can be moved through service (REST, RPC) or real-time transport (message queue or pubsub model)
- stream features = get from rapidly changing data, batch features = computed less frequently in bulk. systems often have both

ch2 
- hierarchical classification is useful for high cardinality problems (large number of classes)
- multilabel stuff, there is a section in [[ml fundamentals]] on this
- multi-objective ML can benefit from 1 model per loss and combine model results instead of combining loss first and then 1 model
	- ie. if you want to filter NSFW and bad quality posts, 1 model per each and combine results with coefficients instead of combine loss
	- maintain modularity essentially
- ML is only useful if it moves the needle on some business metric. everything is ultimately business, needs careful translation
- highly iterative process
- question of data vs mind (algorithms). i feel like data wins has to contain patterns to be picked up on and represent enough of everything that has to be learned yk

ch1
- academia vs industry vary largely in different stakeholder requirements, computational priority, capital, data properties, and interpretability requirements
- studying algs is such a small piece of the puzzle relative to the big picture, which includes deployment, observability/monitoring, maintenance, infra, data stack, etc