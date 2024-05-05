sentiment_consistency_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.


Evaluation Criteria:

Majority sentiment: Sentiment of majority of the users corresponding to an aspect - very positive, positive, neutral, negative and very negative.

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and none of the aspects present in summary have the same majority sentiment as in reviews.
<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and very few of the aspects present in summary have the same majority sentiment as in reviews.
<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and only around half of the aspects present in summary have the same majority sentiment as in reviews.
<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and most of the aspects present in summary have the same majority sentiment as in reviews.
<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information and all aspects present in summary have the same majority sentiment as in reviews.

Metric:

Sentiment Consistency - All the aspects being discussed in the summary should accurately reflect the consensus sentiment of the corresponding aspects from the reviews. Summaries should be penalized if they do not cover accurately the sentiment regarding any aspect within the summary.

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
2. Identify the aspects and their sentiment present in the summary and list them with numbering.
3. For the list of aspects identified, identify the majority sentiment from the reviews and list them with numbering.
4. Next identify how many aspect and sentiment match between reviews and summary from above and list them with numbering.
5. Finally, use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''