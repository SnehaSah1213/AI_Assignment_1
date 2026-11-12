Classical Reasoning Agent - AI Assignment 2026
=================================================
Files: reasoning_agent.ipynb (full implementation), report.pdf, submission.csv, README.txt

How to run
 1. Open reasoning_agent.ipynb in Google Colab (CPU is sufficient) and Run all.
 2. The notebook installs z3-solver/datasets/reportlab, loads RuleTaker, FOLIO and CounterBench from Hugging Face,
    prints accuracy and inference time per dataset and for the unified agent, and regenerates report.pdf.
 3. To predict the private test set set TEST_PATH (csv/json/jsonl) in the last cell; it calls make_submission(df) and writes
    submission.csv with columns id and predicted_label (True/False). Context/question columns are auto-detected
    (premises-FOL, premises_fol, context, knowledge_base, kb, theory, given_info, premises / conclusion-FOL, conclusion_fol, question, query, hypothesis, conclusion).

Method: symbolic parsing -> forward chaining (RuleTaker), CNF + binary resolution with Z3 as time-boxed fallback (FOLIO),
structural causal model with interventions and abduction (CounterBench). No generative AI is used for any decision.
Measured public results: RuleTaker test 99.96%, FOLIO val 83.74%,
CounterBench alpha 95.00% / backdoor 90.00%.
Libraries: python, pandas, z3-solver, datasets, reportlab.
