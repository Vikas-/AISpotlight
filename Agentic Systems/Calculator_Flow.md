# Calculator API Flow Documentation

## Request Flow
[First Mermaid diagram here]

## Technical Flow
[Second Mermaid diagram here]

## System Architecture
[Third Mermaid diagram here]

## API Endpoints

### POST /api/calculator/evaluate
- **Purpose**: Evaluates mathematical expressions using Claude AI
- **Authentication**: Required (Bearer token)
- **Request Body**:
  ```json
  {
    "expression": "string"
  }
  ```
- **Response**:
  ```json
  {
    "result": "string",
    "expression": "string",
    "user_id": "number"
  }
  ```

### GET /api/calculator/history
- **Purpose**: Retrieves calculation history
- **Authentication**: Required (Bearer token)
- **Response**:
  ```json
  {
    "history": [
      {
        "expression": "string",
        "result": "string",
        "timestamp": "string"
      }
    ]
  }
  ```

## Error Handling
- 401: Unauthorized
- 400: Invalid expression
- 500: Server error

## Flow Description

1. **User Input**
   - User enters expression or question in frontend
   - Frontend validates input

2. **API Request**
   - Frontend sends authenticated request to backend
   - Backend validates token

3. **Claude Processing**
   - Backend sends request to Claude
   - Claude either:
     - Responds directly
     - Requests calculator tool use

4. **Tool Processing**
   - If tool use requested:
     - Backend processes calculation
     - Sends result back to Claude
     - Gets final response

5. **Response**
   - Backend formats response
   - Frontend displays result to user