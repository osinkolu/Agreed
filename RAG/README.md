# API Documentation for Document Management and Conflict Detection System

## Overview

This API allows users to upload and manage legal documents, perform conflict detection with existing documents in a database, retrieve context for specific queries, and delete stored data. It uses Snowflake for storage and processing, including conflict detection and summarization using Snowflake Cortex.

---

## Base URL

```

https://docusignhack-hsfqh8fycpewdfgb.eastus-01.azurewebsites.net/
```

---

## Endpoints

### 1. **Welcome Endpoint**

**Description**: A simple endpoint to check if the API is running.

- **URL**: `/`
- **Method**: `GET`
- **Response**:

  ```json
  "Welcome, please smile more"
  ```

---

### 2. **Save Document**

**Description**: Uploads a document (PDF or DOCX), extracts its text, splits it into chunks, and stores the chunks in Snowflake.

- **URL**: `/api/save-document`
- **Method**: `POST`
- **Request**:

  - **Form Data**:

    - `file`: The document file (PDF or DOCX).
    - `tag_name`: A tag to categorize the document.
    - `username`: The unique identifier for the documents to search for
  - **Example**:

    ```bash
    curl -X POST http://<server>/api/save-document \
      -F "file=@contract.docx" \
      -F "tag_name=legal"
    ```
- **Response**:

  ```json
  {
    "message": "Document saved successfully.",
    "summary": "Summary of the uploaded document."
  }
  ```
- **Errors**:

  - `400`: Missing file or unsupported file type.
  - `500`: Server-side error.

---

### 3. **Context Retrieval**

**Description**: Retrieves context (similar document chunks) from the database for a given query.

- **URL**: `/api/context-retrieval`
- **Method**: `POST`
- **Request**:

  - **JSON Body**:

    ```json
    {
      "query": "specific query text",
      "n": 5
      "usernme": olufemuyiwa@kausar.com
    }
    ```

    - `query` (required): The search text.
    - `n` (optional, default: 5): Number of similar chunks to retrieve.
    - `username` (required):  A unique identifier
- **Response**:

  ```json
  {
    "results": [
      {
        "chunk": "Text of a similar document chunk.",
        "tag_name": "legal",
        "filename": "contract1.docx",
        "page_number": 2,
        "paragraph_number": 3
      }
    ]
  }
  ```
- **Errors**:

  - `400`: Missing query in the request.
  - `500`: Server-side error.

---

### 4. **Conflict Checker**

**Description**: Checks for conflicts between a new document and existing documents in the database.

- **URL**: `/api/conflict-checker`
- **Method**: `POST`
- **Request**:

  - **Form Data**:

    - `file`: The document file (PDF or DOCX).
  - **Example**:

    ```bash
    curl -X POST http://<server>/api/conflict-checker \
      -F "file=@new_contract.pdf"
    ```
- **Response**:

  ```json
  {
    "conflict_summary": "Summary of conflicts detected in the document.",
    "complete_conflict": "Detailed text of all conflicts detected."
  }
  ```
- **Errors**:

  - `400`: Missing file or unsupported file type.
  - `500`: Server-side error.

---

### 5. **Delete Document**

**Description**: Deletes document chunks from Snowflake based on the `filename` or `tag_name`.

- **URL**: `/api/delete-document`
- **Method**: `POST`
- **Request**:

  - **JSON Body**:

    ```json
    {
      "filename": "contract1.docx",
      "tag_name": "legal",
      "usernme": olufemuyiwa@kausar.com 
    }
    ```

    - At least one of `filename` or `tag_name` is required. `username` is also required.
- **Response**:

  ```json
  {
    "message": "Document(s) deleted successfully."
  }
  ```
- **Errors**:

  - `400`: Neither `filename` nor `tag_name` is provided.
  - `500`: Server-side error.

---

## File Upload Notes

- **Supported File Types**: PDF, DOCX
- **File Size**: Limited by server settings and `/tmp` directory capacity.

---

## Configuration Details

### Snowflake Configuration

Ensure the following environment variables or configurations are set:

- `SNOWFLAKE_CONFIG["user"]`: Snowflake username.
- `SNOWFLAKE_CONFIG["password"]`: Snowflake password.
- `SNOWFLAKE_CONFIG["account"]`: Snowflake account identifier.
- `SNOWFLAKE_CONFIG["warehouse"]`: Snowflake warehouse.
- `SNOWFLAKE_CONFIG["database"]`: Snowflake database.
- `SNOWFLAKE_CONFIG["schema"]`: Snowflake schema.

### Chunking Configuration

- **CHUNK_SIZE**: `5000` characters.
- **CHUNK_OVERLAP**: `256` characters overlap between chunks.

---

## Error Handling

- **400 Bad Request**: Indicates missing or invalid request parameters.
- **500 Internal Server Error**: Indicates a server-side issue during processing.

---

## Dependencies

- **Flask**: Web framework.
- **PyPDF2**: For extracting text from PDF files.
- **python-docx**: For extracting text from DOCX files.
- **Snowflake**: Snowflake Python connector for database interaction.
- **langchain**: For text chunking and processing.

---

## Future Improvements

- **Concurrency**: Parallelize chunk processing for large files.
- **Extended File Support**: Add support for other document formats (e.g., TXT, XLSX).
- **Authentication**: Secure API endpoints using API keys or OAuth.

---

## Contact

For questions or issues, please contact us.
