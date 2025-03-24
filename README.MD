# Ticket Text Classification and Topic Modeling

## Project Overview
This project presents a complete NLP pipeline for analyzing and classifying customer support ticket texts. The workflow includes text preprocessing, topic modeling using BERTopic and HDBSCAN, and classification using an XGBoost model. The goal is to automatically assign topics to support tickets and demonstrate how such a system can assist in extracting insights from unstructured customer feedback.

## Installation
To install all required dependencies, run:

```sh
pip install -r requirements.txt
```

## Dataset
The dataset contains customer support ticket entries with the following columns:

- `Ticket ID`: Unique ticket identifier
- `Customer Name`, `Customer Email`: Customer information
- `Customer Age`, `Customer Gender`: Demographic details
- `Product Purchased`, `Date of Purchase`: Product and purchase information
- `Ticket Type`, `Ticket Subject`, `Ticket Description`: Core textual content
- `Ticket Status`, `Resolution`, `Ticket Priority`, `Ticket Channel`: Ticket metadata
- `First Response Time`, `Time to Resolution`, `Customer Satisfaction Rating`: Support performance indicators

## Preprocessing Steps

1. **Handling missing values**: Removed incomplete or irrelevant records.
2. **Removing duplicates**: Ensured each ticket is unique.
3. **Text normalization**:
   - Lowercasing, removing special characters and digits
   - Tokenization and stopword removal
   - Lemmatization using NLTK
4. **Feature combination**:
   - Merged `Ticket Subject` and `Ticket Description` into a single `clean_text` field
   - Calculated cosine similarity between subject and description

## Exploratory Data Analysis (EDA)

- Analyzed most frequent words in raw and cleaned texts
- Visualized subject distributions
- Generated word clouds for key categories
- Plotted similarity scores to assess alignment between ticket subject and description

## Topic Modeling (BERTopic + HDBSCAN)

- Used `sentence-transformers` for high-quality embeddings
- Clustered texts using `HDBSCAN`
- Extracted interpretable topics using `BERTopic`
- Evaluated topic model performance using:
  - **Coherence Score**: Measures topic clarity
  - **Diversity Score**: Measures uniqueness of topics
- Visualized topics using intertopic distance map and heatmaps

## Classification with XGBoost

- After topic modeling, split the dataset into training (80%) and testing (20%) sets
- Used BERT embeddings as features
- Trained an XGBoost classifier to predict topic labels
- Evaluated performance with:
  - Classification report (precision, recall, f1-score)
  - Confusion matrix
- Applied model to new/unseen ticket examples

## Example Usage

All steps are implemented in a Jupyter Notebook.

### To run the notebook:
1. Launch Jupyter:
   ```sh
   jupyter notebook
   ```
2. Open the main `.ipynb` file
3. Execute cells sequentially

### Project Structure (Example)
```
project-folder/
├── Customer_Feedback_NLP_Pipeline.ipynb                   # Main analysis notebook
├── tickets_sample_data.xlsx      # Sample ticket data
├── requirements.txt              # Dependency list
├── README.md                     # This file
```

## How to Create a README File
To manually create a README:

1. Open a text/code editor (e.g., VS Code or Notepad++)
2. Write your documentation in Markdown syntax
3. Save the file as `README.md`

You can preview it on GitHub or using a Markdown viewer.

## Future Work
- Use grid search for improved model tuning
- Test with alternative embeddings (e.g., sentence-BERT variants)
- Expand dataset and deploy the model as a ticket classification service

## License
This project is open-source and available under the MIT License.

## Contact
For questions or contributions, feel free to open an issue or contact the maintainer.
