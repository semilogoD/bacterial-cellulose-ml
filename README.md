# 🧫 AI-Driven Prediction of Bacterial Cellulose Yield from Sustainable Agricultural Substrates

> **Status: 🚧 Research in progress.** The paper is in preparation for conference proceedings. Code, data and the full results will be released in this repository after publication.

## 📌 Project Overview

Bacterial cellulose (BC) is a high-purity biopolymer used in wound care, drug delivery, food packaging and composite materials. Industrial production is held back by the cost of the growth medium, which relies on glucose, yeast extract and peptone. Agricultural wastes are an attractive low-cost alternative, but finding which wastes (and which combinations) work has traditionally meant testing one variable at a time.

This project explores whether machine learning can help narrow that search. It combines **wet-lab yields from a locally isolated bacterial strain (CL24)** with **yields compiled from the published literature**, builds regression models to predict BC yield, and uses **explainable AI (SHAP)** to understand what those models rely on.

## 🎯 Objectives

* Build one consistent dataset from two differently structured sources (wet-lab measurements and literature records)
* Predict BC yield from substrate, organism and cultivation features
* Evaluate the models with a validation strategy suited to data that come from many independent studies
* Use explainable AI to understand what a model relies on, and to state the limits of that understanding
* Generate hypotheses for future lab work (hypotheses, not confirmed results)

## 🛠 Tools Used

| Area | Tools |
|---|---|
| Language / environment | Python, Jupyter Notebook |
| Data handling | pandas, NumPy |
| Modelling | scikit-learn, XGBoost |
| Explainability | SHAP |
| Visualisation | Matplotlib, Seaborn |

## 🔄 Workflow

```
 Wet-lab yields (strain CL24)          Published literature records
              │                                     │
              └─────────────────┬───────────────────┘
                                ▼
                 Combine into one dataset
                                ▼
              Clean: duplicates · labels · missing values
                                ▼
                    Exploratory data analysis
                                ▼
          Feature engineering + data-leakage audit
                                ▼
                Cross-validated model comparison
                                ▼
                  SHAP explainability analysis
                                ▼
          Candidate conditions as hypotheses for the lab
```

## 🔎 What the Project Found (high level)

*No figures, numbers or charts are reported here. Those will follow with the paper.*

* **In the lab:** several agricultural wastes, used as carbon or nitrogen sources, gave higher yields than their conventional counterparts, and additives raised yield compared with an additive-free control. The benefit depended on the specific waste: not every one outperformed the conventional options.
* **For machine learning:** the models looked useful when tested in the ordinary way, but did not hold up when tested on whole studies they had not seen. Substrate type, organism group and cultivation mode alone were not enough to predict yield in a new study, which points to differences between labs that published papers do not record.
* **For explainability:** the model leaned most on the type of nutrient source or additive and on the organism group, and least on cultivation mode. These are associations the model relied on, not proof of cause.
* **For the lab:** one of the model's top suggestions matched a condition the lab had already tested and found strong, which gives some confidence in the rest, but those remain untested hypotheses.
* **The wider point:** better prediction across studies will need experimental conditions to be reported more fully and consistently.

## 🔒 Data and Code Availability

The dataset combines unpublished wet-lab measurements with records compiled by hand from published papers, so it is not publicly available. The analysis code will be released here after the paper is published. Until then, this README describes the approach and the main findings in words only, with no figures or numbers.

## 🤖 AI Assistance Disclosure

AI tools (Claude, Anthropic) were used for literature search and citation verification, for developing the data-cleaning and machine-learning code, and for language refinement. The experimental work, the research question, the interpretation of results and the conclusions are the authors'. I re-ran the full pipeline myself in Jupyter and worked through the errors that came up.

## 🧠 Skills Demonstrated

* Curating and cleaning heterogeneous data from two differently structured sources
* Choosing and justifying a validation strategy for small, multi-source data
* Comparing regression models fairly with standard error metrics
* Interpreting model behaviour with SHAP and stating its limits honestly
* Reproducing and debugging a machine-learning pipeline in Jupyter

## 📚 Key Lessons Learned

* **Small datasets call for conservative choices:** a few well-justified models, no cherry-picking, and honest reporting.
* **Audit every input for leakage:** only information known before the experiment belongs in the model.
* **In Jupyter, `plt.close()` straight after `plt.savefig()` hides the figure.** Use `plt.show()` and create each figure with `plt.subplots()`.

## 👤 Author

Oluwasemilogo Oluwasekunolami Akinlo
