# RPA_Agent_Task_Anjali
Invoice Data Extraction & Validation Automation (Blue Prism)

Prerequisites (Dependencies):
1. For the PDF activities used in this automation, "Pdfsharp.dll" should be downloaded and placed in the Blue Prism Automate folder. This is available in the Blue Prism Digital Exchange.
2. For the Email/Outlook activities, the object used requires the "Microsoft.Office.Interop.Outlook.dll" to be installed. This is already available in the C:\Windows\assembly\GAC_MSIL\Microsoft.Office.Interop.Outlook\15.0.0.0__71e9bce111e9429c\Microsoft.Office.Interop.Outlook.dll folder. One must copy and paste this in Blue Prism folder.
3. Environment Variables should be added/modified accordingly:
  InvoiceDataExtractionValidation_EmailIDs--> Email Id to share the report and exception messages
  InvoiceDataExtractionValidation_InputFolderPath--> Folder path where the PDFs will be placed and the Excel Database is available. Request to place Excel data inside   a subfolder "Data".
  InvoiceDataExtractionValidation_QueueName--> Invoice Data Extraction and Validation Queue

This automation mainly consists of three bots, which needs to be run sequentially as mentioned below.

1. Invoice Data Extraction and Validation Automation - Queue Builder: This bot checks for the PDFs in the folder and loads the items to the queue for the processing.
2. Invoice Data Extraction and Validation Automation - Main Process: Picks item from the queue one by one and extracts data from the PDF. Validates it against the Excel data. Moves the PDF file to "Processed" or "Exceptions" folder. Finally, marks the item in the queue as "Success" or "Exception".
3. Invoice Data Extraction and Validation Automation - Report: A summary report of the run in generated in the folder, from the data available in the queue, and is also shared through email.


This automation involves simple inbuilt PDF manipulation actions. Due to the limitations in the Trial/Learning Blue Prism edition, this automation works only for structured data. And may have challenge running for unstructured data. It has 8 items as input, where, it exceptions out 3 items (with email notification) due to data mismatch and data not found, and marks the other 5 items as successful.
