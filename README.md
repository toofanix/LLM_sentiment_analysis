# LLM_sentiment_analysis
## Repos to test LLMs for sentiment analysis
The repo contains works where various small LLMs are compared for sentiment analysis.

The dataset used for the comparison is the FinancialPhrasebank that is available from HuggingFace.

 - https://huggingface.co/datasets/financial_phrasebank
 - The data contains a short sentence, and a label `positive, negative or neutral` that was provided by human user.

The performance of the LLMs in terms of their ability to predict the label correctly is accessed. The model performance is done out-of-box (zero shot) and after fine-tuning.

Models compared:

1. Gemma-2b (base model)
2. Gemma-2b-it (instruction tuned)
3. Gemma-7b (base model)
4. Gemma-7b-it (instruction tuned)
5. Mistral-7B-instruct-v0.2
6. Phi-2

Few takeaways from testing the models above:

1. Out-of-box (zero shot) the models have a decent performance (~0.52 to 0.65).
2. The fine-tuned models perform significantly better (~0.84 to 0.89).
3. Different base models performance differently on the 3 classes. For example: `Gemma-2b-base` has an accuracy of 0.59 on class 2, but `Gemma-2b-it` performs worse at 0.173 on class 2. Seems, like if using a base model, different models should be tested before settling on the the one that works best for the task.
4. The 7b paramters models (zero-shot and finetuned) perform better than the smaller models. The exception here is Phi-2 that performed similar to a 7b model out-of-box even though it is a smaller model.