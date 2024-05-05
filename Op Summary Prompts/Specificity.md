specificity_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.


Evaluation Criteria:

Generic Opinion example: The battery is good.
Specific Opinion example: The battery lasts for more than 12 hours on a single charge.

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and all the information and opinions presented in the summary are generic.
<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and most of the information and opinions presented are generic.
<score>3</score> - The metric is followed reasonably while generating the summary from the provided information, and only around half of the information and the opinions presented are specific.
<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and most of the information and opinions presented in the summary are specific. Very few information and opinions are generic.
<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and all the information and opinions presented in the summary are specific 

Metric:

Specificity - The summary should avoid containing generic information and opinions. All the information and opinions within the summary should contain detailed and specific information about the product and the consensus of the views. Summaries should be penalized for missing details and awarded if they are specific and cover the details.

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
2. Go through the summary and list down all the information and opinions presented. Classify each piece of information and opinion as specific or generic. Stick to the metric only for evaluation.
3. Finally, use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''