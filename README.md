# MLT_supplemental_code
Meta learning with LLM: supplemental code for reproducibility of computational results for MLT and MLT-plus-TM. Related paper: "META LEARNING WITH LANGUAGE MODELS: CHALLENGES AND
OPPORTUNITIES IN THE CLASSIFICATION OF IMBALANCED TEXT", A. Vassilev, H. Jin, M. Hasan, 2023 (to appear on arXiv)


Folder structure:
1. Five individual model predicted probability files from five individual models. Each model has its own folder. They are bigbird, bert, btweet, bloom, and xlnet. 

arxiv2023/
├── bert
│   └── bi
├── bigbird
│   └── bi
├── bloom
│   └── bi
├── btweet
│   └── bi
├── hateCheck_data
├── mlt_pred_hc
├── mlt_tm_pred_hc
└── xlnet
    └── bi
	
Example of an individual model folder "bert". Predicted probability files for CAD dev and CAD test datasets are generated from inferences on bert model. For M-C (multi-label classification), the files are under this folder. 
For B-C, the files are under "bi" sub-folder. In B-C, HateCheck predicted probability files are also generated.
Each individual model includes two runs. The performance of each individual model is averaged by these two runs.
These two runs join MLT and MLT-plus-TM. 

bert
├── bi
│   ├── epoch_2_dev_label_id.csv
│   ├── epoch_2_dev_prob_id.csv
│   ├── epoch_2_hc_label_id.csv
│   ├── epoch_2_hc_prob_id.csv
│   ├── epoch_2_te_label_id.csv
│   ├── epoch_2_te_prob_id.csv
│   ├── epoch_4_dev_label_id.csv
│   ├── epoch_4_dev_prob_id.csv
│   ├── epoch_4_hc_label_id.csv
│   ├── epoch_4_hc_prob_id.csv
│   ├── epoch_4_te_label_id.csv
│   └── epoch_4_te_prob_id.csv
├── epoch_13_dev_label_id.csv
├── epoch_13_dev_prob_id.csv
├── epoch_13_te_label_id.csv
├── epoch_13_te_prob_id.csv
├── epoch_6_dev_label_id.csv
├── epoch_6_dev_prob_id.csv
├── epoch_6_te_label_id.csv
└── epoch_6_te_prob_id.csv


2. Reported HateCheck performance data from external source is under the folder of "hackCheck_data". We include these to compare with our results.

3. 32 predicted probability files (for 32 runs) on hatecheck inferenced from our MLT. They are under folder "mlt_pred_hc". Similarly, MLT-plus-TM files are under "mlt_tm_pred_hc". These data are used as input in eval_models_on_hatecheck.py.

Source code:
1. mlt_mlt-plus-tm_bi.py: MLT and MLT-plus-TM for B-C. Input data are from five individual model "bi" folders. It generates two sets of output: 1)hateCheck inferences on MLT and MLT-plus-TM (output at folders of "mlt_pred_hc" and "mlt_tm_pred_hc"; 2) Output file as MLT_TM_B_C_results.txt. This includes all run log with results for B-C.
2. mlt_mlt-plus-tm_multi.py: MLT and MLT-plus-TM for M-C. Input data are from five individual models. It generates one output file as MLT_TM_M_C_results.txt. This includes all run log with results for M-C.
3. eval_models_on_hatecheck.py: evaluate performance using hateCheck test suites against three external models, our individual models, MLT and MLT-plus-TM. This creates two output files: performance on 29 functionalities for 3 runs ( hatecheck_29_func_acc_3_runs.csv) and performance on target groups for 3 runs (hatecheck_target_acc_3_runs.csv). Input data are from "mlt_pred_hc" and "mlt_tm_pred_hc" folders.
	
Other files:
1. Readme.txt: this file.
2. requirements.txt: libraries required.
3. Output files for final reporting in the paper: MLT_TM_B_C_results.txt, MLT_TM_M_C_results.txt, hatecheck_29_func_acc_3_runs.csv, and hatecheck_target_acc_3_runs.csv.

How to run the code:
1. Run MLT and MLT-plus-TM for B-C: python mlt_mlt-plus-tm_bi.py
2. Run MLT and MLT-plus-TM for M-C: python mlt_mlt-plus-tm_multi.py
3. Run performance on HateCheck 29 functionalities and target groups: python eval_models_on_hatecheck.py. This code is modified on original source code from https://github.com/peluz/checking-hatecheck-code/blob/main/evaluation.ipynb.

