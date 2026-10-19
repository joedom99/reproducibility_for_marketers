# Reproducibility, Replicability, and Generalizability for Marketers

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joedom99/reproducibility_for_marketers/blob/main/reproducibility_for_marketers.ipynb)
![Python](https://img.shields.io/badge/python-3.12%20%7C%203.13-blue)
![statsmodels](https://img.shields.io/badge/statsmodels-0.15-informational)
![scikit--learn](https://img.shields.io/badge/scikit--learn-1.9-orange)
![Data](https://img.shields.io/badge/data-simulated-lightgrey)

Companion notebook for the Marketing Data Science article **"Reproducibility, Replicability, and Generalizability in Digital Marketing Analytics."**

## What This Is

A hands-on walkthrough of three tests every marketing number should pass, using one simple model: an ordinary least squares regression of weekly sales on paid search, social, and email spend.

The data is simulated. I set the true effects myself (paid search 2.0, social 1.2, and email 3.0 per 1,000 dollars of spend), so every test can be checked against the right answer.

## What's Inside

| File | Description |
| --- | --- |
| `reproducibility_for_marketers.ipynb` | The notebook, with all outputs saved |
| `figures/` | The five figures used in the article |
| `requirements.txt` | Minimum package versions, plus the three tested environments |

The notebook covers:

1. **Reproducibility.** Seeded vs. unseeded reruns, result fingerprints, and the same model fit with statsmodels, scikit-learn, and NumPy.
2. **Replicability.** The lucky train/test split, then the same analysis on new data, five times and then 200 times.
3. **Generalizability.** A market shift that a random split hides and a forward split exposes, plus a leakage example.
4. **Reproduced but wrong.** A model without seasonality that passes every consistency check and is still wrong.

## Key Results

- **Repeatability:** five unseeded runs gave five different search estimates; five seeded runs gave one.
- **Reproducibility:** three independent tools agree to within about 1e-13.
- **Robustness:** the same model scored a test MAE anywhere from 6.4 to 13.5 depending only on which weeks were held out.
- **Replicability:** across 200 new datasets, the search estimate averaged 2.01, and 96% of the 95% confidence intervals covered the true value.
- **Generalizability:** after a market shift, test error was 12.5 with a random split and 21.9 with a forward split.
- **Leakage:** using same-week orders cut test error from 9.4 to 4.1, with a feature that can't exist at forecast time.
- **Correctness:** without seasonality, every study estimated the search effect at 3.1 to 3.5 instead of 2.0.

The unseeded demonstration in Part 1 is meant to change every run, so those numbers will differ from the ones above. Everything else should match exactly.

## How to Run

**Google Colab (recommended):** click the **Open in Colab** badge, then choose **Runtime > Run all**. No installs are needed; Colab already has every package. The figures are saved to a `figures/` folder in the Colab session, which is cleared when the session ends, so download any you want to keep.

The notebook was tested in three environments, including Google Colab itself, and produced identical results and fingerprints in all three. The versions are listed in `requirements.txt`.

**Locally:**

```bash
pip install -r requirements.txt
jupyter notebook reproducibility_for_marketers.ipynb
```

## Related Articles

- [Introducing the Marketing Analytics Credibility Model (MACM)](https://blog.marketingdatascience.ai/introducing-the-marketing-analytics-credibility-model-macm-0700dea3c08e)
- [The Same Answer, Ten Different Explanations: Non-Determinism in Generative AI Search](https://blog.marketingdatascience.ai/the-same-answer-ten-different-explanations-non-determinism-in-generative-ai-search-e976d5be6e52)
- [A Practical Guide to Measuring Text Similarity](https://blog.marketingdatascience.ai/a-practical-guide-to-measuring-text-similarity-b770848ce48f)
- [How Similar Are AI-Generated Answers?](https://blog.marketingdatascience.ai/how-similar-are-ai-generated-answers-61b74807abfe)

## Author

**Joe Domaleski**, Country Fried Creative | [Marketing Data Science](https://blog.marketingdatascience.ai/)
