# dfci_msk_teacher_student_medonc

This repository contains training and inference code for extracting cancer outcomes from medical oncologist notes based on the paper "Shareable artificial intelligence to extract cancer outcomes from electronic health records."

Preprocessing code is included but would need to be modified to work on external EHR data depending on its data delivery format.

To run inference, use the file 4_external_medonc_inference.ipynb. You will need a dataset containing a column labeled "text", in which each observation corresponds to the oncologist note on which you would like to run inference. The notebook currently runs inference on synthetic_example_medonc_data.csv, yielding output file synthetic_example_medonc_inference_results.csv .

Student model weights can be obtained from https://huggingface.co/kenlkehl/dfci-student-medonc .  A Docker image that can be downloaded, built to install all required dependencies, and used to run inference on a synthetic dataset of five oncologist notes is also available there. Initial Docker build takes approximately ten minutes; inference takes about 30 seconds.

The model will output predicted logits (log odds) that the following outcomes are present in each report:
1) Any cancer
2) Response to therapy/improving cancer
3) Progression of disease/worsening cancer
