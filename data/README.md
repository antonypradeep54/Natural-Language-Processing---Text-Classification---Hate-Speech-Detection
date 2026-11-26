# Dataset

Place your authorized local copy of `TwitterHate.csv` in this directory. Expected columns: `id`, `label`, `tweet`. Labels: 0 = non-hate, 1 = hate speech. Redistribution permissions have not been verified; the CSV is not included. In Colab, upload the CSV to this directory before running the notebook.


### External dataset source

Dataset source: [Twitter Hate Speech — Kaggle](https://www.kaggle.com/vkrahul/twitter-hate-speech). Redistribution rights have not been verified. Download the labeled training CSV `train_E6oV3lV.csv` (columns `id`, `label`, `tweet`), not the unlabeled test file, extract it if necessary and rename it to `TwitterHate.csv`. Keep it locally or upload it into the Colab runtime's `data/` directory. Do not commit the raw data. Expected original dataset profile (pending verification): 31,962 rows, 29,720 label 0 and 2,242 label 1. Confirm these counts and schema before training; matching counts alone do not establish identical content.
