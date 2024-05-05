aspect_coverage_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.

Evaluation Criteria:
Important aspects - Specific aspects which are being majorly discussed in different reviews.

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary does not cover any important aspects present in the reviews.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary does not cover most of the important aspects present in the reviews.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary covers around half of the important aspects present in the reviews.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary covers most of the important aspects present in reviews.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary covers all the important aspects discussed in reviews. 

Metric:

Aspect Coverage - The summary should cover all the aspects that are majorly being discussed in the reviews. Summaries should be penalized if they miss out on an aspect that was majorly being discussed in the reviews and awarded if it covers all.

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
2. Identify the important aspects present in the reviews and list them with numbering.
3. Identify the important aspects present in the summary and list them with numbering.
4. Identify the important aspects covered by the summary that are present in the reviews and list them with numbering.
5. Calculate the total number of important aspects covered by the summary that are present in the reviews.
6. Calculate the total number of important aspects present in the reviews.
7. Finally use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''