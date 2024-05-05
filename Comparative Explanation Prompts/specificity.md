

specificity_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for specificity based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.


Evaluation Criteria:

Generic Opinion example: The battery is good.
Specific Opinion example: The battery lasts for more than 12 hours on a single charge.

Specificity - The comparative_explanation_summary should avoid containing generic information and opinions. All the information and opinions within the comparative_explanation_summary should contain detailed and specific information about the comparisons of three recommended products. comparative_explanation_summary should be penalized for missing details and awarded if they are specific and cover the details.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and all the information and opinions presented in the summary are generic.
<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and most of the information and opinions presented are generic.
<score>3</score> - The metric is followed reasonably while generating the summary from the provided information, and only around half of the information and the opinions presented are specific.
<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and most of the information and opinions presented in the summary are specific. Very few information and opinions are generic.
<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and all the information and opinions presented in the summary are specific 

Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}

Evaluation Steps:

Let's go step-by-step. Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the comparative_explanation_summary as per the metric. 
2. Go through the comparative_explanation_summary and list down all the information and opinions presented. Classify each piece of information  as specific or generic. Stick to the metric only for evaluation.
3. Finally, use the previous information to rate the comparative_explanation_summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''