# RAAI-SGC: Recursive Agentic AI for Semantic Graph Construction

This repository contains a Jupyter/Colab notebook for building and evaluating semantic graphs from Wikipedia concepts. The notebook starts from seed terms such as **Artificial intelligence**, **Machine learning**, and **Deep learning**, recursively collects related concepts, builds graph variants, and compares them using graph and statistical metrics.

## What It Does

The notebook implements two related semantic graph construction experiments:

- **Agentic relation labeling** using Gemini to infer short semantic relationship labels between linked Wikipedia entities.
- **Weighted semantic graph construction** using recursive Wikipedia scraping, noun keyword extraction, Markov transition probabilities, TF-IDF scores, and combined edge weights.

It evaluates generated graphs against baseline approaches using:

- Node and edge counts
- Edge density
- Clustering coefficient
- Information entropy
- Average edge weight and weight standard deviation
- Semantic reachability
- Paired t-tests

The notebook also generates publication-style visualizations for graph comparison, metrics, reachability, significance, and system architecture.

## Project Files

```text
.
├── Recursive_Agentic_AI_for_Semantic_Graph_Construction (2).ipynb
└── README.md
```

Running the notebook may create output files such as:

```text
raai_sgc_results.json
fig1_architecture.png
fig2_graph_grid.png
fig3_metrics_bar.png
fig4_pvalue_heatmap.png
fig5_reachability.png
```

File names may vary slightly between notebook cells because some figure-generation cells were revised during development.

## Requirements

The notebook is designed for Python 3 and works well in Google Colab.

Main dependencies:

- `google-generativeai`
- `wikipedia`
- `networkx`
- `scipy`
- `scikit-learn`
- `matplotlib`
- `nltk`
- `numpy`

The notebook includes `pip install` cells for these packages.

## Setup

1. Open the notebook in Jupyter or Google Colab.

2. Install dependencies by running the setup cells:

   ```python
   !pip install google-generativeai wikipedia networkx scipy
   !pip install wikipedia networkx scipy scikit-learn matplotlib nltk
   ```

3. If using the Gemini-based relation labeling section, add your Gemini API key:

   ```python
   API_KEY = "YOUR_GEMINI_API_KEY"
   ```

   Do not commit a real API key to version control. Prefer using Colab secrets or environment variables for private keys.

4. Run the notebook cells in order.

## Workflow

The main workflow is:

1. Start with one or more seed terms.
2. Fetch Wikipedia definitions and related concepts.
3. Extract candidate semantic keywords from definitions.
4. Build baseline, Markov, TF-IDF, and combined weighted graphs.
5. Compute graph metrics and statistical comparisons.
6. Generate JSON results and visualization figures.

## Methods Compared

| Method | Description |
| --- | --- |
| Baseline | Uses uniform edge weights. |
| Markov | Uses transition probabilities between discovered concepts. |
| TF-IDF | Uses term importance scores from concept definitions. |
| Combined | Combines Markov transition strength with TF-IDF importance. |
| Agentic/Gemini | Uses Gemini to infer natural-language semantic relation labels. |

## Outputs

The notebook can produce:

- `raai_sgc_results.json` containing metrics, t-test results, and reachability summaries.
- Graph comparison grids across methods and seed terms.
- Entropy and edge-weight variation bar charts.
- P-value significance heatmaps.
- Semantic reachability charts.
- System architecture diagrams.

## Notes

- Wikipedia results can vary over time, so exact graph structure and metrics may change between runs.
- Gemini outputs are model-generated and may vary across executions.
- Some statistical scoring in the early Gemini-labeling section uses simulated scores; review and adapt that section before using it as formal experimental evidence.
- The notebook is research-oriented and currently optimized for experimentation rather than packaging as a reusable Python library.

