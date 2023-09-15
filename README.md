# NLP-NHS-Guidelines
This code is designed to enhance the guidelines for administering IV medication for nurses in the NHS, with the aim of reducing errors that can sometimes lead to fatalities due to poorly written guidelines. We utilize GPT from OpenAI for this purpose.

## Writing Enhancement
The guideline is initially divided into sections, categorized by headers such as 'Administration' and 'Compatibility with Other Medicines.' We then extract the text from each section, enabling us to handle each section individually, providing greater control over the output. The writing improvement process takes place in three stages:

1. We generate a summarized version of the text, focusing on brevity.
2. A refined version of the text is produced, making subtle adjustments based on feedback gathered from nurses in user studies.
3. The markdown formatting of the text is enhanced.

## Adding Technical Suggestions
This tool serves as a support system rather than a replacement for human experts. We do not use GPT to generate technical content but provide suggestions for additional information that should be added by a technical expert. This process involves several steps. Initially, an extra resources document with detailed medicine information is used to generate a list of questions that might have been asked during its creation. We then input the actual medicine guideline document (which we aim to improve) into GPT, along with a prompt to identify which of these questions remain unanswered, indicating potentially missing information. This list is then mapped to the relevant sections in the medication guideline document.

Below is a schematic illustrating how these two pipelines integrate:
![pipeline](https://github.com/hWils/NLP-NHS-Guidelines/assets/47060850/c8c67941-717c-4d60-a226-2559b1edd284)



## Key Evaluation Metrics
- **Readability**: We use the Flesch-Kincaid grade score, where a lower score indicates improved readability.
- **Semantic Similarity**: We rely on BERT Score to ensure that the meaning of each sentence remains consistent.
- **Factfulness**: Entities are identified using AWS in both the original and improved versions to check for any information loss or added details.
- Custom GPT hallucination checker.


# Code
- refined-aws-medical-comments.ipynb - this is the main file for improving the writing. It calls the evaluation script (and can be linked in with the visualiation script).
- evaluation_methods.ipynb - this is called in the main script. It contains all the metrics for assessing the safety and efficacy of the improved versions
- technical.ipynb - this is used to generate technical suggestions, and is a standalone script
- visualisation.ipynb - this script is used to generate a knowledge graph with entities and their relations grouped by entity type to give a quick snapshop of the document content.

# Prompts
This folder contains the following prompts:

- Step 1: Summarise the content for brevity - overview.txt
- Step 2: Refine the writing style - experimental_comments.txt
- Step 3: Improve the markdown - markdown.txt
- Technical suggestions:
- Visualisation: knowledge_graph.txt + generate_relations.txt
- Evaluation: hallucinate_check.txt
