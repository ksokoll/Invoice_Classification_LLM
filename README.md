# Invoice Classification with LLMs

A repository for AI experiments exploring the performance of large language models (LLMs) in automating invoice classification to optimize financial workflows.

## Project Overview

This project investigates the use of large language models (LLMs) to classify invoices efficiently and accurately. The goal is to improve the automation of invoice processing by leveraging natural language understanding to assign correct categories and detect anomalies. The experiments involve prompt engineering, model fine-tuning, and evaluation of different classification strategies.

The following notebook illustrates a system that is able to classify invoices and determine the correct cost center based on ChatGPT o3-mini / 4o-mini. We simulate an accounting use case that is quite common in companies, as incoming invoices need to be labeled with the correct cost type for adequate bookkeeping.

## Benefits of LLMs in Invoice Processing

LLMs are powerful and offer a variety of benefits for invoice processing:

* **Automation**: LLMs can automate the invoice labeling process, saving time and resources.
* **Accuracy**: By using advanced models, the accuracy of classification is increased.
* **Scalability**: LLMs can efficiently process large volumes of invoices, which is particularly beneficial for growing businesses.
* **Flexibility**: The models can be adapted to different invoice formats and structures.

Since we are in the accounting domain, achieving high accuracy is a priority. The goal is a minimum accuracy of 95%, ensuring that at least 19 out of 20 predictions are correct.

## Experimental Setup

### Data and Input Format
- Invoices are provided as structured or semi-structured text.
- The LLM processes the invoice content and assigns a classification label.
- Optional: Historical invoice data is used for context enhancement.

### Objective
- Classify invoices into predefined categories with high accuracy.
- Optimize processing speed and minimize errors and token usage in classification.
- Evaluate the effectiveness of different model setups and prompt strategies.

## Notebook Structure

1. **Create Invoice Dataset**: 
   - 2,500 example invoices are created for a total of 50 cost centers.
2. **Classify Invoices**: 
   - First classification run to analyze baseline accuracy.
3. **Evaluation**: 
   - Analyzing classification accuracy with a focus on low-accuracy categories.
4. **Improving Accuracy**: 
   - Running experiments to enhance the LLM’s accuracy.
5. **Results**: 
   - Summary of improvements and final performance metrics.

## Iterations & Results

### Baseline Setup
- **Approach**: Direct classification using an LLM with a simple prompt.
- **Result**: Initial accuracy of ~90% with common misclassifications in ambiguous cases.

### Creation of Invoice Dataset
- **Process**: Generated 2,500 invoices based on 50 input cost types.

### Iteration 1: Ensemble Method
- **Modification**: Introduced three LLM categorizations instead of one.
- **Impact**: No measurable improvement, but better identification of ambiguous classes.

### Iteration 2: Adjustment of Cost Types
- **Modification**: Removed ambiguous categories to provide clearer decision boundaries.
- **Impact**: Accuracy improved to ~98%, particularly benefiting edge cases.

### Iteration 2.5: Adjustment of Model Type
- **Modification**: Downgraded the LLM from o3 to 4o-mini since results were similar.
- **Impact**: Accuracy remained at ~98%, with faster processing speed and lower token usage.

## Final Results
294 out of 300 samples were correctly classified into the now 40 categories, achieving an accuracy of **98%**. This exceeds the project goal of 95% by three percentage points. Three of the six misclassified samples belonged to the cost types "patent law consulting cost" and "legal consulting cost," which are closely related and could potentially be merged into a single category.

Additionally, this test was conducted using 4o-mini instead of o3. Despite being a weaker model, optimizing the input structure led to stable results. This choice also offers advantages such as faster processing times, reduced costs, and lower environmental impact.

In a real-world scenario, this notebook serves as a proof-of-concept and a foundation for developing a production-ready model.

## Lessons Learned

- **Category clarity is crucial**: Both LLMs and humans struggle with ambiguous classifications. Reducing redundancy and refining categories significantly improved accuracy.
- **Optimal input design reduces model complexity needs**: When inputs are well-structured, a smaller model can perform as well as a more powerful one while consuming fewer resources.
- **LLMs struggle with confidence estimation**: The models often remain highly confident even when making incorrect predictions. Addressing this limitation could be an area of future improvement in LLM research.

## Future Work & Outlook
- Fine-tuned domain-specific models for better adaptability.
- Multi-agent approaches for more robust classification.
- Extending the methodology to related financial document processing tasks.

