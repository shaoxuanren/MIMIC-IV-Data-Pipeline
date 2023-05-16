# MIMIC-IV

**Reference**
This repo is a reproducibility study of Gupta et al, Proceedings of Machine Learning Research 193:311–325, 2022. 
The paper can be found from the following link.
https://proceedings.mlr.press/v193/gupta22a/gupta22a.pdf
The original repo can be found using the link below.
https://github.com/healthylaife/MIMIC-IV-Data-Pipeline

Please cite the original paper using the infomation below.

```
@InProceedings{gupta2022extensive,
  title = 	 {{An Extensive Data Processing Pipeline for MIMIC-IV}},
  author =       {Gupta, Mehak and Gallamoza, Brennan and Cutrona, Nicolas and Dhakal, Pranjal and Poulain, Raphael and Beheshti, Rahmatollah},
  booktitle = 	 {Proceedings of the 2nd Machine Learning for Health symposium},
  pages = 	 {311--325},
  year = 	 {2022},
  volume = 	 {193},
  series = 	 {Proceedings of Machine Learning Research},
  month = 	 {28 Nov},
  publisher =    {PMLR},
  pdf = 	 {https://proceedings.mlr.press/v193/gupta22a/gupta22a.pdf},
  url = 	 {https://proceedings.mlr.press/v193/gupta22a.html}
}
```

**Dependencies**

Please refer requirements.txt.

**Data download instruction**

Go to https://physionet.org/content/mimiciv/1.0/

Follow instructions to get access to MIMIC-IV dataset.

Download the files using your terminal: wget -r -N -c -np --user mehakg --ask-password https://physionet.org/files/mimiciv/1.0/

Save downloaded files in the parent directory of this github repo.

The structure should look like below for v1.0-

mimiciv/1.0/core
mimiciv/1.0/hosp
mimiciv/1.0/icu

The structure should look like below for v2.0-

mimiciv/2.0/hosp
mimiciv/2.0/icu

**How to run the pipeline**

- After downloading the repo, open **mainPipeline.ipynb**.
- **mainPipeline.ipynb**, contains sequential code blocks to extract, preprocess, model and train MIMIC-IV EHR data.
- Follow each code bloack and read intructions given just before each code block to run code block.
- Follow the exact file paths and filenames given in instructions for each code block to run the pipeline.
- For evaluation module, clear instructions are provided on how to use it as a standalone module.

**Preprocessing code**

	- **./day_intervals_preproc**
		- **day_intervals_cohort.py** file is used to extract samples, labels and demographic data for cohorts.
		- **disease_cohort.py** is used to filter samples based on diagnoses codes at time of admission
	- **./hosp_module_preproc**
		- **feature_selection_hosp.py** is used to extract, clean and summarize selected features for non-ICU data.
		- **feature_selection_icu.py** is used to extract, clean and summarize selected features for ICU data.
		
**Training and Evaluation code**

	- **train.py**
		consists of code to create batches of data according to batch_size and create, train and test different models.
	- **Mimic_model.py**
		consist of different model architectures.
	- **evaluation.py**
		consists of class to perform evaluation of results obtained from models.
		This class can be instantiated separated for use as standalone module.
	- **fairness.py**
		consists of code to perform fairness evaluation.
		It can also be used as standalone module.
	- **parameters.py**
		consists of list of hyperparameters to be defined for model training.
	- **callibrate_output**
		consists of code to calibrate model output.
		It can also be used as standalone module.



**Table of results** 

![image](https://user-images.githubusercontent.com/97659804/236751304-4ad6763f-3f50-40db-ac67-427746ffa276.png)



