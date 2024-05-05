relevance_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for relevance based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.



Evaluation Criteria:

Relevance - Selection of important  information from the set  query, product_title, base_price, final_price, Product_Opinion_Summary. The comparative_explanation_summary should include only important opinions from the reviews. comparative_explanation_summary should not contain redundancies and excess information.

<score>1</score> - The summary misses all the important opinions majorly discussed in the query, product_title, base_price, final_price, Product_Opinion_Summary.
<score>2</score> - The summary misses most of the important opinions majorly discussed in the query, product_title, base_price, final_price, Product_Opinion_Summary or mostly has redundant/excess/unimportant details.
<score>3</score> - The summary covers around half of the important opinions majorly discussed in the query, product_title, base_price, final_price, Product_Opinion_Summary or contains redundant/excess/unimportant details.
<score>4</score> - The summary covers most of the important opinions majorly discussed in the query, product_title, base_price, final_price, Product_Opinion_Summary and has very less amount of redundant/excess/unimportant details.
<score>5</score> - The summary covers all the important opinions majorly discussed in the query, product_title, base_price, final_price, Product_Opinion_Summary and has no redundant/excess/unimportant details.

Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

Evaluation Steps:

1. First, write down the steps needed to evaluate the comparative_explanation_summary as per the metric. 
2. Identify all the essential information from the set query, product_title, base_price, final_price, Product_Opinion_Summary corresponding to three different products. List them with numbering.
3. Identify the important opinions present in the comparative_explanation_summary and all the essential information from the set query, product_title, base_price, final_price, Product_Opinion_Summary. List them with numbering.
4. Next, identify how many important opinions are present in both the comparative_explanation_summary and the set query, product_title, base_price, final_price, Product_Opinion_Summary and how much important information from the set query, product_title, base_price, final_price, Product_Opinion_Summary is present in the comparative_explanation_summary and then list them with numbering.
5. Next, identify how many redundant/excess/unimportant details the comparative_explanation_summary has and list them with numbering.
6. Finally, use the previous information to rate the comparative_explanation_summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''

