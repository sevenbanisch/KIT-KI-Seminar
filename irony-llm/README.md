# "Beat the Bot": Irony Detection with LLMs

This project explores whether Large Language Models (LLMs) can annotate irony in online comments in a way that is comparable to human annotators.

Starting from a curated dataset of comments, we:

- collect human irony and confidence ratings,
- generate repeated LLM annotations for the same comments,
- evaluate consistency and agreement within each group, and
- compare human and LLM judgments side by side.

The repository contains multiple Jupyter notebooks for more detailed analysis, reliability checks, and human-vs-LLM comparison.

## Project Structure

```txt
irony-llm/
├── dataset.csv
├── generate_llm_annotations.ipynb
├── evaluate_llm_annotations.ipynb
├── evaluate_human_annotations.ipynb
├── compare_human_llm_annotations.ipynb
├── outputs/
│   ├── human_annotations.csv
│   ├── clean/
│   │   ├── human_comment_stats.csv
│   │   └── llm_comment_stats.csv
│   ├── figures/
│   │   ├── comparison/
│   │   ├── human/
│   │   └── llm/
│   └── llm_raw/
│       ├── iteration_01.json
│       ├── iteration_02.json
│       ├── ...
│       └── iteration_09.json
└── README.md
```

## Notebooks

### `generate_llm_annotations.ipynb`

Runs the LLM-based annotation pipeline on `dataset.csv`.

- Reads the comment dataset
- Uses the OpenAI API to score irony and confidence
- Repeats the annotation multiple times to capture LLM variability
- Saves raw outputs to `outputs/llm_raw/`

### `evaluate_llm_annotations.ipynb`

Processes the raw LLM outputs and summarizes them quantitatively.

- Aggregates repeated LLM runs
- Computes mean, variance, and standard deviation per comment
- Evaluates reliability and agreement metrics such as Cronbach's alpha and Krippendorff's alpha
- Writes cleaned results to `outputs/clean/llm_comment_stats.csv`
- Generates figures in `outputs/figures/llm/`

### `evaluate_human_annotations.ipynb`

Analyzes the human annotation results stored in `outputs/human_annotations.csv`.

- Extracts irony and confidence ratings from the survey export
- Computes descriptive statistics and agreement metrics
- Writes cleaned results to `outputs/clean/human_comment_stats.csv`
- Generates figures in `outputs/figures/human/`

### `compare_human_llm_annotations.ipynb`

Compares aggregated human and LLM annotations directly.

- Loads the cleaned outputs from both evaluation notebooks
- Visualizes agreement and disagreement between humans and the model
- Saves comparison plots to `outputs/figures/comparison/`

## Data and Outputs

### Input data

- `dataset.csv`: source dataset containing thread titles and comments to annotate
- `outputs/human_annotations.csv`: raw human annotation export

### Generated outputs

- `outputs/llm_raw/`: raw JSON responses from repeated LLM annotation runs
- `outputs/clean/`: aggregated comment-level statistics for human and LLM annotations
- `outputs/figures/`: plots for human-only, LLM-only, and comparative analysis

## Typical Workflow

1. Add or update comments in `dataset.csv`.
2. Run `generate_llm_annotations.ipynb` to create repeated LLM annotations.
3. Run `evaluate_llm_annotations.ipynb` to aggregate and analyze LLM results.
4. Run `evaluate_human_annotations.ipynb` to analyze the human annotations.
5. Run `compare_human_llm_annotations.ipynb` for side-by-side comparison.

## Requirements

To run the LLM annotation notebook, the environment variable `OPENAI_API_KEY` must be set.
