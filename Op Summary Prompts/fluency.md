fluency_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.

Evaluation Criteria:

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary is all garbled and does not make any sense.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary has grammatical errors that make it hard to understand or sound unnatural.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary has errors that affect the clarity or smoothness of the text, but the main points are still comprehensible.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary has very few errors, but it is easy to read, follow and comprehend.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary is extremely fluent and easy to read, follow and comprehend.

Metric:

Fluency - The quality of the summary in terms of grammar, spelling, punctuation, capitalization, word choice, and sentence structure should contain no errors. The summary should be easy to read, follow, comprehend, and contain no errors.

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
2. Go through each sentence and give a step-by-step explanation if the summary adheres to the metric considering the provided information as the input or list down if there are any fluency problems. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''