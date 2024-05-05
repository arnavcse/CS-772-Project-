faithfulness_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for faithfulness based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.

Evaluation Criteria:

Faithfulness - Every piece of information mentioned in the comparative_explanation_summary  should be verifiable/supported/present/inferred from the set of information query, product_title, base_price, final_price, Product_Opinion_Summary only. comparative_explanation_summary  should be penalized if any piece of information is not verifiable/supported/present/inferred or even if the comparative_explanation_summary  over generalizes something.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary is for a different products and is irrelevant/unrelated to the given set of information (query, product_title, base_price, final_price, Product_Opinion_Summary).

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary contains very few facts actually verifiable/supported/present/inferred from the set of information (query, product_title, base_price, final_price, Product_Opinion_Summary) and contains a lot of hallucinated facts.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary contains more than one piece of information that is not verifiable/present/inferred from the set of information (query, product_title, base_price, final_price, Product_Opinion_Summary).

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary contains only one piece of information that is not verifiable/supported/present/inferred from the set of information (query, product_title, base_price, final_price, Product_Opinion_Summary).

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and every piece of information present in the summary is verifiable/supported/present/inferred from the set of information (query, product_title, base_price, final_price, Product_Opinion_Summary).

 



Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the comparative_explanation_summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through the comparative_explanation_summary and list down all pieces of information in the comparative_explanation_summary that is not verifiable/supported/present/inferred from the set of information query, product_title, base_price, final_price, Product_Opinion_Summary only. Give a clear step-by-step explanation of what you found.
3. Finally use the previous information to rate the comparative_explanation_summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''