# Document to JSON Converter

A Python application that extracts text and tables from PDF and DOC/DOCX files and converts them into structured JSON format using Ollama's LLM capabilities.

## Features

- Supports both PDF and DOC/DOCX file formats
- Extracts text content and maintains formatting
- Preserves table structures from DOC/DOCX files
- Uses Ollama's LLM for intelligent text-to-JSON conversion
- Maintains document hierarchy and structure
- Saves both JSON output and original files in the output directory

## Prerequisites

- Python 3.x
- Ollama installed and running locally (Download from [Ollama's website](https://ollama.ai/))
- The Llama model pulled in Ollama (`ollama pull llama2`)

## Installation

Install the required dependencies:
```bash
pip install -r requirements.txt
```

## Project Structure

```
.
├── input/              # Place your PDF/DOC files here
├── output/            # Generated JSON files and copied originals
├── code/              # Source code
│   └── convert_doc_pdf_to_json.py
└── requirements.txt   # Python dependencies
```

## Usage

1. Place your PDF or DOC/DOCX files in the `input/` directory

2. Run the converter:
```bash
python code/convert_doc_pdf_to_json.py
```

3. Check the `output/` directory for:
   - Generated JSON files (`filename.json`)
   - Copies of original files

## Output Format

The generated JSON will have the following structure:

```json
{
  "paragraphs": [
    {
      "content": "Paragraph text",
      "hierarchyLevel": 1  // Optional, for section headings
    }
  ],
  "tables": [
    {
      "title": "Table 1",
      "data": [
        ["Header 1", "Header 2", "Header 3"],
        ["Row 1 Col 1", "Row 1 Col 2", "Row 1 Col 3"]
      ]
    }
  ]
}
```

## Error Handling

- The application will skip files that aren't PDF or DOC/DOCX
- If text extraction fails, appropriate error messages will be displayed
- If JSON conversion fails, the raw LLM output will be saved
- Missing input directory will be reported with a clear message

## Dependencies

- `python-docx`: For DOC/DOCX file processing
- `PyPDF2`: For PDF file processing
- `ollama`: For LLM-based text-to-JSON conversion

## Limitations

- PDF tables may not be perfectly preserved due to PDF format limitations
- Very large files might need to be processed in chunks
- The quality of JSON structuring depends on the Ollama model's capabilities
- Currently supports only PDF and DOC/DOCX formats

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## License

MIT License 