The total files and folder structure:
arxiv2023/
├── bert
│   ├── bi
│   │   ├── epoch_2_dev_label_id.csv
│   │   ├── epoch_2_dev_prob_id.csv
│   │   ├── epoch_2_hc_label_id.csv
│   │   ├── epoch_2_hc_prob_id.csv
│   │   ├── epoch_2_te_label_id.csv
│   │   ├── epoch_2_te_prob_id.csv
│   │   ├── epoch_4_dev_label_id.csv
│   │   ├── epoch_4_dev_prob_id.csv
│   │   ├── epoch_4_hc_label_id.csv
│   │   ├── epoch_4_hc_prob_id.csv
│   │   ├── epoch_4_te_label_id.csv
│   │   └── epoch_4_te_prob_id.csv
│   ├── epoch_13_dev_label_id.csv
│   ├── epoch_13_dev_prob_id.csv
│   ├── epoch_13_te_label_id.csv
│   ├── epoch_13_te_prob_id.csv
│   ├── epoch_6_dev_label_id.csv
│   ├── epoch_6_dev_prob_id.csv
│   ├── epoch_6_te_label_id.csv
│   └── epoch_6_te_prob_id.csv
├── bigbird
│   ├── bi
│   │   ├── epoch_1_dev_label_id.csv
│   │   ├── epoch_1_dev_prob_id.csv
│   │   ├── epoch_1_hc_label_id.csv
│   │   ├── epoch_1_hc_prob_id.csv
│   │   ├── epoch_1_te_label_id.csv
│   │   ├── epoch_1_te_prob_id.csv
│   │   ├── epoch_2_dev_label_id.csv
│   │   ├── epoch_2_dev_prob_id.csv
│   │   ├── epoch_2_hc_label_id.csv
│   │   ├── epoch_2_hc_prob_id.csv
│   │   ├── epoch_2_te_label_id.csv
│   │   └── epoch_2_te_prob_id.csv
│   ├── epoch_10_dev_label_id.csv
│   ├── epoch_10_dev_prob_id.csv
│   ├── epoch_10_te_label_id.csv
│   ├── epoch_10_te_prob_id.csv
│   ├── epoch_7_dev_label_id.csv
│   ├── epoch_7_dev_prob_id.csv
│   ├── epoch_7_te_label_id.csv
│   └── epoch_7_te_prob_id.csv
├── bloom
│   ├── bi
│   │   ├── epoch_1_dev_label_id.csv
│   │   ├── epoch_1_dev_prob_id.csv
│   │   ├── epoch_1_hc_label_id.csv
│   │   ├── epoch_1_hc_prob_id.csv
│   │   ├── epoch_1_te_label_id.csv
│   │   ├── epoch_1_te_prob_id.csv
│   │   ├── epoch_3_dev_label_id.csv
│   │   ├── epoch_3_dev_prob_id.csv
│   │   ├── epoch_3_hc_label_id.csv
│   │   ├── epoch_3_hc_prob_id.csv
│   │   ├── epoch_3_te_label_id.csv
│   │   └── epoch_3_te_prob_id.csv
│   ├── epoch_11_dev_label_id.csv
│   ├── epoch_11_dev_prob_id.csv
│   ├── epoch_11_te_label_id.csv
│   ├── epoch_11_te_prob_id.csv
│   ├── epoch_9_dev_label_id.csv
│   ├── epoch_9_dev_prob_id.csv
│   ├── epoch_9_te_label_id.csv
│   └── epoch_9_te_prob_id.csv
├── btweet
│   ├── bi
│   │   ├── epoch_2_dev_label_id.csv
│   │   ├── epoch_2_dev_prob_id.csv
│   │   ├── epoch_2_hc_label_id.csv
│   │   ├── epoch_2_hc_prob_id.csv
│   │   ├── epoch_2_te_label_id.csv
│   │   ├── epoch_2_te_prob_id.csv
│   │   ├── epoch_3_dev_label_id.csv
│   │   ├── epoch_3_dev_prob_id.csv
│   │   ├── epoch_3_hc_label_id.csv
│   │   ├── epoch_3_hc_prob_id.csv
│   │   ├── epoch_3_te_label_id.csv
│   │   └── epoch_3_te_prob_id.csv
│   ├── epoch_11_dev_label_id.csv
│   ├── epoch_11_dev_prob_id.csv
│   ├── epoch_11_te_label_id.csv
│   ├── epoch_11_te_prob_id.csv
│   ├── epoch_18_dev_label_id.csv
│   ├── epoch_18_dev_prob_id.csv
│   ├── epoch_18_te_label_id.csv
│   └── epoch_18_te_prob_id.csv
├── eval_models_on_hatecheck.py
├── hatecheck_29_func_acc_3_runs.csv
├── hateCheck_data
│   ├── hatecheck_final_ACL.csv
│   ├── results_BERT_weighted_ACL.pkl
│   └── results_commercial_models_ACL.pkl
├── hatecheck_target_acc_3_runs.csv
├── mlt_mlt-plus-tm_bi.py
├── mlt_mlt-plus-tm_multi.py
├── mlt_pred_hc
│   ├── mlt_pred_hc_10.csv
│   ├── mlt_pred_hc_11.csv
│   ├── mlt_pred_hc_12.csv
│   ├── mlt_pred_hc_13.csv
│   ├── mlt_pred_hc_14.csv
│   ├── mlt_pred_hc_15.csv
│   ├── mlt_pred_hc_16.csv
│   ├── mlt_pred_hc_17.csv
│   ├── mlt_pred_hc_18.csv
│   ├── mlt_pred_hc_19.csv
│   ├── mlt_pred_hc_1.csv
│   ├── mlt_pred_hc_20.csv
│   ├── mlt_pred_hc_21.csv
│   ├── mlt_pred_hc_22.csv
│   ├── mlt_pred_hc_23.csv
│   ├── mlt_pred_hc_24.csv
│   ├── mlt_pred_hc_25.csv
│   ├── mlt_pred_hc_26.csv
│   ├── mlt_pred_hc_27.csv
│   ├── mlt_pred_hc_28.csv
│   ├── mlt_pred_hc_29.csv
│   ├── mlt_pred_hc_2.csv
│   ├── mlt_pred_hc_30.csv
│   ├── mlt_pred_hc_31.csv
│   ├── mlt_pred_hc_32.csv
│   ├── mlt_pred_hc_3.csv
│   ├── mlt_pred_hc_4.csv
│   ├── mlt_pred_hc_5.csv
│   ├── mlt_pred_hc_6.csv
│   ├── mlt_pred_hc_7.csv
│   ├── mlt_pred_hc_8.csv
│   └── mlt_pred_hc_9.csv
├── MLT_TM_B_C_results.txt
├── MLT_TM_M_C_results.txt
├── mlt_tm_pred_hc
│   ├── mlt_tm_pred_hc_10.csv
│   ├── mlt_tm_pred_hc_11.csv
│   ├── mlt_tm_pred_hc_12.csv
│   ├── mlt_tm_pred_hc_13.csv
│   ├── mlt_tm_pred_hc_14.csv
│   ├── mlt_tm_pred_hc_15.csv
│   ├── mlt_tm_pred_hc_16.csv
│   ├── mlt_tm_pred_hc_17.csv
│   ├── mlt_tm_pred_hc_18.csv
│   ├── mlt_tm_pred_hc_19.csv
│   ├── mlt_tm_pred_hc_1.csv
│   ├── mlt_tm_pred_hc_20.csv
│   ├── mlt_tm_pred_hc_21.csv
│   ├── mlt_tm_pred_hc_22.csv
│   ├── mlt_tm_pred_hc_23.csv
│   ├── mlt_tm_pred_hc_24.csv
│   ├── mlt_tm_pred_hc_25.csv
│   ├── mlt_tm_pred_hc_26.csv
│   ├── mlt_tm_pred_hc_27.csv
│   ├── mlt_tm_pred_hc_28.csv
│   ├── mlt_tm_pred_hc_29.csv
│   ├── mlt_tm_pred_hc_2.csv
│   ├── mlt_tm_pred_hc_30.csv
│   ├── mlt_tm_pred_hc_31.csv
│   ├── mlt_tm_pred_hc_32.csv
│   ├── mlt_tm_pred_hc_3.csv
│   ├── mlt_tm_pred_hc_4.csv
│   ├── mlt_tm_pred_hc_5.csv
│   ├── mlt_tm_pred_hc_6.csv
│   ├── mlt_tm_pred_hc_7.csv
│   ├── mlt_tm_pred_hc_8.csv
│   └── mlt_tm_pred_hc_9.csv
├── requirements.txt
└── xlnet
    ├── bi
    │   ├── epoch_3_dev_label_id.csv
    │   ├── epoch_3_dev_prob_id.csv
    │   ├── epoch_3_hc_label_id.csv
    │   ├── epoch_3_hc_prob_id.csv
    │   ├── epoch_3_te_label_id.csv
    │   ├── epoch_3_te_prob_id.csv
    │   ├── epoch_4_dev_label_id.csv
    │   ├── epoch_4_dev_prob_id.csv
    │   ├── epoch_4_hc_label_id.csv
    │   ├── epoch_4_hc_prob_id.csv
    │   ├── epoch_4_te_label_id.csv
    │   └── epoch_4_te_prob_id.csv
    ├── epoch_16_dev_label_id.csv
    ├── epoch_16_dev_prob_id.csv
    ├── epoch_16_te_label_id.csv
    ├── epoch_16_te_prob_id.csv
    ├── epoch_17_dev_label_id.csv
    ├── epoch_17_dev_prob_id.csv
    ├── epoch_17_te_label_id.csv
    └── epoch_17_te_prob_id.csv

