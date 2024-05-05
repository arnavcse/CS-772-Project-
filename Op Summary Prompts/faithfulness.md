faithfulness_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.


Evaluation Criteria:

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary is for a different product and is irrelevant/unrelated to the given set of information (product title, description, key features, specifications, reviews and product_ugc_summary).

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary contains very few facts actually verifiable/supported/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary)and contains a lot of hallucinated facts.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary contains more than one piece of information that is not verifiable/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary).

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary contains only one piece of information that is not verifiable/supported/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary).

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and every piece of information present in the summary is verifiable/supported/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary)

 

Metric:

Faithfulness - Every piece of information mentioned in the summary should verifiable/supported/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary)  only. Summaries should be penalized if any piece of information is not verifiable/supported/present/inferred or even if the summary over generalizes something.

Product Information:

Product Title: {product_title}

Description: {description}

Key Features: {key_features}

Specifications: {specifications}

Reviews: {reviews}

Product_Ugc_Summary: {product_ugc_summary}

Summary: {Product_Opinion_Summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through the summary and list down all pieces of information in the summary that is not verifiable/supported/present/inferred from the set of information (product title, description, key features, specifications, reviews and product_ugc_summary)  only. Give a clear step-by-step explanation of what you found.
3. Finally use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''