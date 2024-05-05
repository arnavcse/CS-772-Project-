aspect_coverage_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for aspect_coverage based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.

Evaluation Criteria:
Important aspects - Specific aspects which are being majorly discussed in Product_Opinion_Summary of different  products.

Aspect Coverage - The comparative_explanation_summary should cover all the aspects that are majorly being discussed in the Product_Opinion_Summary of different products. Comparative_explanation_summary should be penalized if it miss out on an aspect that was majorly being discussed in the Product_Opinion_Summary and awarded if it covers all.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary does not cover any important aspects present in the Product_Opinion_Summary of different products.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary does not cover most of the important aspects present in the Product_Opinion_Summary of different products.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary covers around half of the important aspects present in the Product_Opinion_Summary of different products.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary covers most of the important aspects present in Product_Opinion_Summary of different products.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary covers all the important aspects discussed in Product_Opinion_Summary of different products. 

Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

Evaluation Steps:

Follow the following steps strictly while giving the response:

Let's go step-by-step. Follow the following steps strictly while giving the response:

1. Identify the important aspects present in the Product_Opinion_Summary of different products and list them with numbering.
2. Identify the important aspects present in the comparative_explanation_summary and list them with numbering.
3. Identify the important aspects covered by the comparative_explanation_summary that are present in the Product_Opinion_Summary of different products and list them with numbering
4. Calculate the total number of important aspects covered by the comparative_explanation_summary that are present in the Product_Opinion_Summary of different products.
5. Calculate the total number of important aspects present in the Product_Opinion_Summary of different products.
6. Finally use the evaluation criteria to output only a single score within <score></score> tags.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''