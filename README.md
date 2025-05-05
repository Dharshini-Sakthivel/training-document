# MongoDB User Data Management MCP Server

A FastMCP server implementation for managing user data with MongoDB, providing tools for data insertion and retrieval operations.

## Features

- MongoDB integration with automatic connection verification
- User data management with fields: name, email, and product
- Data validation and error handling
- Test data initialization
- RESTful API endpoints for data operations

## Prerequisites

- Python >= 3.12
- MongoDB server running on localhost:27017
- Required Python packages (specified in pyproject.toml):
  - mcp[cli] >= 1.7.0
  - pymongo == 4.6.0

## Installation

1. Ensure MongoDB is installed and running on your system
2. Clone the repository
3. Install dependencies using your preferred Python package manager

```bash
# Using pip
pip install -r requirements.txt
```

## Available Tools

### 1. Document Insertion
```python
insert_document(collection: str, document: dict) -> dict
```
- Inserts a new document into specified collection
- Required fields: name, email, product
- Returns success status and document ID

### 2. Document Search
```python
find_documents(collection: str, query: dict = {}) -> dict
```
- Searches for documents matching the query
- Returns filtered fields: name, email, product
- Includes document count

### 3. Specific User Search
```python
find_dharshini_data(collection: str) -> dict
```
- Retrieves documents for user "Dharshini"
- Returns filtered fields: name, email, product
- Includes document count

### 4. Collection Schema
```python
get_collection_schema(collection: str) -> dict
```
- Resource endpoint: `mongodb-collection://{collection}`
- Returns sample document structure

## Usage Examples

### Starting the Server
```python
python server.py
```

### Inserting a Document
```python
document = {
    "name": "John Doe",
    "email": "john@example.com",
    "product": "Basic Subscription"
}
result = insert_document("users", document)
```

### Searching Documents
```python
# Find all documents
result = find_documents("users")

# Find specific user
result = find_documents("users", {"name": "John Doe"})
```

## Error Handling

The server implements comprehensive error handling:
- MongoDB connection verification
- Required field validation
- Document existence checks
- Proper error messages and status codes

## Test Data

The server automatically initializes with test data for demonstration:
- User: Dharshini
- Email: dharshini@example.com
- Product: Premium Subscription

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
