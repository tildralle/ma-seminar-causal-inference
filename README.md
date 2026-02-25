This repository contains all files and data sets used in the preparation of the term paper for the seminar “Causal Inference” (Master Political Science). It is divided into the following three notebooks.

1. topic_model.ipynb

Creates a topic model from coded Bundestag speeches and codes further speeches based on this.

Input Data:
- pp20_random_speeches_final_coding.csv 
    - Coded speeches from the 20th legislative period of the German Bundestag.
- pp20.p
    - All speeches from the 20th legislative period of the German Bundestag, extracted from the Bundestag minutes. The program for extracting the speeches is stored in [this repo](https://github.com/tildralle/extract-speeches-from-bundestag-minutes). 

Output Data:
- pp20_coded.pkl
    - The speeches of the 20th legislative period of the German Bundestag, fully coded.

2. convert_into_panel_data.ipynb

Creates a combined data set in panel format from the coded Bundestag speeches and information on the MPs' outside earnings. This involves a lot of data wrangling. The German coding labels are assigned their English equivalents, all names and designations in the data sets are standardized, and a few more steps.

Input Data:
- pp20_coded.pkl
    - The speeches of the 20th legislative period of the German Bundestag, fully coded.
- pp20_income_data.pkl
    - Data on the private sector jobs of MPs in the 20th legislative period. The API from Abgeordnetenwatch was used to collect the data. The code used for data extraction is stored in [this repo](https://github.com/tildralle/german-mps-moonlighting).

Output Data:
- pp20_income_data_compatible.csv
    - Data on the private sector jobs of MPs in the 20th legislative period, adapted to the data set on parliamentary speeches (pp20_coded.pkl).
- mp_year_topic_df.csv
    - The final data set in panel format at MP-year-topic level.

3. difference-in-difference.ipynb

First performs some descriptive analyses based on mp_year_topic_df.csv and then calculates several fixed effect regressions.

Input Data:
- pp20_income_data_compatible.csv
    - Data on the private sector jobs of MPs in the 20th legislative period, adapted to the data set on parliamentary speeches (pp20_coded.pkl). Mainly used for descriptive statistics.
- mp_year_topic_df.csv
    - The final data set in panel format at MP-year-topic level.