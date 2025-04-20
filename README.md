# Nurse Agent RAG Model (Gemini + Chroma)

This project builds a Retrieval-Augmented Generation (RAG) pipeline designed to simulate a professional nurse reviewing patient data and summarizing key information for doctors.

---

## Dataset

**Source:** [Kaggle Hub: healthcare-dataset.csv](https://www.kaggle.com/datasets/prasad22/healthcare-dataset)

The dataset includes synthetic patient records containing:
- Name, Age, Gender  
- Medical Condition, Assigned Doctor  
- Insurance Provider, Billing Amount  
- Medication, Test Results, etc.

---

## Project Workflow

### 1. Data Cleaning & Transformation with Gemini
- Used Gemini Pro to clean and normalize raw patient data.
- Applied few-shot prompting to demonstrate the desired structure:
  - **Input:** raw, inconsistent data
  - **Output:** clean, standardized summaries with condition categories
- Transformed the data into consistent records for downstream use.

### 2. Document Embedding
- Embedded the cleaned records using Gemini's `text-embedding-004` model.
- 
### 3. Chroma Vector Database
- Stored all embedded patient records in a ChromaDB.

### 4. RAG Pipeline with Prompt Engineering
- Retrieved relevant patient summaries from Chroma based on user queries.
- Constructed a role-based prompt that instructs Gemini to act as a professional nurse.

---

## Example Prompt


You are a professional nurse reviewing multiple patient records.

For each patient, identify their condition category and provide a concise summary highlighting what the doctor should know. 
Be clear and structured, as if you're giving verbal updates during medical rounds. 
Make sure to include a separate summary for each patient based on the information provided.

## Output

Okay, here are the patient summaries for medical rounds:

Patient: Adrienne Bell  
Condition Category: Oncology  
Assigned Doctor: Dr. Kathleen Hanna  

Summary for Dr. Hanna:  
Adrienne Bell is a 43-year-old female oncology patient. Her current billing is $14,238.32. Please review her case to ensure appropriate treatment and billing alignment.

Patient: Danny Smith  
Condition Category: Chronic  
Assigned Doctor: Dr. Tiffany Mitchell  

Summary for Dr. Mitchell:  
Danny Smith is a 76-year-old female patient with a chronic condition. Current billing stands at $27,955.10. Please assess the current management plan and billing accuracy.

Patient: Christina Martinez  
Condition Category: Oncology  
Assigned Doctor: Dr. Suzanne Thomas  

Summary for Dr. Thomas:  
Christina Martinez is a 20-year-old female oncology patient. Her current billing is $45,820.46. Please review her case, focusing on treatment progress and cost-effectiveness, given the significant billing amount.

