coherence_prompt_template = '''

Task Description:

Your task is to evaluate and rate the comparative_explanation_summary for coherence based on the provided set of information query, product_title, base_price, final_price, Product_Opinion_Summary. Use the following evaluation criteria to judge the extent to which the metric is followed by the comparative_explanation_summary. Make sure you consider the full set of information to evaluate the comparative_explanation_summary. Understand the task and the subsequent evaluation metric very clearly. The task is to judge the extent to which the summary follows the metric.

Evaluation Criteria:

Coherence - The collective quality of all sentences. The summary should be well-structured and well-organized. The summary should not just be a heap of related information, but should build from sentence to a coherent body of information.
Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary lacks structure and logical flow, resulting in disjointed ideas and significant inconsistencies, making it confusing and challenging to follow.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary attempts coherence but struggles with occasional lapses in logic, clarity issues, and insufficiently connected ideas, leading to a somewhat disjointed presentation.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary displays a reasonable level of coherence with a logical sequence, yet occasional disruptions in flow and clarity, requiring some improvements for a smoother transition between ideas.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary demonstrates strong coherence, maintaining a clear and organized flow with effective transitions and minimal inconsistencies, effectively conveying main points with clarity and precision.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary showcases exceptional coherence with a flawless logical flow, impeccable transitions, and consistent clarity, presenting information in an impeccably organized and easily comprehensible manner.



Query: {query}
Product Titles: {product_titles}
Base Prices: {base_prices}
Final Prices: {final_prices}
Product Opinion Summaries: {product_opinion_summaries}
Comparative Explanation Summary: {comparative_explanation_summary}



Evaluation Steps:

Follow the following steps strictly while giving the response:

1. First, write down the steps needed to evaluate the summary as per the metric. Reiterate what metric you will be using to evaluate the summary.
2. Go through each sentence and check if everything is presented in a clear and logical order. Give a clear step-by-step explanation of what you found and what is lacking. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''