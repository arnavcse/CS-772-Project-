coherence_prompt_template = '''

Task Description:

You will be given a set of information (product title, description, key features, specifications, reviews and product_ugc_summary) using which a corresponding product opinion summary has been generated. Your task is to evaluate and rate the summary based on the given metric. Evaluate to what extent the summary follows the given metric, considering the provided information as input. Use the following evaluation criteria to judge the extent to which the metric is followed. Make sure you understand the task and the subsequent evaluation metric very clearly.

Evaluation Criteria:

The task is to judge the extent to which the summary follows the metric.

Following are the scores and the evaluation criteria according to which scores must be assigned.

<score>1</score> - The metric is not followed at all while generating the summary from the provided information, and the summary lacks structure and logical flow, resulting in disjointed ideas and significant inconsistencies, making it confusing and challenging to follow.

<score>2</score> - The metric is followed only to a limited extent while generating the summary from the provided information, and the summary attempts coherence but struggles with occasional lapses in logic, clarity issues, and insufficiently connected ideas, leading to a somewhat disjointed presentation.

<score>3</score> - The metric is followed to a reasonable extent while generating the summary from the provided information, and the summary displays a reasonable level of coherence with a logical sequence, yet occasional disruptions in flow and clarity, requiring some improvements for a smoother transition between ideas.

<score>4</score> - The metric is followed mostly while generating the summary from the provided information, and the summary demonstrates strong coherence, maintaining a clear and organized flow with effective transitions and minimal inconsistencies, effectively conveying main points with clarity and precision.

<score>5</score> - The metric is followed thoroughly while generating the summary from the provided information, and the summary showcases exceptional coherence with a flawless logical flow, impeccable transitions, and consistent clarity, presenting information in an impeccably organized and easily comprehensible manner.

Metric:

Coherence - The collective quality of all sentences. The summary should be well-structured and well-organized. The summary should not just be a heap of related information, but should build from sentence to a coherent body of information.

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
2. Go through each sentence and check if everything is presented in a clear and logical order. Give a clear step-by-step explanation of what you found and what is lacking. Stick to the metric only for evaluation.
3. Next, evaluate the extent to which the metric is followed.
4. Use the previous information to rate the summary using the evaluation criteria and assign a score within the <score></score> tags.

Note: Strictly give the score within <score></score> tags only e.g Score- <score>5</score>.

First give a detailed explanation and then finally give a single score following the format: Score- <score>5</score>

THE EVALUATION AND SCORE MUST BE ASSIGNED STRICTLY ACCORDING TO THE METRIC ONLY AND NOTHING ELSE!

Response:

'''