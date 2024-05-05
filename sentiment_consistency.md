sentiment_consistency_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for sentiment_consistency based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.


Evaluation Criteria:

Majority sentiment: Sentiment of majority of the users corresponding to an aspect - very positive, positive, neutral, negative and very negative.

Sentiment Consistency - All the aspects being discussed in the summary should accurately reflect the consensus sentiment of the corresponding aspects from the reviews. Summaries should be penalized if they do not cover accurately the sentiment regarding any aspect within the summary.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and none of the aspects present in summary have the same majority sentiment as in query, product_title, base_price, final_price, Product_Opinion_Summary.
<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and very few of the aspects present in summary have the same majority sentiment as in query, product_title, base_price, final_price, Product_Opinion_Summary.
<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and only around half of the aspects present in summary have the same majority sentiment as in query, product_title, base_price, final_price, Product_Opinion_Summary.
<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and most of the aspects present in summary have the same majority sentiment as in query, product_title, base_price, final_price, Product_Opinion_Summary.
<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information and all aspects present in summary have the same majority sentiment as in query, product_title, base_price, final_price, Product_Opinion_Summary.



Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

Evaluation Steps:

1. First, write down the steps needed to evaluate the comparative_explanation_summary as per the metric. 
2. Identify the aspects and their sentiment present in the comparative_explanation_summary and list them with numbering.
3. For the list of aspects identified, identify the majority sentiment from the base_price, final_price, Product_Opinion_Summary of three different products and list them with numbering.
4. Next identify how many aspect and sentiment match between base_price, final_price, Product_Opinion_Summary of three different products and comparative_explanation_summary from above and list them with numbering.
5. Finally, use the previous information to rate the comparative_explanation_summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''