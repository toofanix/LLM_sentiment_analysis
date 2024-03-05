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


RESULTS:
```markdown
| Model                         | Zero Shot Accuracy Overall | Zero Shot Accuracy 0 | Zero Shot Accuracy 1 | Zero Shot Accuracy 2 | Fine-Tuned Accuracy Overall | Fine-Tuned Accuracy 0 | Fine-Tuned Accuracy 1 | Fine-Tuned Accuracy 2 |
|-------------------------------|----------------------------|----------------------|----------------------|----------------------|----------------------------|-----------------------|-----------------------|-----------------------|
| gemma-2b-base                 | 0.564                      | 0.747                | 0.357                | 0.590                | 0.847                      | 0.913                 | 0.843                 | 0.783                 |
| gemma-2b-it                   | 0.523                      | 0.907                | 0.490                | 0.173                | 0.871                      | 0.957                 | 0.867                 | 0.790                 |
| gemma-7b-base                 | 0.671                      | 0.773                | 0.337                | 0.903                | 0.873                      | 0.923                 | 0.863                 | 0.833                 |
| gemma-7b-it                   | 0.631                      | 0.803                | 0.193                | 0.897                | 0.886                      | 0.977                 | 0.877                 | 0.803                 |
| Mistral-7b-instruction-v0.2   | 0.607                      | 0.693                | 0.957                | 0.170                | 0.873                      | 0.967                 | 0.893                 | 0.760                 |
| Phi-2                         | 0.652                      | 0.793                | 0.203                | 0.953                | 0.858                      | 0.960                 | 0.793                 | 0.820                 |
```


Few takeaways from testing the models above:

1. Out-of-box (zero shot) the models have a decent performance (~0.52 to 0.65).
2. The fine-tuned models perform significantly better (~0.84 to 0.89).
3. Different base models performance differently on the 3 classes. For example: `Gemma-2b-base` has an accuracy of 0.59 on class 2, but `Gemma-2b-it` performs worse at 0.173 on class 2. Seems, like if using a base model, different models should be tested before settling on the the one that works best for the task.
4. The 7b paramters models (zero-shot and finetuned) perform better than the smaller models. The exception here is Phi-2 that performed similar to a 7b model out-of-box even though it is a smaller model.