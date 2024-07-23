# dfci_msk_teacher_student_medonc

This repository contains training and inference code for extracting cancer outcomes from medical oncologist notes based on the paper "Shareable artificial intelligence to extract cancer outcomes from electronic health records."

Preprocessing code would need to be modified to work on external EHR data depending on its data delivery format.

Training and initial evaluation of the DFCI-medonc-teacher model is done in 1_train_dfci_teacher_on_dfci_phi.ipynb. Inference with the teacher model on MIMIC discharge summaries is done in 2a_teacher_inference_on_mimic_discharges_firsthalf.ipynb and 2b_teacher_inference_on_mimic_discharges_secondhalf.ipynb. Training and initial evaluation of the DFCI-medonc-student model is done in 3_train_medonc_student_on_mimic.ipynb. These notebooks are provided for illustration purposes only, since we cannot share the private PHI data used to train the teacher, and the MIMIC data are available on Physionet to credentialed users.

In accordance with policies specified on the MIMIC-IV dataset site, which require that models trained using MIMIC data be released through Physionet to enable proper credential checks, student model weights and sample code for inference on synthetic data have been submitted to Physionet. To run inference after obtaining the weights, the notebook 4_external_medonc_inference.ipynb can also be used. It expects a dataset containing a column labeled "text", in which each observation corresponds to the oncologist note on which you would like to run inference. The notebook currently runs inference on synthetic_example_medonc_data.csv, yielding output file synthetic_example_medonc_inference_result.csv 

The model will output predicted logits (log odds) that the following outcomes are present in each report:
1) Any cancer
2) Response to therapy/improving cancer
3) Progression of disease/worsening cancer
