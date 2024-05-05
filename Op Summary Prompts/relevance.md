relevance_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.



Evaluation Criteria:

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary misses all the important opinions majorly discussed in the reviews and all the essential information from the set  (product title, description, key features, specifications, reviews and product_ugc_summary).
<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary misses most of the important opinions majorly discussed in the reviews or mostly has redundant/excess/unimportant details from the set  (product title, description, key features, specifications, reviews and product_ugc_summary).
<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary covers around half of the important opinions majorly discussed in the reviews or contains redundant/excess/unimportant details from the set  (product title, description, key features, specifications, reviews and product_ugc_summary).
<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary covers most of the important opinions majorly discussed in the reviews and has significantly less amount of redundant/excess/unimportant details from the set  (product title, description, key features, specifications, reviews and product_ugc_summary)
<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information and covers all the important opinions majorly discussed in the reviews and has no redundant/excess/unimportant details from the set  (product title, description, key features, specifications, reviews and product_ugc_summary).

Metric:

Relevance - Selection of important  information from the set  (product title, description, key features, specifications, reviews and product_ugc_summary) . The summary should include only important opinions from the reviews. Summaries should not contain redundancies and excess information.

Product Information:

Product Title: {product_title}

Description: {description}

Key Features: {key_features}

Specifications: {specifications}

Reviews: {reviews}

Product_Ugc_Summary: {product_ugc_summary}

Summary: {Product_Opinion_Summary}

Evaluation Steps:

Let's go step-by-step. Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Identify all the important opinions that are majorly discussed in the reviews and all the essential information from the set (product title, description, key features, specifications, reviews, and product_ugc_summary) corresponding to the product. List them with numbering.
3. Identify the important opinions present in the summary and all the essential information from the set (product title, description, key features, specifications, reviews, and product_ugc_summary). List them with numbering.
4. Next, identify how many important opinions are present in both the summary and reviews and how much important information from the set (product title, description, key features, specifications, reviews, and product_ugc_summary) is present in the summary and then list them with numbering.
5. Next, identify how many redundant/excess/unimportant details the summary has and list them with numbering.
6. Finally, use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''