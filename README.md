# Invoice Segregation Automation (UiPath RPA)

## Project Overview
An automated Robotic Process Automation (RPA) solution built using **UiPath Studio** to process, segregate, and route batch invoice PDF files. The bot dynamically reads files from a source directory, parses file metadata, extracts invoice identifiers, and routes each file to its corresponding target directory using dynamic dynamic switch-case logic.

---

## Key Features & Logic Flow

1. **Folder Path & File Fetching:**
   * Fetches target source directory containing batch invoice documents.
   * Retrieves all file paths as a string array (`String[]`) using `.NET System.IO.Directory.GetFiles(folderpath)`.

2. **Iterative Processing & Metadata Parsing:**
   * Iterates through each file path using a `For Each` activity.
   * Converts raw file path strings into `.NET FileInfo` objects (`New FileInfo(invoice)`) to access structured file properties and metadata.
   * Standardizes file name extraction by stripping directory paths and extensions using `System.IO.Path.GetFileNameWithoutExtension(file_info.FullName)`.

3. **Dynamic Routing (Switch Case):**
   * Extracts specific identifying business rules (e.g., entity codes, branch identifiers) using string manipulation (`file_name.Substring(...)`).
   * Evaluates extracted conditions within a **Switch Case** activity to automatically move invoices into designated sub-folders.

---

## Technical Stack & Dependencies

* **Tool:** UiPath Studio
* **Language/Framework:** VB.NET / .NET `System.IO`
* **Data Types Used:**
  * `String` (Directory paths, individual file names)
  * `String[]` (File path collections)
  * `System.IO.FileInfo` (File metadata object)

---

## Folder Structure

```text
Invoice_Segregation/
│
├── Main.xaml                      # Main workflow logic
├── Source/
│   └── Invoices by Company Code/  # Input folder for incoming PDFs
├── Output/                        # Target destination folders
├── project.json                   # UiPath dependencies & project config
├── .gitignore
└── README.md
