# „Beat the Bot“: Irony Detection with LLMs

This project evaluates irony in online comment using a Large Language Model (LLM).  
Given a dataset of discussion threads and comments, the notebook sends each comment to an LLM and asks it to rate the degree of irony and its confidence.

The goal is to explore how well LLMs can perform text annotation tasks that are traditionally done by human annotators. This is a common use case in computational social science and text classification pipelines.

## Structure

```txt
irony_llm
├── data.csv
├── evaluate_irony.ipynb
├── README.md
└── irony_results.json
```

# TODO
- [ ] Embed definitions for irony, irony, etc.?
- [ ] Collect more datapoints (~50)
- [ ] Let humans annotate the same dataset (some sort of ground truth) and compare the results
