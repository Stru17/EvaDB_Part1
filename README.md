# EvaDB PDF Reader Enhancement Project

## Introduction

The primary objective of this project is to refine the existing PDF Reader script utilized by EvaDB to facilitate more precise extraction of textual and image data from various PDF documents. The extracted data, which can be formatted into txt, csv, or xml files, forms a pivotal resource for subsequent text analysis, summarization, translation, among other applications. A prime example of its application within EvaDB is the Story QA feature, which leverages extracted text to enable ChatGPT in addressing related queries.

## Implementation Timeline/Details

In the exploration phase, I tested pdfquery and PyPDF2 but found them to be lacking, especially when handling PDFs with bullet points or multiple text columns on a single page. Their line-by-line text extraction necessitated additional processing to achieve desired results.

Upon further investigation, the `fitz` library, also known as `PyMuPDF`, was discovered to have superior performance in text extraction from PDFs. Even beter, it also has additional functionalities including image extraction, PDF file merging, among others. Unlike its predecessors, `fitz` efficiently handles multiple text columns and exhibits fewer errors during line-by-line text extraction.

Having shared these findings with Professor Arulraj, it was agreed that the ensuing step would involve text processing to chunk data into topics or sections from the extracted txt file. The professor suggested to explore `unstructuredIO`, which I then integrated into the project by connecting to its robust API (requiring an access key) and its ability to categorize extracted text into Title, Narrative Text, List Item, and Uncategorized Text. Nonetheless, `unstructuredIO` faced a similar line-by-line text extraction challenge, warranting a decision to feed it with the `fitz` generated text file which, although necessitated some processing, yielded a significantly improved and readable csv file output.

## Challenges Faced

The focal point of the challenge was centered around ensuring efficient text extraction particularly from PDFs formatted as documents, papers, or articles. The necessity to process the `fitz` output to ensure accurate title detection for `unstructuredIO` and to merge sentences appropriately was a notable hurdle. Despite some errors, a viable solution was achieved to improve EvaDB's pdf loader, enabling `unstructuredIO` to categorize text into types, though some inaccuracies remain, presenting an opportunity for future improvement.

## Sample Input/Output

Refer to the `EvaDB Part 1.ipynb` file within the EvaDB PDF folder for the finalized code. The `spring_2023_orientation_document.pdf` within the 'orientation' folder serves as the sample input, with respective output files illustrating text extraction and processing results using different libraries. A comparative review of these files highlights the strides made in enhancing PDF text extraction for EvaDB's applications. `fitz_unstructured_pdf_loader_script.py` is the finalized code that is expected to be pulled into EvaDB for potential improvements to EvaDB.

## Next Steps

The forthcoming phase of this project aims at evaluating the enhanced PDF reader script with the Story QA feature in ChatGPT4 through the EvaDB Part 2 segment. This will ascertain the script’s impact on improving the bot's efficiency in summarization and question-answering tasks. Additionally, further exploration will be directed towards discovering more proficient methods of text chunking, which may encompass alternative solutions or enhanced processing of the `fitz` output text file.

## Requirements and Usage

Ensure the following libraries are installed:

```plaintext
pandas
PyMuPDF
requests
