# PhenoRareAI
Phenotype-Based Intelligent Diagnosis for Rare Neuromuscular Disorders (NMD) 


# Phenotype-Augmentation

The Phenotype-Augmentation folder holds the Phenotypic Radiographs web files after phenotype enhancement refinement for Glycogen storage disease II and Spinal Muscular Atrophy.


# CHPO-NER


1. Store electronic hospital medical data file of txt format and json format in the CHPO-NER/hospital_data and CHPO-NER/hospital_data_json folder

2. Download https://huggingface.co/FreedomIntelligence/HuatuoGPT2-7B to CHPO-NER (or download https://drive.google.com/file/d/1Kvnd26gKvDQX0t95ZvytuqNmzbGbEDt1/view?usp=drive_link to CHPO-NER)

3. Download https://huggingface.co/Adapting/bert-base-chinese-finetuned-NER-biomedical and https://huggingface.co/iioSnail/bert-base-chinese-medical-ner to CHPO-NER/TXT2HPO (or download https://drive.google.com/file/d/1Kvnd26gKvDQX0t95ZvytuqNmzbGbEDt1/view?usp=drive_link to CHPO-NER/TXT2HPO)

4. Run python bert_base_chinese_finetuned_biomedical_api.py (bert_base_chinese_medical_api.py) [Set API_TOKEN] and Run python huatuogpt2_prompt_disease_symptom.py [Set openai.api_key and Modify the prompt format in labelByGPT_disease_symptom.py]

5. Run python chpobert-entity-process.py and Run python huatuogpt2_ner_enetity_process.py to process the recognition results of the previous step, get the recognition results of each patient's EHR into csv files(stored in the CBERT-NER-API and HuatuoGPT2-NER-API folders).

6. Go to the CHPO-NER/TXT2HPO folder and Run python chinese-finetuned-NER-biomedical_chpo_embedding.py and python chinese-medical-ner_chpo_embedding.py to create Chinese embedding dictionarys (or download https://drive.google.com/file/d/1rTm8-_Dy2apRBu8EjcrbMtX7XUIda0A1/view?usp=drive_link stored in CHPO-NER/TXT2HPO)

7. Follow the PhenoPro running process(https://github.com/jumphone/PhenoPro). (1) Run Python step0_dumping.py. (2) Run our seven models for phenotype identification, such as Run python txt2hpo_sunday_zh_cn.py, Run python step1_txt2hpo_cutoff_finetuned _ner_biomedical.py and Run python step1_txt2hpo_gptner_disease_symptom_finetuned_ner_biomedical.py



# Disease-Prioritization

1. Store the human clinical phenotype data of hospital patients in the Disease-Prioritization/HPODataBase/Hospital_DATA folder.

2. Download https://drive.google.com/file/d/11mCvwvNky7-jDC1RIsp91wvnAT6rI3r_/view?usp=drive_link and Extract into the Disease-Prioritization/HPODataBase/20221215 folder

3. Go to Disease-Prioritization/HPODataBase and Run python create_lin_similarity_matrix_adddelete.py (or download https://drive.google.com/file/d/1Pb3lCoIDr1GETu9Yyf4meSybMjZQkqJN/view?usp=drive_link to store it in Disease-Prioritization/HPODataBase/HPODataBase/20221215)

4. Go to Disease-Prioritization/Phen2Disease: (1) Run python phen2disease_double_adddelete.py. (2) Run python phen2disease_patient_adddelete.py. (3) Run python similarityscoredisease_adddelete.py. (4) Run python diseasezscoreintegrated_adddelete.py

6. Go to Disease-Prioritization/BASE_IC: (1) Run python BASE_IC_DiseaseRank_adddelete.py. (2) Run python BASE_IC_DiseaseRank_adddelete_score.py

7. Download the Phrank project https://pypi.org/project/phrank), update our Disease-Prioritization/Phrank project file and Run python phrank_disease_adddelete.py

8. Download LIRICAL ( https://lirical.readthedocs.io/en/latest), update our Disease-Prioritization/LIRICAL project file, Run python lirical_disease_adddelete.py

9. Go to Disease-Prioritization/RRF and Run python RRF_adddelete_integrated.py
