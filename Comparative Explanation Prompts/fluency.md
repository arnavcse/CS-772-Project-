fluency_prompt_template = """
Task Description:
Your task is to evaluate and rate the comparative_explanation_summary for fluency based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly.

Evaluation Criteria:
Fluency : The quality of summary in terms of grammar, spelling, punctuation, capitalization, word choice, and sentence structure and should contain no errors. The summary should be easy to read, follow, comprehend and should contain no errors.
Following are the scores and the evaluation criteria according to which scores must be assigned.
<score>1</score> - The summary is all garbled and does not make any sense.
<score>2</score> - The summary has grammatical errors that make it hard to understand or sound unnatural.
<score>3</score> - The summary has errors that affect the clarity or smoothness of the text, but the main points are still comprehensible.
<score>4</score> - The summary has very few errors, but it is easy to read, follow and comprehend.
<score>5</score> - The summary is extremely fluent and is easy to read, follow and comprehend.Metric:

Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

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
"""