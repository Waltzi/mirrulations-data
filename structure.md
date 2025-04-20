## Overview

The data from [regulations.gov](https://www.regulations.gov/) is split into two broad categories:

- **Raw Data**: The original data obtained from the source, organized by agency and docket ID, separating binary and textual content.
- **Derived Data**: Processed outputs derived from the raw data using future tools like AI models, entity extractors, and summarization pipelines.

Each element (docket, document, comment) is uniquely identified, and attachments (usually `.pdf`, `.doc`, or `.docx`) are stored alongside extracted or structured text versions.

---

## Raw Data Structure

The `raw-data` directory contains the original source data, separated by agency and docket ID.

```
raw-data
└── <agency>
    └── <docket id>
        ├── binary-<docket id>
        │   ├── comments_attachments
        │   │   ├── <comment id>_attachment_<counter>.<extension>
        │   │   └── ...
        │   └── documents_attachments
        │       ├── <document id>_attachment_<counter>.<extension>
        │       └── ...
        └── text-<docket id>
            ├── comments
            │   ├── <comment id>.json
            ├── docket
            │   ├── <docket id>.json
            ├── documents
            │   ├── <document id>.json
            │   ├── <document id>_content.htm
```

---

## Derived Data Structure

The `derived-data` directory contains outputs of processing pipelines, such as AI-generated summaries, named entity recognition, and extracted text.

```
derived-data
└── <agency>
    └── <docket id>
        ├── mirrulations
        │   ├── ai_summary
        │   │   ├── comment
        │   │   ├── comment_attachments
        │   │   └── document
        │   ├── entities
        │   │   ├── comment
        │   │   ├── comment_attachment
        │   │   └── document
        │   └── extracted_txt
        │       └── comment_attachment
        │           └── <comment id>_attachment_<counter>_extracted.txt
        ├── MoravianResearch
        │   └── <projectName>
        │       ├── comment
        │       ├── docket
        │       └── document
        └── trotterf
            └── <projectName>
                └── <fileType>
                    └── <fileID>.txt
```

---

## Summary

- **Top-Level Separation**: `raw-data` for original unprocessed content, `derived-data` for all post-processing artifacts.
- **Agency and Docket Organization**: Both structures mirror agency/docketId hierarchy for consistency.
- **Binary/Text Separation**: In `raw-data`, attachments and text content are split for cleaner access and processing.
- **Structured Outputs**: In `derived-data`, various project folders house data outputs for derived information like summaries and text extraction(comment attachments).
