## BeHealthy NER Model for Disease and Treatment Extraction

### Overview

This project is centered around developing a Named Entity Recognition (NER) model for a hypothetical health tech company, "BeHealthy." BeHealthy connects the medical community with patients through a platform that facilitates doctor-patient interactions, appointment scheduling, and online prescription ordering. As BeHealthy expands, so does the volume of medical data generated through patient notes and doctor reviews.

The primary goal of this project is to create a custom NER model capable of extracting disease names and their probable treatments from unstructured medical text. This will enable BeHealthy to better organize and analyze patient data and enhance the services offered to patients and healthcare providers.

### Problem Statement

Given a dataset of unstructured medical text, the task is to:

    - Identify diseases and treatments mentioned implicitly in the text.
    - Extract this information into a structured format (e.g., a dictionary or table) where diseases serve as keys and their probable treatments as values.
    - For instance, a sentence in the dataset might read:

        "The patient was a 62-year-old man with squamous cell lung cancer, which was first successfully treated by a combination of radiation therapy and chemotherapy."

In this example:

    - Disease: Lung cancer
    - Treatment: Chemotherapy

### Approach

To accomplish this, we’ll leverage a Conditional Random Fields (CRF) model, trained on annotated medical text, to detect disease and treatment entities within sentences. Below is an outline of the steps involved:

### Steps

#### Data Processing

    - Merge individual words into complete sentences based on blank line delimiters in the dataset.
    - Recreate sentences in the train_sent and test_sent datasets from word-level data.
    - Generate corresponding label sequences in train_label and test_label datasets, where each word has an associated label:
        - O: Other (non-entity)
        - D: Disease
        - T: Treatment


#### Feature Engineering

    - Define features for each word to aid the model in distinguishing diseases and treatments. Examples of features include:
        - Part-of-speech tags
        - Word morphology (e.g., suffixes, prefixes)
        - Contextual words around each target word


#### Model Training

    - Train the CRF model on the processed training data using the feature set defined above.
    - Use the train_sent and train_label datasets for model training and test_sent and test_label datasets for model evaluation.


#### Evaluation

    - Evaluate model performance on the test dataset to assess its accuracy in extracting diseases and treatments.

#### Dictionary Creation

    - Construct a dictionary where each disease (key) maps to its associated treatments (values), based on model predictions on the test dataset.

### Dataset Information

The following datasets are provided:

    - train_sent: Training sentences split by word with blank lines indicating new sentences.
    - test_sent: Testing sentences structured similarly to the training set.
    - train_label: Labels corresponding to each word in train_sent (D, T, or O).
    - test_label: Labels corresponding to each word in test_sent.

### Resources

    - Sample Medical Dataset: Includes both training and testing datasets for sentence and label data.
    - Commented Jupyter Notebook: Demonstrates data processing, feature engineering, and model training in Python.


### Expanding the feature set to incorporate additional medical terms and context.

    - Fine-tuning the CRF model or using more advanced deep learning models for improved accuracy.
    - Integrating the model into BeHealthy’s platform for real-time disease-treatment extraction.
